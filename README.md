# eslint-configs

Geteilte ESLint-Konfiguration (Flat Config, ESLint 10) mit zwei Presets:

- `eslint-configs/base` für TypeScript
- `eslint-configs/angular` für Angular-Apps, mit Template-Regeln

## Einbinden

Als devDependency mit festem Tag, in jedem Paket, das lintet:

```sh
pnpm add -D "eslint-configs@git+https://github.com/wittlaknauer/eslint-config.git#v1.0.2" eslint typescript
```

`eslint.config.mjs` im Paket:

```js
import baseConfig from "eslint-configs/base";

export default [
  ...baseConfig,
  {
    files: ["**/*.ts"],
    languageOptions: {
      parserOptions: { projectService: true, tsconfigRootDir: import.meta.dirname },
    },
  },
];
```

Dazu in der `package.json` das Script `"lint": "eslint ."`.

## Neue Version

Änderung committen, Tag `vX.Y.Z` setzen und mit dem Tag pushen. Projekte heben danach den Tag in ihrer
Abhängigkeit an.
