********************************************************************************
Breve análise de dados sobre o mercado de trabalho de cientista de dados nos EUA
********************************************************************************

++++++
Resumo
++++++

Neste projeto é realizado uma breve análise exploratória de dados de um dataset de anúncios de vagas de emprego para cientista de dados nos E.U.A. no mês de Agosto de 2008. Os dados foram coletados no site Indeed por Shanshan Lu e publicados no site Kaggle. O arquivo do dataset está no formato CSV. Foram utilizadas as bibliotecas do Pandas, Numpy, matplotlib, seaborn para a realização deste estudo. Também foi usado o nltk, uma das bibliotecas de processamento de linguagem natural do python, para analisar as posições das vagas e colaboram no machine learning.

+++++++
Sumário
+++++++

`Sobre o dataset e feature engineering`_

`Análise do campo Position`_

`Análise do campo Company`_

`Análise do campo Location`_

`Análise do campo Description`_

`Machine Learning`_

+++++++++++++++++++++++++++++++++++++
Sobre o dataset e feature engineering
+++++++++++++++++++++++++++++++++++++

O dataset é composto por dados de 6964 anúncios que são: Position Name, Location, Job Description Company Name e Number of Reviews of the Company (Em português, nome da posição, localização, descrição da vaga, nome da empresa, número de reviews da empresa, respectivamente). Com exceção do campo Reviews, o qual é numérico, todos os campos, ou colunas do dataset, são variáveis categóricas. O campo Position Name é tanto ordinal quanto nominal. O campo Reviews contém 1638 valores nulos enquanto os demais contêm 11 cada. O campo description tem mais de 6000 valores únicos enquanto o campo location tem em torno de 400. Surpreendemente há um pouco mais de 5 mil nomes de posições, sendo Data Scientist a posição mais frequente, aparecendo 351 vezes.

Foram removidos todos os valores nulos no dataframe, com exceção daqueles pertencentes ao campo reviews. Algumas localidades de determinadas vagas contêm números no nome. Tais caracteres foram removidos. Pontuações foram removidas nos nomes das posições.

Foi criado uma coluna chamada state (Estado) usando as siglas dos estados contidos nos nomes das localidades das vagas. Ao todo são 10 estados, sendo a Califórnia o estado mais comum, parecendo 2152 vezes.

+++++++++++++++++++++++++
Análise do campo Position
+++++++++++++++++++++++++

Utilizando a biblioteca do nltk, foi observado nos nomes das posições que as palavras scientist e data são as mais comuns, seguida de engineer, research e senior. Verifica-se também que palavras associadas ao nível hierárquico da função (senior, manager, director, lead, sr) estão entre as 30 palavras mais comuns. Além disso, as palavras machine e learning estão entre as 10 mais usadas. Quanto aos pares de palavras mais comuns, estão os pares data scientist, machine learning e scientist data na liderança do ranking. Quanto aos tritetos, o data scientist data lidera a lista.

Analisando as posições nas quais a palavra data scientist aparece, verifica-se que há alta oferta de cargos para profissionais nível sênior ou ligados a um cargo de liderança. Verifica-se que as palavras machine e learning são bastante comuns em posições de cientista de dados. Somado a isso, o par natural language é bastante popular também, palavras associadas ao termo processamento de linguagem natural. Outros pares tais como financial service e deep learning também estão entre os top 30. De modo surpreende, o nome New York é bastante comum nos nomes das posições de cientista de dados. Quanto aos tritetos, verifica-se que natural language processing lidera o ranking. Entre os tritetos mais populares, verifica-se a presença da palavra Azure, nome dado ao cloud computing service da Microsoft. Para finalizar, entre os tritetos e os pares, pode-se observar grupos de palavras como cognitive natural, cognitive natural language, manager cognitive natural e associate cognite natural estão entre os grupos mais comuns. Tais termos também estão ligados ao processamento de linguagem natural.

Uma outra abordagem de análise das posições das vagas foi implementada. As posições foram divididas em 5 categorias com base na presença de determinadas palavras chaves nos nomes das posições. As categorias são: Data Scientist, Machine Learning Engineer, Data Analyst, Data Science Manager, Data Engineer e Others. Verirfica-se que a categoria Data Scientist é a mais comum das 5, superior a soma das categorias Machine Learnining Engineer e Data Analyst. Somado a isso, pode-se observar que a categoria Others é a terceira maior categoria. A ordem do ranking de modo geral varia de estado para estado. A categoria Data Scientist é a mais procurada na Califórnia e em diversos estados, mas em Colorado e Washington Machine Learning Engineer lidera. O segundo colocado no ranking também varia entre os estados nos quais Data Scientist lidera. Seguindo essa comparação entre estes estados, nota-se que o percentual da categoria Data Scientist não é o mesmo entre estes. Essa categoria é bem mais procurada em New Jersey do que os outros estados, mais de 75% das vagas, enquanto em Illinois é apenas de 30%. Para finalizar, de modo geral, a proporcionalidade das demais categorias em relação à categoria Data Scientist é diferente. Com relação à este aspecto, verifica-se que os estados do Texas e Georgia seguem mais ou menos o mesmo padrão, divergindo significativamente apenas nas categorias Data Analyst e Data Engineer.

Para aprofundar e reforçar a análise comparativa das categorias entre os estados foi feito um conjunto de gráficos de barra. Os gráficos de barra mostram a quantidade de vagas das categorias em cada estado. Cada gráfico para uma categoria e cada barra para um estado. Pode-se observar que, de modo geral e estatisticamente, os estados dão prioridades diferentes em relação as categorias.

Foi feita uma Word Cloud para cada categoria. A Word Cloud apresenta as palavras mais usadas em um conjunto de textos. O tamanho das palavras está de acordo com a frequência que elas aparecem nos textos. Verifica-se que a word cloud de data scientist apresenta as palavras research e science como sendo as mais usadas, seguidas de learning, analysis, business e development. Na word cloud de others, as maiores palavras são research, ability e project. A palavra business é bastante comum nas categorias data analyst, data engineer e data science manager. Para a categoria machine learning engineer, software e learning são as palavras mais usadas.

++++++++++++++++++++++++
Análise do campo Company
++++++++++++++++++++++++

Analisando o campo Company do dataframe, verifica-se a maioria das vagas são da Amazon, Ball Aerospace, Microsoft, Google e de duas empresas da área de saúde. Usando as word clouds nas descrições das vagas ligadas às top 5 empresas com maior número delas, verifica-se a Amazon e Microsoft focam mais nas palavras custumer, business e learning. Nos anúncios da Ball Aerospace nota-se que os termos required, systems e aerospace são os mais comuns. A Google, diferenciando da Microsoft, utiliza mais palavras como product, qualification, resume, technical nas descrições das vagas de emprego.

Comparando as categorias de posições entre as principais empresas e as demais, verifica-se que a Google, Microsoft, Amazon e Ball Aerospace contêm mais vagas relacionadas a categoria Machine Learning Engineer. As vagas da NYU Langone Health são mais comuns na categoria Others e Data Analyst. Para as demais empresas, a categoria Data Scientist contém mais posições. Fazendo uma comparação das vagas da top 5 empresas e das demais em relação aos estados, nota-se que a Amazon e a Microsoft estão concentrando suas vagas no estado de Washignton, Ball Aerospace em Colorado e NYU Langone Health em New York. As vagas da Google e outras empresas estão mais concentradas na Califórnia.

Quanto aos reviews das top 5 empresas e as demais, verifica-se que entre as top 5, a Amazon tem a maior média de reviews por vaga. Diferente das top 5, as reviews das outras empresas têm alto desvio padrão, grande diferença entre o máximo e o mínimo e a mediana distante da média. Portanto, o perfil do conjunto de reviews destas empresas é bastante diverso.

+++++++++++++++++++++++++
Análise do campo Location
+++++++++++++++++++++++++

Quanto ao campo das localidades das vagas, verifica-se que a cidade de New York é a que tem maior número de vagas. No entanto, o estado de New York é o quarto no ranking dos 10 estados, liderado pelo estado da Califórnia. A vaga mais comum na cidade de New York e do estado da Califórnia é de data scientist. 

++++++++++++++++++++++++++++
Análise do campo Description
++++++++++++++++++++++++++++

No mapeamento das palavras relacionadas a grau acadêmico, verifica-se que há 3209 vagas que têm termos relacionados ao bacharelado, 3138 relacionados ao mestrado e 1900 ao doutorado. Analisando a presença de nomes de determinadas tecnologias tais como Python, R, Perl, SQL, entre outros nas descrições das vagas, verifica-se que mais de 80% delas exige a linguagem  R, seguida por, um pouco menos de 40%, Python e SQL, em torno de 25%. Quanto as bibliotecas do Python, selecionamos 6 delas para verificar a presença delas nas descrições : spacy, nltk, sklearn, pandas, numpy e tensorflow. Verifica-se que tensorflow é a biblioteca mais comum das 6, seguida de pandas e numpy. Também foi analisado os anos de experiência exigida pelas vagas e pode-se constatar que a maioria delas pede 5 anos de experiência ou menos.

.. _`machine Learning`:
++++++++++++++++
Machine Learning
++++++++++++++++

Um modelo de machine learning foi treinado para prever qual empresa pertence determinado anúncio de vaga de emprego. Para isso, as posições foram separadas nas 5 empresas com maior número de vagas e as demais reunidas em um único grupo chamado other. O modelo de ML escolhido foi o classificador linear stochastic gradient descent (SGD) do scikit learn e no seu treinamento foi usado Validação Cruzada.

Para preparar os dados para ser usados no treinamento do modelo foram realizadas algumas feature engineering. As palavras dos textos dos anúncios foram simplificadas na sua forma fundamental através do algoritmo de stemming. E em seguida, foi obtido os valores numéricos do paramêtro TF-IDF delas. TF-IDF, term frequency-inverse document frequency (frequência do termo - frequência do documento inversa), é um parâmetro estatístico que estima o grau de relevância de uma palavra em um documento dentro de um conjunto de documentos. Quanto ao rótulo, que é o nome das empresas, foram codificados por valores entre 0 a 5. Foi separado 30% dos dados para servirem como teste e nesta separação foi aplicada uma estratificação com base na distribuição das vagas entre as empresas escolhidas.

Para estimar a qualidade do modelo, foram medidos a precisão e a matriz de confusão dele. A precisão do modelo SGD após o treinamento é de 0.977 e a matriz de confusão dele apresenta, de modo geral, bom resultado.
