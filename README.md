# BBC Text Classification
This is the source code of the Data Mining Assignment at HCMUT.

## Introduction 

We used the [BBC Full Text Document Classification](https://www.kaggle.com/datasets/alfathterry/bbc-full-text-document-classification) dataset. This dataset contains a collections of news articles organized into multiple categories, including entertainment, sport,... Each entry consists of its *text* and its *label*.

We aim to evaluate and compare the performance of **CountVectorizer**, **TfidfVectorizer**, **Word2Vec** with *ANN* and *KNN* for the classification task. After that, we briefly explain the reasons of differences.

## Remark
### Performance

- ANN models perform best with CountVectorizer, CountVectorizer slightly outperforming TfidfVectorizer.
- For KNN, TfidfVectorizer is superior.
- Word2Vec's performance is significantly lower in both ANN and KNN.

#### CountVectorizer
| Label         | ANN Precision | ANN Recall | ANN F1-Score | KNN Precision | KNN Recall | KNN F1-Score |
|---------------|---------------|------------|--------------|---------------|------------|--------------|
| entertainment | 1.0000        | 0.9697     | 0.9846       | 0.6202        | 0.7692     | 0.6867       |
| business      | 0.9718        | 1.0000     | 0.9857       | 0.9677        | 0.4000     | 0.5660       |
| sport         | 0.9881        | 0.9881     | 0.9881       | 0.8784        | 0.7927     | 0.8333       |
| politics      | 0.9808        | 1.0000     | 0.9903       | 0.5714        | 1.0000     | 0.7273       |
| tech          | 1.0000        | 0.9872     | 0.9935       | 1.0000        | 0.3239     | 0.4894       |

#### TfidfVectorizer
| Label         | ANN Precision | ANN Recall | ANN F1-Score | KNN Precision | KNN Recall | KNN F1-Score |
|---------------|---------------|------------|--------------|---------------|------------|--------------|
| entertainment | 0.9898        | 0.9798     | 0.9848       | 0.8929        | 0.9615     | 0.9259       |
| business      | 0.9853        | 0.9710     | 0.9781       | 1.0000        | 0.9067     | 0.9510       |
| sport         | 0.9762        | 0.9762     | 0.9762       | 0.9634        | 0.9634     | 0.9634       |
| politics      | 1.0000        | 1.0000     | 1.0000       | 1.0000        | 0.9900     | 0.9950       |
| tech          | 0.9625        | 0.9872     | 0.9747       | 0.9577        | 0.9577     | 0.9577       |

#### Word2Vec
| Label         | ANN Precision | ANN Recall | ANN F1-Score | KNN Precision | KNN Recall | KNN F1-Score |
|---------------|---------------|------------|--------------|---------------|------------|--------------|
| entertainment | 0.5490        | 0.8485     | 0.6667       | 0.6014        | 0.8558     | 0.7063       |
| business      | 0.4762        | 0.1449     | 0.2222       | 0.7273        | 0.5333     | 0.6154       |
| sport         | 0.5726        | 0.8452     | 0.6827       | 0.7500        | 0.7317     | 0.7407       |
| politics      | 0.4962        | 0.6471     | 0.5617       | 0.7527        | 0.7000     | 0.7254       |
| tech          | 1.0000        | 0.0128     | 0.0253       | 0.6786        | 0.5352     | 0.5984       |


### Explain
#### Data Sparsity:
- CountVectorizer and TfidfVectorizer produce sparse vectors, which are effective for certain algorithms like ANN that can handle large feature spaces.
- Word2Vec produces dense vectors, which may lose information in aggregation.
#### Task Dependence: 
- CountVectorizer and TfidfVectorizer emphasize lexical differences (important for classification).
- Word2Vec emphasizes semantic similarity.
#### Dataset Size and Quality:
- Word2Vec benefits from a large corpus for training embeddings. 

## Result
Final score: 9.5/10
