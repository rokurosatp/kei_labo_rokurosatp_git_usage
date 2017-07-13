# gensimでword2vecを使う方法 #

##  gensimのインストール ##

python環境があればすぐに入るはずです

---
Linux:

    sudo -H pip3 install gensim

---
Windows (Miniconda):

依存パッケージの`numpy`と`scipy`についてはcondaからインストールする必要があります。

    conda update conda
    conda install numpy
    conda install scipy
    pip install gensim

---
## ベクトルの構築 ##
---

数行でベクトルの構築が書けます

* [API リファレンス: models.word2vec – Deep learning with word2vec](https://radimrehurek.com/gensim/models/word2vec.html)

### 構築のコード ###

    from gensim.model.word2vec import Word2Vec
    
    sentences = ['first sentence', 'second sentence']   # ドキュメントに書かれていないが文文字列のリストをいれると思われる
    model = Word2Vec(sentences, size=100, window=5, min_count=5, worker=4)
    model.save('filename')              # 学習したvectorをファイルに保存

### モデル利用のコード ###

    from gensim.model.word2vec import Word2Vec

    model = Word2Vec.load('filename')  # ロード
    vec = model['word']                # ベクトルの抽出
