# Dashboard de Inteligência Agrícola Nacional (Base IBGE 2024)

Este projeto apresenta uma solução de Business Intelligence para análise de faturamento e produtividade do setor agrícola brasileiro. A base de dados utilizada é a Pesquisa Agrícola Municipal (PAM - IBGE).

## Arquitetura do Projeto

O fluxo de dados foi estruturado para garantir a integridade das informações e a portabilidade do modelo entre diferentes ambientes.

### 1. Processamento e Saneamento (Excel/Power Query)
* **Consolidação de Dados:** ETL desenvolvido em Linguagem M para agrupamento dinâmico de 27 arquivos estaduais (UFs).
* **Padronização Geográfica:** Tratamento de strings para separação de hierarquias (Mesorregião, Microrregião e Município) e limpeza de caracteres especiais.
* **Parametrização:** Utilização do parâmetro `p_PAM` para definição do diretório de origem, facilitando a atualização em diferentes máquinas.

### 2. Modelagem e Performance (Power BI)
* **Modelo Dimensional:** Estrutura Star Schema composta por tabelas Fato (`fato_PAM`) e Dimensões (`d_Cultivo`, `d_Geografia`).
* **Regras de Negócio (DAX):** * Cálculo de **Rendimento Médio Ponderado** (Produtividade) por área colhida, seguindo a metodologia oficial do IBGE.
    * Conversão de unidades de medida e tratamento de grandezas financeiras (Mil Reais para Bilhões/Milhões).
    * KPIs condicionais baseados na seleção do cultivo.

---

## Estrutura de Pastas

* **/PAM Brasil 2024**: Arquivo `.pbix` do relatório com dados em cache.
* **/data/raw_data**: Pasta contendo os 27 arquivos originais do IBGE por UF.
* **/data/pam_brasil**: Arquivo `.xlsx` gerado após o primeiro ETL que alimenta o Power BI.
* **/geo**: Arquivo geográfico para os visuais de mapa.

---

## Instruções para Execução

Para atualizar o projeto localmente, é necessário configurar os parâmetros de origem:

**1. No arquivo Excel:**
* Acesse `Dados` > `Consultas e Conexões` > `Editar Parâmetros`.
* Altere o valor do parâmetro `p_PAM` para o caminho da pasta `/data/raw_data` em seu computador.
* Clique em **Atualizar Tudo**.

**2. No Power BI:**
* Vá em `Transformar Dados` > `Editar Parâmetros`.
* Informe o novo caminho para a **pam_brasil** (Excel) e para a tabela de **Geografia**.
* Clique em **Aplicar Alterações**.

---

**Tecnologias:** Power BI, Power Query (Linguagem M), Excel, DAX.

### Contato
**Luiz Henrique Alves** 
[LinkedIn](https://www.linkedin.com/in/luizhenriqueaaugusto/)
