# Verificador de Assinaturas com Redes Siamesas

![Status](https://img.shields.io/badge/status-conclu%C3%ADdo-green)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Framework](https://img.shields.io/badge/Framework-TensorFlow%2FKeras-orange)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/samuelprimo/verificador-assinaturas/blob/main/verificador-assinaturas.ipynb)

## - Sobre o Projeto

Este é um mini-projeto de Visão Computacional desenvolvido como estudo prático para o Mestrado em Informática. O objetivo é construir e treinar um modelo de Deep Learning capaz de verificar a autenticidade de assinaturas manuscritas, determinando se duas imagens de assinatura pertencem à mesma pessoa.

A abordagem utilizada é o **Deep Metric Learning** através de uma arquitetura de **Rede Siamesa**, que é especialmente eficaz para tarefas de verificação e reconhecimento one-shot.

---

## - Tecnologias Utilizadas

O projeto foi inteiramente desenvolvido em um ambiente Google Colab, utilizando as seguintes tecnologias:

* **Linguagem:** Python 3
* **Framework de Deep Learning:** TensorFlow / Keras
* **Bibliotecas:**
    * NumPy (para manipulação numérica)
    * OpenCV (`cv2`) (para pré-processamento de imagens)
    * Matplotlib (para visualização dos resultados)
    * Scikit-learn (para divisão dos dados de treino/validação)

---

## - Como Funciona? A Arquitetura Siamesa

Diferente de um classificador tradicional, a Rede Siamesa não aprende a identificar *de quem* é uma assinatura. Em vez disso, ela aprende a **medir a similaridade** entre duas imagens.

1.  **Rede Base:** Criamos uma Rede Neural Convolucional (CNN) que atua como um "extrator de características". Esta rede recebe uma imagem de assinatura e a transforma em um vetor numérico de 128 dimensões (um "embedding"), que representa a essência daquela assinatura.
2.  **Torres Gêmeas:** O modelo siamês utiliza duas instâncias idênticas (gêmeas) dessa rede base, com os mesmos pesos. Cada "torre" processa uma das duas imagens de entrada.
3.  **Cálculo de Distância:** Após a passagem pelas torres, obtemos dois vetores de embedding. O modelo então calcula a distância entre esses dois vetores.
4.  **Aprendizado:** Durante o treinamento, o modelo é ensinado a:
    * **Minimizar** a distância entre os vetores de assinaturas da mesma pessoa (pares genuínos).
    * **Maximizar** a distância entre os vetores de assinaturas de pessoas diferentes (falsificações).
5.  **Previsão:** Na fase de teste, uma distância pequena entre os vetores significa que as assinaturas são provavelmente genuínas, enquanto uma distância grande indica uma provável falsificação.

---

## - Resultados

O modelo foi treinado com 8.000 pares de imagens e alcançou uma acurácia de validação satisfatória, demonstrando sua capacidade de generalizar e diferenciar assinaturas que nunca viu antes. Dentro do arquibo .ipynb é possível visualizar perfeitamente os resultados.


---

## - Como Executar

É possível executar este projeto diretamente no Google Colab.

1.  **Clique no badge "Open in Colab"** no topo deste README.
2.  **Baixe o Dataset:** O dataset utilizado foi o [Handwritten Signature Forgery Detection](https://www.kaggle.com/datasets/divyanshrai/handwritten-signature-forgery-detection) do Kaggle.
3.  **Prepare os Arquivos:** Para maior eficiência, compacte a pasta do dataset em um único arquivo `.zip`.
4.  **Faça o Upload:** No ambiente Colab, faça o upload do arquivo `.zip` para a pasta `/content`.
5.  **Execute as Células:** Siga as instruções do notebook, executando as células em ordem para descompactar os dados, treinar o modelo e visualizar os resultados.

---

## - Autor

* **Samuel Primo**
    * GitHub: [@samuelprimo](https://github.com/samuelprimo)
    * LinkedIn: (se você tiver, coloque o link aqui)

---

## - Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
