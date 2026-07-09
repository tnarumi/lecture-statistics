# 統計学特講（経済学部） Colab教材ページ

このページは、授業で使うGoogle Colabノートブックへの入口です。  
各回の授業開始時に、Moodleからこのページを開き、該当回のリンクをクリックしてください。

## 授業ノートブック一覧

1. Pythonの導入 

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/01_introduction.ipynb

2. Pythonによるデータ分析 

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/02_basicStat.ipynb

3. 国内総生産（GDP） 

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/03_gdp.ipynb

4. 物価指数 

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/04_price_index.ipynb

5. 労働統計

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/05_labor_statistics.ipynb

6. 人口統計

  準備中


## 自由分析課題のテンプレート

  https://colab.research.google.com/github/tnarumi/lecture-statistics/blob/main/notebooks/2026_stat2.ipynb


## 最初に必ず行うこと（毎回）

1. 上のリンクを開いてGoogle Colabを表示する
2. Colabで「ドライブにコピー」をクリックする
3. コピーしたノートブックで作業する

注意：配布された元ファイルを直接編集せず、必ず自分のGoogle Drive上のコピーで作業してください。

## 授業中の基本操作

1. 上から順にセルを実行する（`Shift + Enter`）
2. エラーが出たら、まずそのセルをもう一度実行する
3. 課題提出がある場合は、Moodleの指示に従って提出する

## よくある質問

`Q. ノートブックが編集できません`  
`A. 「ドライブにコピー」をしていない可能性があります。先にコピーを作成してください。`

`Q. 前回の続きから作業したいです`  
`A. Google Driveに保存されている自分のノートブックを開いてください。`

`Q. CSVの読み込みで文字化けやエラーが出ます`  
`A. 日本語を含むCSVでは、文字コードの違いでエラーが出ることがあります。次のようにread_csvでencodingを指定して試してください。`

```python
df = pd.read_csv(csv_file, encoding="cp932")
df = pd.read_csv(csv_file, encoding="utf-8-sig")
```

`Q. 実行するとNameErrorが出ます`  
`A. その変数を作るセルがまだ実行されていない可能性があります。ノートブックを上から順に実行し直してください。途中だけ実行すると、dfやmodelなどがまだ作られていないことがあります。`

`Q. KeyErrorが出ます`  
`A. 指定した列名がデータの列名と一致していない可能性があります。まずdf.columnsを実行して列名を確認し、スペル、大文字小文字、アンダースコアを合わせてください。`

`Q. GitHub上のCSVデータを読み込めません`  
`A. 配布データはGitHub上のCSVファイルを読み込んでいます。インターネット接続や一時的なGitHub、Colabの不調で失敗することがあるため、少し時間を置いてセルを再実行してください。`

`Q. 欠損値を削除したらデータ数が減りました`  
`A. dropna()は欠損値を含む行を削除します。df.isna().sum()やdf.shapeで、どの列に欠損があり、何行残っているかを確認してください。`

`Q. GDP成長率やインフレ率の最初の行がNaNになります`  
`A. shift()やpct_change()は前の年、前の月、前年同月などと比べる計算なので、比較相手がない最初の行はNaNになります。計算ミスではありません。`

`Q. 日付を使ったグラフでエラーが出ます`  
`A. date列が文字列のままだと扱いにくいことがあります。物価指数や労働統計のノートブックと同じように、pd.to_datetime(df["date"])で日付型に変換してください。`

`Q. グラフが表示されない、または横軸や縦軸がおかしいです`  
`A. df.plot(x="date", y="value")のxとyには、実際に存在する列名を入れる必要があります。`

`Q. GDPや労働統計の値が公表値と少し一致しません`  
`A. ノートブックでは、単位や集計方法を授業用にそろえたデータを使っています。GDPは名目値、労働統計は万人単位です。実際の公表統計とは季節調整の有無や丸めのため少しずれることがあります。`

`Q. 列名にUnnamedが出ます`  
`A. CSVの冒頭に説明行やメタデータ行が入っている可能性があります。データ読込セルのskip_num_rowsを変更して、実際の列名がある行まで読み飛ばしてください。`

`Q. 自由分析課題でCSVを選び直したいです`  
`A. 一度アップロードしたCSVがColab上に残っている場合、同じファイルを自動で読み込みます。別のCSVを使うときはcsv_file = ""としてからデータ読込セルを再実行してください。`
