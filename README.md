# @the-sintra/eslint-config-native

> ESLint 설정 패키지 for React Native (Expo)

React Native 및 Expo 프로젝트를 위한 엄격하고 일관된 코드 스타일 가이드라인을 제공하는 ESLint 설정입니다.

## 🚀 빠른 시작

### 1. 설치

```bash
npm install --save-dev @the-sintra/eslint-config-native eslint
```

### 2. TypeScript 호환성 조정

```bash
npm install --save-dev typescript@~5.5.4
```

### 3. Import resolver 설치

```bash
npm install --save-dev eslint-import-resolver-typescript --legacy-peer-deps
```

### 4. ESLint 설정 파일 생성

프로젝트 루트에 `.eslintrc.js` 파일을 생성하세요:

```javascript
module.exports = {
  extends: ["@the-sintra/eslint-config-native"],
  parserOptions: {
    project: __dirname + '/tsconfig.json',
  },
  settings: {
    'import/resolver': {
      typescript: {
        project: __dirname + '/tsconfig.json',
      },
    },
  },
};
```

### 5. .eslintignore 파일 생성

```
# ESLint configuration
.eslintrc.js

# Dependencies
node_modules/

# Build output
.expo/
dist/
build/

# Cache
.cache/
```

### 6. package.json 스크립트 추가

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

## 🎯 사용법

### 기본 사용

```bash
npm run lint
```

### 자동 수정

```bash
npm run lint:fix
```

## 📋 포함된 규칙

이 설정은 다음과 같은 ESLint 설정을 확장합니다:

- **airbnb**: 업계 표준 JavaScript/React 코딩 스타일
- **airbnb-typescript**: TypeScript용 airbnb 규칙
- **airbnb/hooks**: React Hooks 규칙
- **@typescript-eslint/recommended**: TypeScript 추천 규칙
- **react-native**: React Native 특화 규칙

## 🔧 TypeScript 지원

### 지원되는 TypeScript 버전

| typescript-eslint 버전 | TypeScript 지원 범위 | 권장사항 |
|------------------------|-------------------|----------|
| v7.18.0 (현재 사용)    | `>=4.7.4 <5.6.0` | TypeScript ~5.5.4 |
| v8.35.1 (최신)        | `>=4.8.4 <5.9.0` | TypeScript ~5.8.3 |

### TypeScript 5.6.0+ 사용하려면

최신 TypeScript를 사용하려면 다음 명령어로 업그레이드하세요:

```bash
npm install --save-dev typescript@~5.8.3
```

## 🛠️ 고급 설정

### 프로젝트별 규칙 추가

```javascript
module.exports = {
  extends: ["@the-sintra/eslint-config-native"],
  parserOptions: {
    project: __dirname + '/tsconfig.json',
  },
  settings: {
    'import/resolver': {
      typescript: {
        project: __dirname + '/tsconfig.json',
      },
    },
  },
  rules: {
    // 프로젝트별 규칙 추가
    'react-native/no-unused-styles': 'warn',
    'react-native/no-color-literals': 'error',
  },
};
```

### 특정 파일 제외

```javascript
module.exports = {
  extends: ["@the-sintra/eslint-config-native"],
  parserOptions: {
    project: __dirname + '/tsconfig.json',
  },
  settings: {
    'import/resolver': {
      typescript: {
        project: __dirname + '/tsconfig.json',
      },
    },
  },
  ignorePatterns: [
    '**/*.test.ts',
    '**/*.test.tsx',
    'metro.config.js',
  ],
};
```

## 🚨 문제 해결

### 1. `@typescript-eslint/recommended` 오류

```
Error: Cannot resolve configuration "@typescript-eslint/recommended"
```

**해결책:** 이미 패키지에 수정되어 있습니다. 최신 버전(1.0.4+)을 사용하세요.

### 2. TypeScript 버전 경고

```
WARNING: You are currently running a version of TypeScript which is not officially supported
```

**해결책:** 지원되는 TypeScript 버전으로 다운그레이드하세요:

```bash
npm install --save-dev typescript@~5.5.4
```

### 3. Import resolver 오류

```
Unable to resolve path to module
```

**해결책:** TypeScript resolver를 설치하고 설정하세요:

```bash
npm install --save-dev eslint-import-resolver-typescript --legacy-peer-deps
```

### 4. Parser 오류

```
Error: Error while loading rule '@typescript-eslint/...': You have used a rule which requires parserServices
```

**해결책:** `.eslintrc.js`에 `parserOptions.project` 설정을 추가하세요:

```javascript
module.exports = {
  extends: ["@the-sintra/eslint-config-native"],
  parserOptions: {
    project: __dirname + '/tsconfig.json',
  },
};
```

## 📦 의존성

### Peer Dependencies

```json
{
  "eslint": "^8.57.0",
  "typescript": ">=4.7.4 <5.6.0"
}
```

### 포함된 Dependencies

- `@typescript-eslint/eslint-plugin`: `^7.18.0`
- `@typescript-eslint/parser`: `^7.18.0`
- `eslint-config-airbnb`: `^19.0.4`
- `eslint-config-airbnb-typescript`: `^18.0.0`
- `eslint-plugin-import`: `^2.28.1`
- `eslint-plugin-jsx-a11y`: `^6.8.0`
- `eslint-plugin-react`: `^7.37.5`
- `eslint-plugin-react-hooks`: `^4.6.0`
- `eslint-plugin-react-native`: `^5.0.0`

## 🎮 예시 프로젝트

### 완전한 설정 예시

```javascript
// .eslintrc.js
module.exports = {
  extends: ["@the-sintra/eslint-config-native"],
  parserOptions: {
    project: __dirname + '/tsconfig.json',
  },
  settings: {
    'import/resolver': {
      typescript: {
        project: __dirname + '/tsconfig.json',
      },
    },
  },
  rules: {
    // 프로젝트 특성에 맞는 규칙 조정
    'react-native/no-unused-styles': 'warn',
    'react-native/no-color-literals': 'error',
    'import/prefer-default-export': 'off',
  },
};
```

### package.json 예시

```json
{
  "scripts": {
    "start": "expo start",
    "android": "expo start --android", 
    "ios": "expo start --ios",
    "web": "expo start --web",
    "lint": "eslint .",
    "lint:fix": "eslint . --fix",
    "type-check": "tsc --noEmit"
  },
  "devDependencies": {
    "@the-sintra/eslint-config-native": "^1.0.4",
    "eslint": "^8.57.0",
    "eslint-import-resolver-typescript": "^3.6.0",
    "typescript": "~5.5.4"
  }
}
```

## 📚 추가 리소스

- [ESLint 공식 문서](https://eslint.org/)
- [TypeScript ESLint 문서](https://typescript-eslint.io/)
- [Airbnb JavaScript 스타일 가이드](https://github.com/airbnb/javascript)
- [React Native ESLint 플러그인](https://github.com/Intellicode/eslint-plugin-react-native)

## 🤝 기여하기

이슈나 개선사항이 있으시면 [GitHub Issues](https://github.com/the-sintra/guideline-native/issues)에 등록해주세요.

## 📄 라이센스

MIT License

## 👨‍💻 개발자

- **Sungju Cho** - [@iamfiro](https://github.com/iamfiro)
- **Email**: hello@devfiro.com

---

**⚡️ 빠른 설정 명령어 모음**

```bash
# 1. 기본 설치
npm install --save-dev @the-sintra/eslint-config-native eslint

# 2. TypeScript 호환성 조정
npm install --save-dev typescript@~5.5.4

# 3. Import resolver 설치
npm install --save-dev eslint-import-resolver-typescript --legacy-peer-deps

# 4. ESLint 실행
npm run lint
```

이제 React Native 프로젝트에서 일관된 코드 스타일을 유지할 수 있습니다! 🎉 