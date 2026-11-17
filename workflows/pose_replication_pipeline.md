# Pose Replication & Character Customization Pipeline

This guide outlines the exact, repeatable workflow to replicate this executive studio portrait for yourself or a client without running into identity drift, synthetic skin textures, or broken hand anatomy.

---

### The 2-Step "Physical Reverse-Engineering" Workflow

Most people fail at character generation because they try to describe themselves from memory and use vague words like "handsome man" or "black guy with dreadlocks", which forces the AI model to guess and invent a generic stranger. 

To lock your real biological likeness into the master prompt on the first try, use this quick reverse-engineering step:

#### Step 1: Extract Your Physical Signature Using Vision AI
Take a well-lit, unedited photo of your face, upload it to ChatGPT, Claude, or Google Gemini, and use this exact intake prompt:

```text
Analyze this photo of me and write a concise, highly specific 3-sentence description of my physical appearance for a photo prompt. Focus strictly on:
1. Exact facial bone structure, jawline contour, and eye shape.
2. Natural skin undertone, pigmentation, and melanin depth.
3. Precise hairstyle, loc thickness, hairline shape, and facial hair grooming style.
Do not use flattering or generic adjectives; keep it factual, grounded, and photographic.
```

#### Step 2: Inject Your Signature into the Master Prompt
Take the resulting 3 sentences and paste them directly into the `[CHARACTER & IDENTITY]` section of `prompts/01_master_universal_studio_prompt.txt`, replacing the placeholder text.

When you feed that combined prompt along with your uploaded photo into Google Flow (Nano Banana Pro) or ChatGPT, the diffusion engine anchors to your exact biological reality instead of generating an artificial catalog model.

---

### Multimodal Token Weighting in Google Flow

When working in Google Flow or similar canvas environments:
1. **Primary Token (`Character Reference`):** Upload your own portrait photo.
2. **Text Binding Layer:** Paste the Master Prompt into the text field, referencing your image tag.
3. **Negative Armor:** The negative parameters are already baked into the master prompt to prevent plastic skin smoothing and digit fusion during the crossed-arms render.

---

### Hand Anatomy & Finger QA

Crossed-arm stances place hands directly over opposing arms, which is historically where diffusion models fail by fusing fingernails or bending joints backwards.

If a generation captures your face perfectly but softens a knuckle or fingernail:
1. Never re-roll the entire prompt and risk losing a great face render.
2. Use localized inpainting or an image-to-image edit pass focused strictly on the hand bounding box.
3. Prompt: `"High-resolution photographic hand resting on forearm, crisp individual fingers, authentic knuckle creases, natural fingernails."`
