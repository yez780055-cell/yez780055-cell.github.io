# Cozy Days TWA domain

This repository is reserved for the root GitHub Pages origin:

- Origin: https://yez780055-cell.github.io
- Purpose: Android Trusted Web Activity (TWA) Digital Asset Links verification.
- Web app: https://yez780055-cell.github.io/cozy-days-app/

## Current status

The `.well-known/assetlinks.json` file is intentionally an empty JSON array (`[]`). It is syntactically valid but does **not** authorize any Android app yet.

After the Android package is built with Bubblewrap, replace the placeholder with the exact package name and SHA-256 fingerprint of the signing certificate used for the distributed APK/AAB:

```json
[
  {
    "relation": ["delegate_permission/common.handle_all_urls"],
    "target": {
      "namespace": "android_app",
      "package_name": "YOUR_ANDROID_APPLICATION_ID",
      "sha256_cert_fingerprints": ["YOUR_RELEASE_SIGNING_CERTIFICATE_SHA256"]
    }
  }
]
```

Do not publish guessed package names or certificate fingerprints. If Play App Signing is used, publish the app-signing certificate fingerprint from Play Console, not the upload-key fingerprint.

## GitHub Pages

Configure Pages to deploy from the `main` branch, root folder, or switch Pages to GitHub Actions and add a deployment workflow. Then verify:

- `https://yez780055-cell.github.io/`
- `https://yez780055-cell.github.io/.well-known/assetlinks.json`

Both must be served over HTTPS. The asset links endpoint must return JSON with an appropriate content type.

## Safety boundary

This repository is separate from `cozy-days-app`. It does not change that repository, its `main` branch, or its deployment.
