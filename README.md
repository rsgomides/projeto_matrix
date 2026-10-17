# 🟢 Matrix Impact Hub

Apresentação interativa de página única, no estilo visual do universo *Matrix*, que usa a metáfora da **pílula azul vs. pílula vermelha** para confrontar o senso comum popular com evidências/dados reais sobre um tema de sua escolha (configurado atualmente para **investimentos e mercado financeiro**).

Construído em **HTML, CSS e JavaScript puros** — sem frameworks, sem build step, sem dependências de terceiros. Basta abrir o arquivo no navegador.

---

## ✨ Demonstração do fluxo

1. **Cena 1 — Introdução:** o fundo "chuva digital" da Matrix toca em loop. Uma cortina de vídeo temático sobe sobre a tela, reproduz um vídeo de abertura e desce, revelando o título, uma narração digitada em efeito *typewriter* e o botão de entrada.
2. **Cena 2 — A Escolha:** o usuário escolhe entre a **Pílula Azul** (ilusão/senso comum) ou a **Pílula Vermelha** (realidade/dados). Cada escolha revela um painel de conteúdo com transição de *glitch*.
3. **Textos cíclicos:** cada pílula guarda até **10 textos diferentes**. Clicar repetidamente na mesma pílula avança para o próximo texto da lista (com indicador "X / 10"), voltando ao primeiro depois do último.
4. **Resetar:** um botão permite reiniciar toda a simulação, voltando à Cena 1 e zerando os contadores de texto.

---

## 🧰 Stack técnica

| Camada | Tecnologia |
|---|---|
| Estrutura | HTML5 semântico |
| Estilo | CSS3 (`clamp()`, `flexbox`, `backdrop-filter`, `prefers-reduced-motion`) |
| Interatividade | JavaScript vanilla (ES6+), sem dependências externas |
| Mídia | `<video>`, `<audio>`, `<canvas>` (chuva digital) |
| Fontes | Google Fonts (`Orbitron`, `Share Tech Mono`) via CDN |

Não há etapa de build, bundler ou `node_modules` — o projeto é **100% estático**.

---

## 📁 Estrutura de arquivos esperada

```
matrix-impact-hub/
├── index.html              ← arquivo principal (este projeto)
├── matrix-bg.mp4            ← vídeo de fundo em loop (chuva digital / código)
├── matrix-poster.jpg        ← imagem exibida enquanto matrix-bg.mp4 carrega
├── theme-video.mp4          ← vídeo de abertura da Cena 1 (cortina)
├── morpheus-dialogue.jpg    ← imagem do mentor na Cena 1 (aceita .jpg/.jpeg/.png/.webp)
├── morpheus-pills.jpg       ← imagem do mentor com as pílulas na Cena 2
└── intro-music.mp3          ← música de fundo da Cena 1 (opcional, desativada por padrão)
```

> ⚠️ **Nenhum desses arquivos de mídia está incluído no repositório.** O HTML foi projetado para funcionar mesmo sem eles — imagens ausentes mostram um aviso visível (⚠️) ao invés de quebrar o layout, vídeos ausentes simplesmente não aparecem, e áudio ausente é ignorado silenciosamente.

---

## 🚀 Como usar

### Opção 1 — Direto no navegador
Baixe/clone o repositório e dê duplo clique no `index.html`. Funciona via `file://` sem precisar de servidor.

### Opção 2 — Servidor local (recomendado para evitar restrições de autoplay)
```bash
# Com Python instalado
python3 -m http.server 8000

# Depois acesse:
http://localhost:8000
```

### Publicando no GitHub Pages
1. Suba este repositório para o GitHub
2. Vá em **Settings → Pages**
3. Em "Branch", selecione `main` (ou a branch desejada) e a pasta `/root`
4. Acesse a URL gerada pelo GitHub — a apresentação estará disponível publicamente

---

## 🎨 Personalização

### Textos principais
No `<script>`, edite o objeto de configuração:
```js
const CONFIG = {
    introText: "...",   // narração digitada da Cena 1
    choiceText: "...",  // texto explicativo da Cena 2
    typingSpeed: 40      // velocidade do efeito de digitação (ms por caractere)
};
```

### Textos das pílulas (até 10 cada)
Edite os arrays `illusionTexts` (pílula azul) e `realityTexts` (pílula vermelha). Cada posição da lista é exibida em um clique — não precisa ter exatamente 10 itens, o contador se ajusta ao tamanho de cada array.

### Imagens
Qualquer imagem referenciada aceita `.jpg`, `.jpeg`, `.png` ou `.webp` automaticamente — basta salvar com o nome-base correto (ex: `morpheus-pills.png` funciona sem alterar o código).

### Vídeo de abertura (cortina)
Troque `theme-video.mp4` pelo vídeo desejado. **Importante:** navegadores não reproduzem o contêiner `.mkv` nativamente — o arquivo precisa estar em `.mp4` (H.264).

### Música de fundo da Cena 1
Está desativada por padrão. Para reativar, altere:
```js
const INTRO_MUSIC_ENABLED = false;  // troque para true
```

### Acessibilidade
O projeto já respeita a preferência de sistema `prefers-reduced-motion`, desativando animações para usuários sensíveis a movimento.

---

## ⚠️ Avisos e limitações conhecidas

- **Autoplay de áudio/vídeo com som:** navegadores modernos bloqueiam reprodução automática de mídia com som antes de qualquer interação do usuário. O projeto já trata isso com fallback (tenta tocar mudo e libera o som no primeiro clique), mas em apresentações ao vivo recomenda-se um clique inicial na tela.
- **Formatos de vídeo:** use sempre `.mp4` (H.264/AAC). Formatos como `.mkv` ou `.avi` não são suportados pela tag `<video>` em nenhum navegador.
- **Direitos de imagem/personagens:** este projeto usa um "mentor" com identidade visual própria, inspirado na estética do filme *Matrix*, mas sem reproduzir personagens protegidos por direitos autorais.

---

## 📄 Licença

Defina aqui a licença do seu projeto (ex: MIT, uso pessoal/educacional, etc.) — este README não assume nenhuma licença por padrão.

---

## 🙋 Suporte

Projeto desenvolvido de forma iterativa para fins de apresentação/educação. Para dúvidas sobre customização, consulte os comentários `<!-- EDIT: ... -->` espalhados pelo próprio arquivo `index.html`, que marcam exatamente onde cada ajuste deve ser feito.
