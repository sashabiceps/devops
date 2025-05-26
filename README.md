👥 Equipe FIAP - 2TDS
Nome	RM
Pablo Lopes Doria de Andrade	556834
Vinicius Leopoldino de Oliveira	557047
Diego Santos Cardoso	558711
📌 Visão Geral
Projeto desenvolvido para a disciplina DevOps Tools & Cloud Computing, implementando uma API REST para gestão de motos em pátios utilizando:

Spring Boot (Java)

Docker (Containerização)

Azure Cloud (VM Linux)

⚠️ Status Atual
diff
- Atenção: A conteinerização completa não está visível devido a uma falha no servidor de banco de dados
🛠️ Tecnologias
Backend: Java 17, Spring Boot 3.x

Banco de Dados: H2 (embutido durante desenvolvimento)

Infraestrutura: Docker, Azure CLI

Documentação: Swagger UI

📋 Endpoints Principais
Método	Endpoint	Descrição
GET	/motos	Lista todas as motos
POST	/motos	Cadastra nova moto
GET	/motos/{id}	Busca moto por ID
🚀 Execução Local
Pré-requisitos
Java 17

Maven 3.8+

Docker (opcional)

bash
# 1. Clone o repositório
git clone https://github.com/Pablo0703/Challenge_Java.git

# 2. Acesse o diretório
cd Challenge_Java/ChallengeMottu

# 3. Execute com Maven
./mvnw spring-boot:run

# Acesse a API:
curl http://localhost:8080/motos
☁️ Implantação na Azure
bash
# Crie a VM (execute localmente)
az vm create \
  --resource-group rg-challenge \
  --name vm-challenge \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys

# Abra a porta 8080
az vm open-port --port 8080 --resource-group rg-challenge --name vm-challenge
🐳 Containerização (Parcial)
dockerfile
FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
COPY src ./src
RUN ./mvnw clean package -DskipTests
EXPOSE 8080
ENTRYPOINT ["java","-jar","target/ChallengeMottu-0.0.1-SNAPSHOT.jar"]
🔍 Diagnóstico do Problema
A falha na conteinerização completa ocorre devido a:

bash
# Log do erro (exemplo):
Caused by: java.net.UnknownHostException: banco-servidor
📊 Diagrama de Arquitetura
[Usuário] → [VM Azure] → [Container Docker] → [Spring Boot]
                           (Falha) ↘
                          [Banco de Dados Offline]
📬 Contato
Para mais informações sobre o projeto, entre em contato com qualquer membro da equipe listado acima.
