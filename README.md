# aws-serverless-data-discovery

📊 AWS Serverless Data Discovery: De Dados Brutos ao SQL
📝 Descrição do Projeto

Este projeto demonstra a implementação de uma arquitetura de dados moderna e serverless na AWS. O objetivo foi ingerir dados brutos em um Data Lake e torná-los consultáveis via SQL de forma automatizada, utilizando o conceito de Schema-on-Read.

A solução foca em baixo custo operacional (FinOps) e escalabilidade, eliminando a necessidade de gerenciar servidores de banco de dados 24/7.

🏗️ Arquitetura
A estrutura do pipeline segue o fluxo:

<img width="1810" height="592" alt="imagem projeto aws" src="https://github.com/user-attachments/assets/b1a416e5-388c-4513-be5d-6f24542af111" />


Amazon S3: Armazenamento dos dados brutos (CSV).
<img width="1344" height="674" alt="S3" src="https://github.com/user-attachments/assets/d5efb10d-161f-40f2-b0d1-ff74043759f3" />

AWS Glue Crawler: Descoberta automática de esquema e catalogação de metadados.
<img width="1344" height="676" alt="Glue" src="https://github.com/user-attachments/assets/064bd2c9-ab06-430c-8bd2-13d44c14c2f6" />

Amazon Athena: Motor de consulta SQL para análise dos dados armazenados no S3.
<img width="1344" height="723" alt="imagem do projeto" src="https://github.com/user-attachments/assets/145eb950-765c-401b-8d26-f225ef8832cb" />

IAM: Políticas de segurança de privilégio mínimo para comunicação entre serviços.

🛠️ Tecnologias Utilizadas
Cloud: Amazon Web Services (AWS)

Linguagem de Consulta: SQL

Processamento de Dados: AWS Glue

Armazenamento: Amazon S3

Segurança: AWS IAM

🚀 Passo a Passo da Implementação
1. Camada de Armazenamento (S3)
Configurei um bucket S3 estruturado para receber arquivos CSV, simulando uma ingestão de dados transacionais.

2. Automação e Catalogação (Glue)
Implementei um Glue Crawler com uma IAM Role específica para varrer o bucket. O Crawler identificou o esquema dos dados e criou automaticamente a tabela no Glue Data Catalog, reduzindo o esforço manual de modelagem inicial.

3. Análise e Insights (Athena)
Utilizei o Amazon Athena para realizar consultas SQL ad-hoc.
Exemplo de Query de Negócio executada:

SQL
SELECT produto, SUM(valor) as total_receita
FROM db_vendas_lab.vendas
GROUP BY produto
ORDER BY total_receita DESC;
💰 Visão FinOps
Como Analista FinOps, selecionei esta arquitetura por dois motivos principais:

Custo Zero em Repouso: O Athena e o Glue não geram cobrança se não houver consultas/execuções.

Escalabilidade: O custo é baseado apenas no volume de dados escaneados ($5 por TB), tornando-o ideal para análises esporádicas de grandes volumes.

query_insights.sql

👤 Autor
Reginaldo Rocha
Cloud Analyst | FinOps | Especialista em Bancos de Dados em Formação
LinkedIn | GitHub
