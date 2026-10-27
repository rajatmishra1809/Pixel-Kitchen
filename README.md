# 🎨 PixelKitchen — Cloud-Based Color Palette Generator

<p align="center">
  <strong>Every image has a palette waiting to be discovered.</strong>
  <br />
  Transform your favorite images into beautiful, customizable color palettes.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-Vite-61DAFB?logo=react&logoColor=white" alt="React and Vite" />
  <img src="https://img.shields.io/badge/Styling-Tailwind%20CSS-06B6D4?logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/Animations-Framer%20Motion-FF0080" alt="Framer Motion" />
  <img src="https://img.shields.io/badge/Cloud-AWS-FF9900?logo=amazonaws&logoColor=white" alt="AWS" />
  <img src="https://img.shields.io/badge/Status-In%20Development-orange" alt="Project status" />
</p>

---

## 📖 About the Project

**PixelKitchen** is a cloud-oriented web application that extracts dominant colors from uploaded images and transforms them into customizable color palettes. It provides an interactive workspace for exploring color combinations, previewing designs, and exporting palettes for use in web design, graphic design, and other creative projects.

The project demonstrates cloud architecture concepts through web hosting, serverless computing, cloud storage, and application monitoring using Amazon Web Services (AWS).

## ✨ Features

- 🖼️ **Image Upload & Curated Presets:** Upload images in JPG, JPEG, PNG, and WebP formats, or test instantly with curated landscape, architecture, and urban scenes.
- 🎨 **Client-Side Quantization Engine:** Extract 5–8 dominant colors directly in the browser via canvas without requiring paid AI APIs.
- 🔍 **Interactive Eyedropper:** Hover over images with a live magnifying loupe to sample and add any exact pixel color.
- 🌈 **Mathematical Color Harmonies:** Generate Complementary, Analogous, Triadic, Tetradic, Monochromatic, and Split-Complementary schemes.
- 🧪 **Precision Inspector:** Fine-tune colors using an interactive color wheel, HEX input, and real-time HSL sliders.
- 🔒 **Color Locking & Reordering:** Lock preferred colors and regenerate the remaining palette, or reorder swatches.
- 👁️ **Live Design Preview:** Real-time website mockup preview with Dark/Light mode and Desktop/Mobile responsive viewports.
- ♿ **Accessibility & CVD Matrix:** Real-time WCAG 2.1 AA/AAA contrast ratios and color blindness simulations (Protanopia, Deuteranopia, Tritanopia, Achromatopsia).
- 📋 **One-Click Copy:** Copy HEX codes with liquid glass feedback toasts.
- 💾 **Save Palettes:** Persist color collections locally with an AWS DynamoDB-ready storage architecture.
- 📦 **Multi-Format Export:** Export palettes as CSS variables, Tailwind CSS config, JSON, or downloadable 1200×680 high-res PNG cards.
- 🪟 **Liquid Glass UI:** Modern Apple-inspired glassmorphism with layered blur, ambient violet/cyan glows, and fluid Motion transitions.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| React | Component-based user interface |
| Vite | Development server and build tooling |
| Tailwind CSS | Responsive styling |
| Framer Motion | Animations and transitions |
| JavaScript Canvas / Color extraction library | Image color analysis |
| Amazon S3 / AWS Amplify | Static asset or frontend hosting |
| Amazon CloudFront | Content delivery |
| AWS Lambda | Serverless backend processing |
| Amazon API Gateway | Backend API endpoints |
| Amazon DynamoDB | Persistent palette storage |
| Amazon CloudWatch | Logs and monitoring |

AWS services are part of the planned architecture and should be marked as implemented only after deployment and integration.

## 🏗️ System Architecture

```mermaid
flowchart TD
    A[User] --> B[React + Vite Frontend]
    B --> C[Image Upload and Palette Editor]
    C --> D[Browser-Based Color Extraction]
    D --> E[Palette Generation and Export]

    B --> F[Amazon API Gateway]
    F --> G[AWS Lambda]
    G --> H[Amazon DynamoDB]

    B --> I[Amazon S3 / AWS Amplify Hosting]
    I --> J[Amazon CloudFront]
    G --> K[Amazon CloudWatch]
```

### Architecture Overview

1. **Frontend:** React provides the interactive palette editor and image upload interface.
2. **Color Processing:** Browser-based processing extracts colors without requiring a paid AI API.
3. **Hosting:** AWS Amplify or Amazon S3 with CloudFront delivers the frontend.
4. **Serverless Backend:** API Gateway and Lambda support backend operations when required.
5. **Database:** DynamoDB stores saved palettes and related metadata.
6. **Monitoring:** CloudWatch provides application logs and operational visibility.

The browser-based processing path can work independently of the AWS backend. Backend and database integrations are optional until implemented.

## 🚀 Getting Started

### Prerequisites

Make sure you have installed:

- [Node.js](https://nodejs.org/) — preferably an active LTS version.
- npm, included with Node.js.
- Git.
- A code editor such as Visual Studio Code.

### 1. Clone the repository

```bash
git clone https://github.com/rajatmishra1809/Pixel-Kitchen.git
```

### 2. Navigate to the project directory

```bash
cd Pixel-Kitchen
```

### 3. Install dependencies

```bash
npm install
```

### 4. Start the development server

```bash
npm run dev
```

Open the local URL displayed in your terminal:

```text
http://localhost:3000
```

### 5. Build for production

```bash
npm run build
```

Vite generates the production build in the `dist/` directory.

To preview the production build locally:

```bash
npm run preview
```

## 🌐 Deployment Options

### Option A: Vercel (Recommended for Quick Deploy)

PixelKitchen is pre-configured for Vercel with `vercel.json` (SPA rewrites) and `.npmrc` (`legacy-peer-deps=true`):

1. Go to [Vercel Dashboard](https://vercel.com/new).
2. Import your GitHub repository (`rajatmishra1809/Pixel-Kitchen`).
3. Vercel automatically detects the **Vite** framework preset with build command `npm run build` and output directory `dist`.
4. Click **Deploy**.

## ☁️ AWS Deployment

PixelKitchen can be deployed using AWS Amplify Hosting or Amazon S3 with CloudFront.

### Option A: AWS Amplify Hosting

1. Open the [AWS Amplify Console](https://console.aws.amazon.com/amplify/apps).
2. Connect your GitHub account.
3. Select the PixelKitchen repository and deployment branch.
4. Configure the build command as `npm run build`.
5. Set the output directory to `dist`.
6. Deploy the application.
7. Verify the deployed URL and test the main features.

Amplify can automatically redeploy the website when changes are pushed to the connected branch.

### Option B: Amazon S3 and CloudFront

1. Run `npm run build`.
2. Create an S3 bucket configured for secure static website delivery.
3. Upload the contents of `dist/`.
4. Configure CloudFront with the S3 bucket as its origin.
5. Configure appropriate access permissions and HTTPS delivery.
6. Test the deployed application.

For production use, prefer CloudFront with a private S3 origin rather than making the bucket publicly accessible.

## 💰 Cost Considerations

The project is designed to minimize infrastructure costs.

- Perform basic image processing in the browser.
- Avoid paid AI APIs and unnecessary backend calls.
- Use AWS services only when required.
- Monitor service usage and configure billing alerts.
- Remove unused resources after testing.

AWS usage is not guaranteed to be free. Charges depend on account eligibility, service usage, and applicable Free Tier allowances.

## 🎯 Project Objectives

- Develop an interactive web application for extracting and customizing color palettes from images.
- Demonstrate cloud architecture concepts through deployment, serverless computing, storage, and monitoring.
- Provide a practical, user-friendly design utility with palette editing and export capabilities.

## 🔮 Future Enhancements

- Multi-tenant user authentication and personalized cloud palette collections.
- Integration with AWS Cognito for managed identity and OAuth sign-in.
- Cloud-based bulk image processing through AWS Lambda.
- Instant palette sharing through unique short URLs and QR codes.
- Advanced procedural mesh gradient generation and CSS export.
- Real-time telemetry and palette trend analytics via Amazon CloudWatch.

## 🎓 Academic Information

| Field | Details |
|---|---|
| Project | PixelKitchen |
| Course | Cloud Architecture Design |
| Course Code | BCSE355L |
| Institution | Vellore Institute of Technology, Chennai Campus |
| Project Type | Individual Mini-Project |
| Deployment Platform | Amazon Web Services (AWS) |

## 👨‍💻 Author

**Rajat Mishra**

B.Tech — Computer Science and Engineering, AI & Robotics Specialization  
Vellore Institute of Technology, Chennai Campus

---

<p align="center">
  <strong>Made with creativity, code, and a little bit of color. 🎨</strong>
</p>
