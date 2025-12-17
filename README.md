# 🤖✨ Chatbot for Portfolio Website

Welcome to the **Chatbot for Portfolio Website** workflow! This project powers a smart, friendly, and professional AI chatbot embedded directly into a personal portfolio website. It is built with **n8n**, **LangChain**, **OpenRouter**, and **PostgreSQL memory** to deliver a smooth, contextual, and human‑like chat experience.

---

## 🌈 Overview

This workflow enables website visitors to chat with an AI assistant that:

* Knows who **Tomy Vo** is and what he does
* Answers questions about skills, projects, and services
* Remembers conversation context across messages
* Responds fast via a webhook endpoint
* Feels natural, polite, and professional

The chatbot is **not pretending to be Tomy Vo**. Instead, it acts as a trustworthy assistant representing him.

---

## 🚀 Key Features

✨ **AI Agent with Personality & Rules**
🧠 **Persistent Chat Memory (PostgreSQL)**
🌍 **Automatic Language Detection**
🔗 **Webhook‑based Integration (Perfect for Websites)**
⚡ **Powered by LLaMA 3.3 70B via OpenRouter**
🔐 **Session‑based Conversations**
🧼 **Clean JSON API Response**
🌐 **CORS Enabled (Ready for Frontend Use)**

---

## 🧱 Architecture at a Glance

```
Website Chat UI
      ↓
   Webhook (POST)
      ↓
   AI Agent (LangChain)
      ↓
OpenRouter LLM (LLaMA 3.3 70B)
      ↓
Postgres Chat Memory
      ↓
 JSON Response → Frontend
```

---

## 🧩 Workflow Nodes Explained

### 🔔 Webhook

**Node:** `Webhook`
**Method:** POST
**Path:** `/8715b2dc-ff23-4a61-bb7c-2be1c7c0bc91`

This is the entry point of the chatbot. Your website sends messages here in JSON format:

```json
{
  "message": "Hello",
  "sessionId": "unique-session-id"
}
```

---

### 🤖 AI Agent (LangChain)

**Node:** `AI Agent`

This is the brain of the system.

It includes:

* A **strict system prompt** defining behavior
* A detailed **profile of Tomy Vo**
* Clear rules (no hallucinations, no system leaks, no double quotes)
* Language auto‑detection
* Friendly but professional tone

📌 The agent:

* Never claims to be Tomy Vo
* Never invents facts
* Keeps answers short unless asked otherwise

---

### 🧠 OpenRouter Chat Model

**Model:** `meta-llama/llama-3.3-70b-instruct`

Why this model?

* Extremely strong reasoning
* Natural conversation flow
* Excellent instruction following
* Great balance between detail and clarity

This node provides the **language intelligence** used by the AI Agent.

---

### 💾 Postgres Chat Memory

**Node:** `Postgres Chat Memory`

This node enables **persistent conversation memory**.

* Each user is tracked via a `sessionId`
* Past messages are remembered
* Enables contextual follow‑up questions

This dramatically improves the chat experience and makes it feel human.

---

### 📤 Respond to Webhook

**Node:** `Respond to Webhook`

This node sends the final response back to the frontend:

```json
{
  "reply": "AI response text"
}
```

It also includes:

* `Access-Control-Allow-Origin: *`
* Perfect compatibility with any frontend framework

---

## 🔐 Session Handling

Sessions are managed via a custom key:

```js
sessionId = localStorage.getItem('chat_session_id')
```

This ensures:

* Each visitor has their own memory
* Conversations persist across messages
* No data mixing between users

---

## 🌍 Language Behavior

The chatbot automatically:

* Replies in the **same language as the user**
* Defaults to **English** if unclear
* Uses simple explanations for technical topics

---

## 🎯 Primary Goal

> Provide a helpful, trustworthy, and pleasant chat experience for visitors of Tomy Vo’s portfolio website.

The chatbot acts as:

* A guide 🧭
* A technical explainer 🛠️
* A professional assistant 🤝

---

## 🛠️ Use Cases

✅ Portfolio websites
✅ Personal branding
✅ AI service showcases
✅ Freelancers & students
✅ AI‑powered landing pages

---

## 📦 Deployment Notes

* Requires **n8n with LangChain support**
* Requires **OpenRouter API credentials**
* Requires **PostgreSQL database** for memory
* Frontend can be any stack (HTML, React, Vue, etc.)

---

## 🌟 Final Thoughts

This workflow is a **clean, scalable, and production‑ready chatbot backend** designed specifically for personal portfolio websites. It combines strong AI reasoning, memory, and strict behavioral control to create a premium user experience.

If you want to extend it later:

* Add tools to the AI Agent
* Connect a vector database
* Add analytics or logging
* Add rate limiting

Happy building 🚀✨
