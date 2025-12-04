# Homey Plate Food Gallery

A photo gallery website built with Hugo and the [hugo-theme-gallery](https://github.com/nicokaiser/hugo-theme-gallery) theme.

## Local Development

To run the site locally:

```bash
hugo server -D
```

The site will be available at `http://localhost:1313/`

## Adding Content

### Creating a New Album

1. Create a new folder in the `content/` directory (e.g., `content/italian-dishes/`)
2. Add an `index.md` file with front matter:

```markdown
---
title: "Italian Dishes"
date: 2025-12-03
description: "A collection of Italian recipes and dishes"
---
```

3. Add your images (JPG, PNG) to the same folder
4. The first image or any image with "feature" in the filename will be used as the album cover

### Image Organization

- Images are automatically displayed in a justified gallery layout
- Images can have titles from EXIF data or front matter
- Albums without images won't be shown in the gallery

## Deploying to Cloudflare Pages

### Prerequisites

1. A Cloudflare account (free tier is fine)
2. Your code pushed to a GitHub, GitLab, or Bitbucket repository

### Deployment Steps

1. **Push your code to a Git repository** (if not already done):
   ```bash
   # Add your remote repository
   git remote add origin https://github.com/yourusername/homeyplatefood.git

   # Push the code
   git push -u origin main
   ```

2. **Log in to Cloudflare Dashboard**:
   - Go to [dash.cloudflare.com](https://dash.cloudflare.com)
   - Navigate to "Workers & Pages"

3. **Create a New Pages Project**:
   - Click "Create application"
   - Select "Pages" tab
   - Click "Connect to Git"
   - Choose your Git provider (GitHub, GitLab, or Bitbucket)
   - Authorize Cloudflare to access your repositories
   - Select the `homeyplatefood` repository

4. **Configure Build Settings**:
   - **Project name**: `homeyplatefood` (or your preferred name)
   - **Production branch**: `main`
   - **Build command**: `hugo --gc --minify`
   - **Build output directory**: `public`
   - **Environment variables**:
     - Variable name: `HUGO_VERSION`
     - Value: `0.133.1` (or your Hugo version)

5. **Deploy**:
   - Click "Save and Deploy"
   - Cloudflare Pages will build and deploy your site
   - Your site will be available at `https://homeyplatefood.pages.dev/`
   - You can also add a custom domain in the Pages settings

### Continuous Deployment

Once set up, every push to your `main` branch will automatically trigger a new deployment on Cloudflare Pages.

### Custom Domain (Optional)

1. In your Cloudflare Pages project, go to "Custom domains"
2. Click "Set up a custom domain"
3. Enter your domain name
4. Follow the instructions to update your DNS settings

## Theme Configuration

The site uses the hugo-theme-gallery theme. Configuration options are in `hugo.toml`:

- `params.defaultTheme`: Set to "light" or "dark"
- `params.gallery`: Gallery-specific settings
- `params.socialIcons`: Add social media links
- `imaging`: Image processing settings

For more configuration options, see the [theme documentation](https://github.com/nicokaiser/hugo-theme-gallery).

## Site Structure

```
content/
├── _index.md              # Homepage
├── about.md               # About page
└── sample-dishes/         # Sample album
    └── index.md
```

## Important Notes

- **Do not use WebP images** - Hugo's WebP implementation has a bug that causes dull-looking images
- Use JPG or PNG format for best results
- Images are automatically resized and optimized during build
- Original EXIF data can be preserved or stripped based on configuration

## Requirements

- Hugo Extended >= 0.123.0
- Git (for theme submodule and deployment)

## License

This site uses the hugo-theme-gallery theme, which is licensed under the MIT License. Ray
