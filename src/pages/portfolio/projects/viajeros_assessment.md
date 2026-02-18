---
layout:  /src/layouts/ProjectLayout.astro
title: 'Viajeros Assessment'
pubDate: 2026-02-18
description: 'Viajeros Assessment is a web application for digital assessment aimed at educational institutions, mainly for the Cosmo Schools educational model.'
languages: ["react", "ts"]
image:
  url: "/images/projects/VA.webp"
  alt: "viajeros-assessment-image."
--- 

# Viajeros Assessment — Digital Assessment Platform

## Project objective

**Viajeros Assessment** is a web application for digital assessment aimed at educational institutions, mainly for the Cosmo Schools educational model. It lets students take tests by modules (by grade and subject), with a guided flow from login through viewing results and collecting feedback (NPS). The frontend consumes a REST API, manages progress state on the client, persists answers and timings, and provides a responsive, accessible experience throughout the journey.

---

## Technical description

### Purpose and context

The platform covers the full assessment cycle: **authentication**, **test period selection**, **welcome**, **module selection via carousel**, **question answering per module**, and **completion with results and NPS survey**. It is designed for institutional settings where assessment is done by periods and by modules (e.g. by grade), with progress tracking (started, in progress, completed) and achievement levels.

### Tech stack

| Layer | Technology |
|------|------------|
| **Runtime / Build** | React 19, Vite 7, TypeScript 5.9 |
| **Global state** | Redux Toolkit (store configured; optional use vs. local state + persistence) |
| **Routing** | React Router v7 (createBrowserRouter, protected routes) |
| **Styling** | Tailwind CSS v4 (@tailwindcss/vite), tw-animate-css, class-variance-authority (CVA), clsx, tailwind-merge |
| **UI / UX** | Radix UI (Label, Slot), Embla Carousel, Lucide React, React Icons, react-hot-toast |
| **Code quality** | ESLint 9, Prettier, TypeScript strict |


### Architecture and data flow

- **Centralized API**: HTTP client in `apiClient` with `Authorization: Bearer` injection from `sessionStorage`, standard response handling and typed errors (`ApiClientError`).
- **Environment variables**: Config in `config/env.ts`; in development the Vite proxy (`/api` → real API) is used to avoid CORS.
- **Protected routes**: `ProtectedRoute` component checks `authService.isAuthenticated()` and redirects to `/` when there is no session.
- **User flow**: Login → User Validation → Test Period Selection → Welcome Test → Module Selection → Question Selection → Question View (per question). Additional routes: No Product Assigned and catch-all to Login.


---

## Conclusion

Viajeros Assessment is a **digital assessment frontend** built with React 19 + TypeScript + Vite, integrated with a REST API, with client-side progress and timing persistence, module carousel, question flow with on-demand content and options, per-module results with achievement levels, and a post-assessment NPS survey. The description above serves as a technical and structural basis to present the project in a portfolio in a detailed and appealing way for recruiters or technical audiences.



## 🌐 Demo

👉 [View live demo](https://viajeros.assessment.selecu.net/) 


🚀 *Developed by STGRL.*
