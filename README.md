# Manutenção Preditiva com Inteligência Artificial

Projeto desenvolvido para a atividade avaliativa do módulo de Análise Preditiva com Python.

## Objetivo

O objetivo deste projeto é desenvolver um modelo de classificação capaz de auxiliar na identificação de possíveis falhas mecânicas em equipamentos industriais a partir de dados coletados por sensores.

A variável alvo utilizada foi `falha_maquina`, onde:

- `0` representa funcionamento normal;
- `1` representa ocorrência de falha mecânica.

## Base de dados

A base utilizada possui 10.000 registros e 14 colunas, contendo informações como:

- temperatura do ar;
- temperatura do processo;
- velocidade de rotação;
- torque;
- desgaste da ferramenta;
- ocorrência de falha da máquina.

As informações fornecidas pelo Departamento de Engenharia também foram consideradas durante a seleção das variáveis utilizadas nos modelos.

## Etapas realizadas

O projeto foi desenvolvido seguindo as seguintes etapas:

1. Análise Exploratória dos Dados (EDA)
2. Limpeza e tratamento dos dados
3. Feature Engineering
4. Divisão e balanceamento dos dados
5. Escalonamento das variáveis
6. Treinamento e ajuste dos modelos
7. Avaliação da acurácia e escolha do modelo final

## Tratamento dos dados

Foram verificadas linhas duplicadas e valores ausentes.

Os valores ausentes identificados nas variáveis numéricas foram preenchidos utilizando a mediana.

Também foram analisados possíveis outliers por meio de boxplots. Os valores extremos identificados foram mantidos, pois não foram encontradas evidências de que representassem erros na base.

## Feature Engineering

Foi criada a variável `potencia`, utilizando a multiplicação entre a velocidade de rotação e o torque.

Essa nova variável foi utilizada como uma característica adicional durante a modelagem.

## Divisão e balanceamento

Os dados foram divididos em:

- 80% para treino;
- 20% para teste.

Foi utilizado `stratify=y` para manter a proporção entre as classes.

Como a variável alvo estava bastante desbalanceada, foi aplicado SMOTE somente nos dados de treino.

## Modelos utilizados

Foram avaliados dois modelos de classificação:

### K-Nearest Neighbors (KNN)

Foram testados:

- K = 3
- K = 5
- K = 7

O melhor resultado no teste foi obtido com K = 3, com acurácia aproximada de 90,7%.

### Árvore de Decisão

Foram testados:

- `max_depth=3`
- `max_depth=5`
- `max_depth=None`

A configuração `max_depth=5` apresentou comportamento mais estável entre treino e teste.

A árvore com `max_depth=None` alcançou a maior acurácia no conjunto de teste, aproximadamente 93,85%, embora tenha apresentado maior sinal de overfitting.

## Resultado final

Comparando os melhores resultados no conjunto de teste:

- KNN: aproximadamente 90,7%
- Árvore de Decisão: aproximadamente 93,85%

A Árvore de Decisão apresentou a maior acurácia e foi o modelo com melhor desempenho neste projeto.

## Tecnologias utilizadas

- Python
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn
- Jupyter Notebook
- Git
- GitHub

## Estrutura do projeto

```text
manutencao-preditiva-ia/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── 01_analise_exploratoria.ipynb
├── outputs/
├── README.md
└── requirements.txt
```

## Como executar

1. Clone ou baixe este repositório.
2. Instale as dependências presentes no arquivo `requirements.txt`.
3. Abra o arquivo `notebooks/01_analise_exploratoria.ipynb`.
4. Execute as células do notebook na ordem em que estão apresentadas.

Para instalar as dependências:

```bash
pip install -r requirements.txt
```

## Possíveis melhorias futuras

Como melhorias futuras, poderiam ser testados outros algoritmos de classificação, novas combinações de variáveis e outras métricas de avaliação além da acurácia.

Também seria possível realizar novos ajustes nos hiperparâmetros para buscar um melhor equilíbrio entre desempenho e overfitting.