---
layout: section
---

# O que é o Next.js?


---
level: 2
layout: image-right

# the image source
image: /next-logo.png

# a custom class name to the content
class: my-cool-content-on-the-left
---

# O que é o Next?

É um framework open-source para criação de aplicações em React.

Ele foi criado e é mantido pela equipe Vercel.

O Next fornece um pacote completo de funcionalidades, para facilitar o desenvolvimento de apps react.

---

## 🤷🏽‍♂️ Por que eu deveria utilizar o Next.js?

<br />

- Sistema de roteamento fácil de usar, sem a necessidade de configuração inicial
- Baixo nível de acoplamento do framework
- Sistema de build
- Suporte a Typescript
- Eslint
- etc

---
level: 2
layout: image-right

# the image source
image: /code.jpg

# a custom class name to the content
class: my-cool-content-on-the-left
---

## O que o Next.js pode fazer?

<br/>

- Criação de APIs
- Criação de apps no SSR (Server-Side Rendering)
- Criação de apps no Client
- Exportações estáticas

---
layout: center
class: text-center
---
# Estratégias de renderização


### ✨✨✨ Onde o Next.js brilha! ✨✨✨
![brilho](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExYW82ZmxoejhidjBwMXR0dW9wYzA4cm40aGlweTJpZnA4dXhoNTZ5cSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3ov9jQsTzqjSyIWRDa/giphy.gif)

---
level: 2
layout: image-right

# the image source
image: /server-and-client.jpg

# a custom class name to the content
class: my-cool-content-on-the-left
---

### Estratégias de renderização

<br/>
<br/>

#### CSR (Client side rendering)
Renderização é feita do Lado do cliente

<br/>

#### SSR (Server-Side Rendering)
Renderização toda feita no servidor

<br/>

### SSG (Static site generation)
Gera páginas estáticas

---

## Iniciando uma app com Next

Para criar uma aplicação com Next, apenas rode o comando:

```sh
npx create-next-app@latest
```

Responda suas preferências:

```sh
What is your project named? my-app
Would you like to use TypeScript? No / Yes
Would you like to use ESLint? No / Yes
Would you like to use Tailwind CSS? No / Yes
Would you like to use `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
Would you like to customize the default import alias (@/*)? No / Yes
What import alias would you like configured? @/*
```

---
level: 2
layout: image-right

# the image source
image: /pastas.png

# a custom class name to the content
class: my-cool-content-on-the-left
---

## Anatomia de uma app Next

<br/>

- page.tsx: Rota na aplicação
    - `src/app/credit/page.tsx` -> /credit
    - `src/app/credit/loan/[id].tsx` -> /credit/loan/123
- route: Cria uma rota de "API"
    - `src/app/users/route.ts` -> /users
- public: Arquivos estáticos
- `next.config.js`: Arquivo de configuração do next

---

## Criando minha APP

<br>

#### CSR (Client side rendering)

```js
'use client'
import { useState, useEffect } from 'react'
 
export default function Page() {
  const [data, setData] = useState<any>(null)
 
  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch('https://swapi.py4e.com/api/people/1')
      const result = await response.json()
      setData(result)
    }
    ...
  }, [])
 
  return <p>{data ? `Your data: ${data?.name}` : 'Loading...'}</p>
}

```

---


## Criando minha APP

<br>

#### SSR
```js
async function getData() {
    const res = await fetch('https://swapi.py4e.com/api/people/1')
    if (!res.ok) throw new Error('Failed to fetch data')
   
    return res.json()
}

export default async function ServerPage() {
    const data = await getData()
   
    return <main>{data.name}</main>
}
```

---

## Criando minha APP

<br>

### SSG

Adicione a configuração ao seu arquivo `next.config`

```js
// next.config.js
const nextConfig = {
  output: 'export',
  ...
}

```

---


## Criando minha APP

<br>

### API

Adicione a configuração ao seu arquivo `next.config`

```js
// src/app/users/route.ts => GET - /users

import { NextResponse } from 'next/server'

async function getData() {
  const res = await fetch('https://swapi.py4e.com/api/people')
  if (!res.ok) throw new Error('Failed to fetch data')

  return res.json()
}

export async function GET(request: Request) {
  const data = await getData()
  const names = data.results.map((people: any) => people.name)

  return NextResponse.json(names)
}

```

---

# Extras
O Next é um framework muito poderoso e popular. Existem muitas outras features, caso você queira se aprofundar.

- Internacionalização
- Middleware
- Customização para páginas de erros
- Lazy loading
- Otimização de bundle
- etc...

---
layout: center

---
## Dúvidas?

![Perguntas](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMTk3ZWs2d3NoMDVlcWp3azU5YWprZjh1OWZ3dWR6dTV6aXBxNjBjMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZXwdJuk172dQwAqMGv/giphy.gif)

---
layout: center
---
# FIM!
![fim](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDY1dDdwYmd1aGFhc3pwZ2N6MTFpM29rMHNycXZ2N3JhdWN1cmhpMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/7yojoQtevjOCI/giphy.gif)