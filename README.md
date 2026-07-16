# Prashanth Akula Portfolio — 3D Interactive Upgrades

Welcome to the documentation for the high-end 3D upgrades integrated into **Prashanth Akula's Motion & Edit Portfolio**. This single-page luxury portfolio has been elevated with premium, zero-dependency 3D graphics and spatial interaction designs inspired by award-winning Awwwards portfolios.

---

## 🚀 Key 3D Features

### 1. Interactive 3D Particle Plexus Sphere
The landing screen features a custom, high-performance HTML5 Canvas-based 3D particle system that rotates and morphs dynamically.
* **Golden Spiral Distribution**: 140 particles are mathematically mapped across a virtual 3D sphere using a golden ratio spherical distribution.
* **Multi-Axis 3D Rotation**: The system calculates continuous 3D coordinate transformations using trigonometric matrices (sine/cosine) to rotate the sphere in real-time.
* **Interactive Tilt**: Moving the cursor across the viewport applies subtle gravitational tilt and speed changes, making the sphere react dynamically to user actions.
* **Organic Morphing**: A slow, sinusoidal morphing function fluctuates the radius of individual particles over time, creating a breathing, liquid-like constellation.
* **Perspective Projection & Depth Cueing**: Perspective scaling is calculated per-particle ($scale = \frac{fov}{fov + z + distance}$). Particles closer to the screen are rendered larger, brighter, and with an added neon bloom effect, while background elements dim and shrink.
* **Proximity Connectors**: Connecting lines are drawn between neighboring particles, with line transparency dynamically linked to the distance between them.
* **Non-Blocking Overlay**: Configured with `pointer-events: none` and z-indices to run smoothly in the background without blocking user clicks on links or call-to-action buttons.

### 2. 3D Layered Parallax Hover Cards
All **Featured Work** project cards and **Software Proficiency** cards feature an interactive 3D tilt response.
* **Cursor-Relative Math**: Tracks the exact hover coordinates relative to the card's center to apply dynamic, responsive rotation angles:
  ```javascript
  const rx = -(y - yc) / (yc / 12); // rotateX
  const ry = (x - xc) / (xc / 12);  // rotateY
  ```
* **True 3D Depth**: Built using CSS `transform-style: preserve-3d` to allow child layers to exist in a real 3D spatial field.
* **Parallax Pop-Out**: Inner layers (such as video thumbnails and metadata text) are pushed forward using `translateZ(30px)` and `translateZ(15px)`. When the card rotates, these layers slide relative to the card border, creating an immersive, multi-layered depth effect.

---

## 🛠️ Technical Stack & Architecture

* **Framework**: React + Vite (Fast HMR & build pipelines)
* **Styling**: Premium Vanilla CSS + scoped JSX style tags
* **3D Math Engine**: Vanilla JS Canvas 2D engine (zero external dependencies like Three.js, ensuring instant load times and lightweight bundle size)
* **Icons**: Lucide React
* **Linter**: Oxlint (Ultra-fast code quality verification)

---

## ⚡ Performance Optimization

* **GPU Acceleration**: Heavy transformations (3D rotations, perspective scaling, and card shadows) are offloaded to the GPU to ensure a locked 64 FPS on both desktop monitors and high-refresh-rate mobile devices.
* **No Library Footprint**: Avoids heavy 3D library dependencies, keeping the JavaScript bundle light ($~340\text{ KB}$ including all assets, video preview generation, and components).
* **Client-Side Video Previews**: Automatically extracts the first frame of project videos dynamically in the browser on load, avoiding the need for heavy image assets.
