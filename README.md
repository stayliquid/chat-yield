# <a href="https://t.me/chatyieldbot" target="_blank">Try Chat Yield 👉 TG @chatyieldbot</a>

Chat Yield is an AI agent that simplifies discovering and entering liquidity pools on the Solana blockchain, all through a simple conversation on Telegram.

## What is Chat Yield?

DeFi can be complex. Finding the right liquidity pool involves navigating multiple websites, analyzing stats, and understanding transaction details. Chat Yield streamlines this entire process into a natural language conversation.

Simply tell the bot what you're looking for—using text or a voice memo—and it will:
1.  **Understand** your investment preferences (e.g., risk level, token quality).
2.  **Find** a suitable liquidity pool on Raydium.
3.  **Propose** it to you with clear, concise stats.
4.  **Generate** a one-click Solana Action link to execute the transaction securely in your wallet.

This repository contains the two core components of the project: the **Telegram bot** and the **Solana Actions backend**.

## ✨ Features

-   **Conversational AI**: Powered by OpenAI's GPT models to understand user intent for finding liquidity pools.
-   **Voice Memo Support**: Send a voice message, and it will be transcribed by OpenAI's Whisper-1 for processing.
-   **Solana Actions Integration**: Generates secure transaction links that can be opened and signed directly in any compatible Solana wallet (like Phantom or Solflare), providing a seamless and transparent user experience.
-   **Raydium CLMM Support**: The backend is built to interact with Raydium's Concentrated Liquidity Market Maker (CLMM) pools.

## 🏗️ Architecture

Chat Yield is composed of two independent services that work together:

1.  **Telegram Bot (Python/FastAPI)**:
    -   Handles all user interaction within Telegram via a webhook.
    -   Calls the OpenAI API to parse user intent and transcribe audio.
    -   Fetches pool data from the Raydium API.
    -   Constructs a Solana Action URL that points to the backend service.

2.  **Solana Actions Backend (TypeScript/NestJS)**:
    -   Decodes proposal data embedded in the action URL.
    -   Uses the Raydium SDK to build the "join pool" transaction.
    -   Serializes and returns the transaction to the user's wallet for signing.

## 🛠️ Tech Stack

-   **Backend**: TypeScript, NestJS, Raydium SDK v2, `@solana/actions`
-   **Telegram Bot**: Python, FastAPI, `python-telegram-bot`, OpenAI API (GPT & Whisper)
-   **Deployment**: The services are designed for serverless platforms like Vercel (Backend) and a server/container service (Bot).

## 🚀 Getting Started (Local Development)

### Prerequisites

-   [Node.js](https://nodejs.org/) (v18 or newer)
-   [Python](https://www.python.org/) (v3.10 or newer)
-   [ngrok](https://ngrok.com/) to expose your local bot server to the internet.
-   A **Telegram Bot Token** from [@BotFather](https://t.me/BotFather).
-   An **OpenAI API Key**.
-   A **Solana RPC URL** (e.g., from [Helius](https://www.helius.dev/) or [Triton](https://triton.one/)).

Project specific setups can be found in the respective repository's `README` files: [solana-agent](https://github.com/stayliquid/solana_agent) and [solana-telegram-agent](https://github.com/stayliquid/solana_telegram_agent).
