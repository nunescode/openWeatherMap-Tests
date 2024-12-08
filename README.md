
# **Projeto: Testes Automatizados com API OpenWeatherMap**

Este projeto demonstra a criação e execução de testes automatizados para a API pública **OpenWeatherMap**, utilizando **Postman**, **Newman** e relatórios detalhados com **htmlextra**. O objetivo é validar diversos cenários, incluindo casos positivos, negativos e fluxos encadeados, garantindo a qualidade dos dados retornados pela API.

---

## **Índice**
- [Objetivo](#objetivo)
- [Funcionalidades do Projeto](#funcionalidades-do-projeto)
- [Requisitos](#requisitos)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Como Executar](#como-executar)
- [Detalhes dos Testes](#detalhes-dos-testes)
- [Relatório](#relatório)
- [Contribuindo](#contribuindo)

---

## **Objetivo**
Este projeto foi desenvolvido para:
- Demonstrar habilidades na criação de testes de APIs utilizando Postman.
- Automatizar a execução de testes com Newman.
- Validar a funcionalidade da API em diversos cenários.
- Gerar relatórios visuais e detalhados para análise.

---

## **Funcionalidades do Projeto**
- **Testes Positivos:**
  - Validação do status da resposta (`200 OK`).
  - Verificação de dados importantes como temperatura, umidade, pressão e vento.
- **Testes Negativos:**
  - Validação de mensagens de erro para cidades inexistentes, chaves inválidas e parâmetros ausentes.
- **Fluxos Encadeados:**
  - Captura e reutilização de IDs de cidades em múltiplas requisições.
- **Relatórios Visuais:**
  - Geração de relatórios detalhados em formato HTML.

---

## **Requisitos**
Certifique-se de que as seguintes ferramentas estão instaladas na sua máquina:
- [Node.js](https://nodejs.org/)
- [Postman](https://www.postman.com/)
- [Newman](https://github.com/postmanlabs/newman)

Para instalar o Newman e o relatório extra:
```bash
npm install -g newman newman-reporter-htmlextra
```

---

## **Estrutura do Projeto**
A estrutura de pastas e arquivos do projeto é a seguinte:
```
.
├── collections/
│   ├── clima.postman_collection.json           # Collection do Postman com os testes
│   ├── openWeatherMap.postman_environment.json # Arquivo de ambiente do Postman
│   ├── estadosbr1.json                         # Arquivo com lista de cidades/estados
├── reports/
│   ├── report.html                             # Relatório gerado pelo Newman
├── README.md                                   # Documentação do projeto
```

---

## **Como Executar**

### **Passo 1: Clonar o Repositório**
```bash
git clone https://github.com/seu-usuario/openweathermap-tests.git
cd openweathermap-tests
```

### **Passo 2: Executar os Testes com o Newman**
1. Certifique-se de que as dependências necessárias estão instaladas.
2. Execute o seguinte comando para rodar os testes:
   ```bash
   newman run collections/clima.postman_collection.json \
       -e collections/openWeatherMap.postman_environment.json \
       -r htmlextra \
       --reporter-htmlextra-export reports/openWeatherMap_report.html
   ```

### **Executar no Postman com estadosbr1.json (opcional)**

1. **Importar os Arquivos para o Postman**
   - Abra o Postman.
   - Clique em **Import** e selecione os seguintes arquivos:
     - `collections/clima.postman_collection.json`
     - `collections/openWeatherMap.postman_environment.json`
     - `collections/estadosbr1.json` (como arquivo de dados para o Runner).

2. **Configurar o Ambiente**
   - Certifique-se de que o ambiente `openWeatherMap` está selecionado no Postman.

3. **Abrir o Collection Runner**
   - No Postman, clique em **Runner** no canto superior direito.
   - Selecione a collection **clima**.

4. **Adicionar o Arquivo de Dados**
   - No Runner, clique em **Data File** e selecione o arquivo `estadosbr1.json`.

5. **Executar os Testes**
   - Ajuste o número de iterações, se necessário.
   - Clique em **Run** para executar os testes.
   - Verifique os resultados diretamente no Postman.


### **Passo 3: Visualizar o Relatório**
- Abra o relatório gerado:
   ```bash
   start reports/openWeatherMap_report.html
   ```

---

## **Detalhes dos Testes**

### **Cenários Positivos**
- **Buscar Clima Atual:**
  - Validação de temperatura, pressão, vento, umidade e descrição do clima.
  - Verificação de que o ID da cidade é armazenado corretamente.
- **Fluxos Encadeados:**
  - Utilização do ID de cidade para buscar previsões futuras.

### **Cenários Negativos**
- **Erro por Cidade Inexistente:**
  - Validação de mensagem: `"city not found"`.
- **Erro por API Key Inválida:**
  - Validação de mensagem: `"Invalid API key"`.
- **Erro por Parâmetro Faltando:**
  - Validação de mensagem: `"Nothing to geocode"`.

---

## **Relatório**
O relatório gerado com o **htmlextra** fornece:
- Resultados detalhados de cada requisição.
- Visualização de falhas, incluindo mensagens de erro.
- Tempos de resposta e dados capturados.

---

## **Contribuindo**
1. Faça um fork do projeto.
2. Crie sua branch para a feature:
   ```bash
   git checkout -b minha-feature
   ```
3. Faça commit das alterações:
   ```bash
   git commit -m "Descrição da feature"
   ```
4. Envie suas alterações:
   ```bash
   git push origin minha-feature
   ```
5. Abra um Pull Request.

---
