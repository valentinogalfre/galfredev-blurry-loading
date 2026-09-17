# Proyecto 01 – Blurry Loading

Efecto de **blur progresivo** a pantalla completa con contador accesible. Proyecto 01/15 de la serie de mini-proyectos de GalfreDev.

🔗 **[Demo en GitHub Pages](https://valentinogalfre.github.io/galfredev-blurry-loading/)**

## Cómo funciona

`src/components/BlurryLoader.tsx` avanza un contador de 0 a 100 y mapea el progreso a un `filter: blur()` que va de `maxBlurPx` (24 px por defecto) a 0. El estado se expone con `role="progressbar"` y un texto `aria-live="polite"` para lectores de pantalla.

## Stack

- Vite + React + TypeScript
- Tailwind CSS
- pnpm (`packageManager` en `package.json`; los build scripts permitidos viven en `pnpm-workspace.yaml`)

## Correr local

```bash
pnpm install
pnpm dev        # http://localhost:5173
pnpm build      # tsc -b && vite build → dist/
```

## Flujo de trabajo

| Rama | Environment (GitHub) | Uso |
|---|---|---|
| `develop` (default) | `staging` | Integración: acá entran fixes y features, por PR o push directo. |
| `main` | `production` | Producción: solo recibe merges desde `develop`. |

CI (`.github/workflows/ci.yml`) corre en cada push a `develop`/`main` y en cada PR. Para reproducirlo local:

```bash
pnpm install --frozen-lockfile
pnpm lint && pnpm build
```

**Promover a producción:** PR `develop → main` (o `git checkout main && git merge --ff-only develop && git push`). El push a `main` publica en GitHub Pages (`pages.yml`).
