# z3d-cv-portfolio

A Python-based photogrammetry pipeline for 3D face reconstruction—packed with CV buzzwords and built to impress.

## 🚀 Project Overview

This end‑to‑end project showcases core Computer Vision techniques:
- **Structure‑from‑Motion (SfM):** feature detection & matching, camera pose estimation via COLMAP  
- **Multi‑View Stereo (MVS):** dense point‑cloud generation and mesh reconstruction with OpenMVS  
- **3D Mesh Processing:** mesh refinement, UV unwrapping, texture baking  
- **Visualization & Rendering:** interactive viewing and stylized shading using `trimesh` & `pyrender`  
- **Automation & DevOps:** Python orchestration scripts and Docker containerization

## 📂 Repository Structure

face3d-cv-portfolio/ ├── images/ # Raw capture photos ├── prepped/ # Pre‑processed (cropped/resized) images ├── scripts/ │ ├── capture_setup.md # DIY capture guidelines │ ├── run_sfm.py # COLMAP SfM orchestration │ ├── run_mvs.sh # OpenMVS dense reconstruction pipeline │ ├── render.py # Load & render mesh with pyrender │ └── preprocess.sh # ImageMagick batch crop/resize ├── Dockerfile # Containerize the pipeline ├── requirements.txt # Python dependencies ├── README.md # Project overview & instructions └── LICENSE

markdown
Copy

## 🛠️ Key Features

1. **Automated SfM & MVS**  
   - One‑line COLMAP “automatic_reconstructor” for sparse point cloud & camera poses  
   - Bash scripts to convert to OpenMVS format, densify, mesh, refine, and texture  

2. **Python Integration**  
   - `run_sfm.py`: wraps COLMAP commands via `subprocess`  
   - `render.py`: interactive viewer with `trimesh` & `pyrender`, plus turntable animation export  

3. **Stylized Rendering**  
   - Rim‑lighting, edge‑enhancement, HDRI environment mapping  
   - Optional neural rendering extension with PyTorch3D  

4. **Amateur‑Friendly Capture**  
   - DIY setup guide for phone‑only rigs (Lazy Susan, floor markers, consistent lighting)  
   - Pre‑processing scripts to batch‑crop and standardize images for robust matching  

5. **Containerized Deployment**  
   - Dockerfile installs COLMAP, OpenMVS, and Python libs—reproduce anywhere  
   - Configurable parameters for image paths, resolution levels, and rendering options  

## 🎯 Getting Started

1. **Clone the repo**  
   ```bash
   git clone https://github.com/yourusername/face3d-cv-portfolio.git
   cd face3d-cv-portfolio
Build Docker image

bash
Copy
docker build -t face3d-cv .
Run the full pipeline

bash
Copy
docker run --rm \
  -v $(pwd)/images:/app/images \
  -v $(pwd)/prepped:/app/prepped \
  face3d-cv \
  bash -c "./scripts/preprocess.sh && python scripts/run_sfm.py && bash scripts/run_mvs.sh && python scripts/render.py"
Customize & Extend

Tweak capture positions in scripts/capture_setup.md

Adjust resolution (--resolution-level) in scripts/run_mvs.sh

Integrate PyTorch3D neural renderer in scripts/render.py

📜 License
MIT License. See LICENSE for details.

