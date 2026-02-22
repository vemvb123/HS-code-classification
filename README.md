# HS-code-classification

## Introduction
This study investigates the application of machine learning techniques for Optical Character
Recognition (OCR) and Harmonized System (HS) code classification.

Today, the logistics company Jetcarrier manually assigns HS codes to orders.
This study evaluates the feasibility of automating HS code assignment through machine learning.

Large Language Models (LLM) are investigated for OCR to extract order descriptions from
receipts. Several approaches for HS code classification based on text descriptions are also investigated. 
The investigated methods are 
- Natural Language Processing (NLP)
- Large Language Models (LLMs)
- Semantic Similarity Comparison (SSC)
- Classic Supervised Classification models.
These approaches’ strengths and weaknesses are showcased.

## Extraction of receipt information
LLMs showed good results in extracting textual order descriptions from receipts.
These descriptions were then used with classification models to assign HS codes to the
descriptions.

Graph showcasing LLM accuracy in identifying correct amount of products in a receipt:

<img width="775" height="460" alt="bilde" src="https://github.com/user-attachments/assets/ded2adaa-6cb4-4de5-a285-9829f501ac82" />

Based on these experiments, the model qwen2.5-coder-14b-instruct-q6 k was selected for
having the lowest error as well as among the lowest computational time

To use the models for machine learning, information had to be extracted from them. 

<img width="786" height="707" alt="bilde" src="https://github.com/user-attachments/assets/d9ca0a61-f796-47eb-8af9-59f415e8e575" />

## Text preprocessing
Results of text cleaning:

<img width="519" height="252" alt="bilde" src="https://github.com/user-attachments/assets/d4a75085-d2aa-4c9a-8aa7-0cf7886b4f0d" />

First, the product descriptions were cleaned of noise. This means removing symbols, unneeded
text, punctuation, and stop words. Then, apply spell correction, stemming, and lemmatization.
The SentenceTransformer framework was used with all-MiniLM-L7v2 on the cleaned text descriptions. It maps the product descriptions to a 384-dimensional vector space. This sentence-
transformer was used as it is fast and intended for short sentences, like the product descriptions.
As the number of attributes increases, the need for more examples per output class grows ac-
cordingly. The training time for the models also grow with the number of attributes. To address
this, Principal Component Analysis (PCA) was applied to reduce the vector dimensionality to
100.

## Results

<img width="346" height="177" alt="bilde" src="https://github.com/user-attachments/assets/b50ced45-f720-4d79-b68e-a1cb67ebc605" />

<img width="772" height="435" alt="bilde" src="https://github.com/user-attachments/assets/18d677f9-78b1-40e4-a007-988f42ebef1e" />



Experimental results indicate that NLP-based approaches outperformed other methodologies,
being able to accurately assign up to 8-digit HS codes. Conversely, LLMs, SSC, and traditional
supervised models faced challenges primarily due to data limitations in the dataset.

The study also emphasizes the critical role of high-quality, sufficient data for training effective
classification models. Machine learning is known for needing a lot of data to accurately find
patterns and generalize. A challenge was unsatisfactory data quality, a lack of enough HS code
digit examples, and class imbalance.

NLP worked sufficiently across all digits of the HS code. Supervised machine learning worked
well on the initial digits, but ceased to work on lower digits due to sparse data.
 
LLM and SSC struggled with HS code assignment, but can potentially work with less data than
Classic Supervised Classification, and without pretraining, in addition to not needing labeled
data, which may give less system maintenance.

It was found that machine learning is viable for automatically assigning HS codes, given that
there is sufficient data.







