# 💰 Bot de Finanzas Personales con n8n, Docker, Telegram y Google Sheets

![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-orange?style=for-the-badge&logo=n8n)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue?style=for-the-badge&logo=docker)
![Telegram](https://img.shields.io/badge/Telegram-Bot_API-blue?style=for-the-badge&logo=telegram)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-Database-green?style=for-the-badge&logo=google-sheets)

Este proyecto es un sistema de automatización **Full Stack** que permite registrar gastos personales en tiempo real mediante un chat de Telegram. El sistema procesa el lenguaje natural, estructura los datos y los almacena automáticamente en una hoja de cálculo de Google Sheets.

## 🚀 Arquitectura del Proyecto

El sistema funciona mediante una arquitectura de microservicios contenerizada con Docker:

1.  **Input:** El usuario envía un mensaje (ej: `Cena 45`) al Bot de Telegram.
2.  **Webhook:** Telegram envía el payload a nuestra instancia local de n8n (expuesta vía túnel seguro).
3.  **Processing:** n8n ejecuta un script en JavaScript para separar el concepto (`Cena`) del monto (`45`).
4.  **Storage:** Se conecta vía API (Service Account) a Google Sheets y añade una nueva fila.
5.  **Feedback:** El bot responde al usuario confirmando la transacción.

## 🛠️ Tecnologías Utilizadas

* **n8n:** Orquestador de flujos de trabajo (Self-hosted).
* **Docker & Docker Compose:** Para la contenerización y despliegue del servicio.
* **JavaScript (ES6):** Para la lógica de manipulación de datos dentro de n8n.
* **Google Cloud Platform (GCP):** Gestión de credenciales IAM (Service Account) para la API de Sheets.
* **ngrok:** Túnel inverso para exponer el localhost a webhooks públicos durante el desarrollo.

## 📋 Pre-requisitos

* Docker y Docker Compose instalados.
* Cuenta de Telegram y un Bot creado con BotFather.
* Proyecto en Google Cloud con la API de Google Sheets habilitada.
* Cuenta de ngrok (para el túnel HTTPS).

## ⚙️ Instalación y Configuración

Sigue estos pasos para desplegar el proyecto en tu máquina local:

### 1. Clonar el repositorio
```bash
git clone [https://github.com/oscartoledoc/BotFinance_n8n.git](https://github.com/oscartoledoc/BotFinance_n8n.git)
cd BotFinance_n8n
