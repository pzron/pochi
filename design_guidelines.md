# Web3 Social Platform Design Guidelines

## Design Foundation

**Reference-Based Approach**: Twitter/X architecture + Web3 aesthetics (Rainbow Wallet, Zora, Lens). Combines familiar social UX with crypto-native visuals (gradients, glassmorphism, elevated cards).

**Core Principles**: Familiar patterns, balanced density, visible blockchain interactions, wallet-first auth, trust through transparency.

---

## Layout System

**Desktop Structure**:
- Three-column: Left nav (w-64), center feed (max-w-2xl), right sidebar (w-80)
- Left: Sticky nav with logo, actions, wallet info
- Center: Scrollable feed with readability constraints
- Right: Trending, suggestions, token stats

**Spacing**: Tailwind units 1-2-3-4-6-8-12-16
- Component padding: p-4, p-6, p-8
- Vertical spacing: space-y-4, space-y-6
- Icon-text gaps: gap-2, gap-3

**Responsive**:
- **Desktop (lg+)**: Full three-column
- **Tablet (md)**: Two-column, hide right sidebar, collapsible left nav
- **Mobile**: Single column, bottom nav (5 actions), hamburger menu

---

## Typography

**Fonts**:
- Primary: Inter (400, 500, 600, 700) - UI, body, navigation
- Monospace: JetBrains Mono (400, 500) - addresses, hashes

**Scale**:
- Display: text-4xl/5xl font-bold (profile names, modal titles)
- Headings: text-2xl/3xl font-semibold (sections)
- Subheadings: text-lg/xl font-medium (cards, usernames)
- Body: text-base font-normal (posts, descriptions)
- Small: text-sm font-normal (metadata, timestamps)
- Micro: text-xs font-medium (labels, badges)

**Examples**: Post author (text-base font-semibold), timestamp (text-sm), token amounts (text-lg font-bold monospace), wallet addresses (text-sm font-mono).

---

## Core Components

### Navigation

**Left Sidebar**:
- Logo: h-16 with brand
- Nav items: py-3 px-4, rounded-full, icon + label (gap-4)
- Active: filled background
- Primary action (Create): w-full py-3 rounded-full
- Bottom: wallet info, balance, settings

**Mobile Header**: Fixed h-16, centered logo, wallet status, notifications

### Feed

**Post Card**:
```
- Container: border rounded-lg p-4, hover elevation
- Header: Avatar (h-12 w-12 rounded-full) + username + timestamp + verified + menu
- Content: mt-3, relaxed line-height
- Media: mt-3 rounded-lg, aspect-video/square
- Actions: mt-4 flex justify-between (like, repost, comment, tip)
- NFT badge: top-right indicator
```

**Create Post Modal**:
```
- max-w-2xl rounded-2xl
- Header: title, character count, close
- Textarea: min-h-32, auto-expand
- Media: drag-drop with preview
- Footer: token gate, IPFS toggle, privacy, submit
```

### Profile

**Header**:
```
- Cover: h-48/64 gradient/NFT
- Avatar: -mt-16 h-32 w-32 rounded-full border-4
- Name: text-2xl font-bold + verification
- Address: text-sm font-mono truncated + copy
- Stats: grid-cols-4 (followers, following, posts, holdings)
- Actions: Follow, Tip, Message (flex gap-2 mt-4)
```

**Tabs**: Posts, Replies, Media, NFTs, Tokens, Likes (border-b, py-4 px-6)

### Web3 Components

**Wallet Connection**:
```
- Disconnected: "Connect Wallet" button
- Connected: Dropdown with truncated address, balance, network badge
- Menu: switch wallet, view explorer, disconnect
```

**Token Display**:
```
- Glassmorphism card p-6 rounded-xl
- Icon + symbol + amount (text-2xl font-bold)
- USD value (text-sm)
- Actions: Tip, Stake, Swap
```

**NFT Avatar**:
- Gradient border, shimmer effect
- NFT badge (top-right)
- Hover: collection name + token ID

**Tipping Modal**:
```
- max-w-md centered
- Recipient: avatar + name
- Amount input with token dropdown
- Quick amounts: grid (0.1, 0.5, 1, 5)
- Balance + max button
- Confirm with gas estimate
```

**Transaction Toast**:
```
- Fixed bottom-right, slide-in
- Status: Pending (animated), Success (✓), Failed (X)
- Explorer link
- Auto-dismiss 5s (success), persistent (fail)
```

### Sidebar

**Trending**: rounded-xl p-4, hashtag + count + indicator, py-3 hover

**Suggested Users**: Avatar (h-10 w-10) + name + compact follow button

**Token Stats**: Glassmorphism, price + 24h change, sparkline, market cap/volume

### Messaging

**DM Interface**:
```
- Split: Conversations (w-80) + Chat (flex-1)
- Messages: left/right bubbles, rounded-lg max-w-md
- Input: Fixed bottom rounded-full, attachment button
- E2EE indicator: lock icon
```

### DAO/Governance

**Proposal Card**:
```
- border rounded-xl p-6
- Title (text-xl font-bold) + status badge
- Description with "Read more"
- Progress bars (Yes/No/Abstain)
- Vote buttons (if active)
- Countdown + quorum
```

**Community Card**: Cover h-32, name, members, token-gated badge, join button, stats

---

## Media & Visual Effects

**Images**:
- Covers: gradients/patterns default
- Posts: single (aspect-video) or grid (2-4)
- NFTs: shimmer borders + collection badges
- Avatars: gradient circles + first letter

**Icons**: Heroicons (h-5 w-5 default, h-6 w-6 prominent, h-4 w-4 inline)

**Glassmorphism**: backdrop-blur-lg on elevated cards (token balances, modals, FABs) + subtle border

---

## Animations

**Micro-interactions**:
- Like: scale + bounce
- Wallet connection: pulse during connect
- New posts: fade-in from top
- Toasts: slide-in

**Loading**:
- Skeleton screens with shimmer
- Transaction spinner with estimated time
- Progressive image blur-up

**Avoid**: Heavy transitions, excessive hover animations, distracting backgrounds

---

## Accessibility

- Touch targets: min-h-11
- Focus: Visible ring-2 offset-2
- ARIA labels on icon buttons
- Screen reader tx announcements
- High contrast support
- Keyboard shortcuts (n: new post, /: search)

---

## Blockchain UX Patterns

**Transaction Flow**:
1. User action → 2. Modal (details + gas) → 3. "Confirm in Wallet" (animated) → 4. Wallet popup → 5. Pending toast (explorer link) → 6. Success/fail notification

**Token-Gated Content**:
- Lock icon on gated posts
- Unlock modal: required tokens, balance, purchase option
- Preview with blur

**NFT Integration**:
- PFPs: verification badge
- Collectibles: mint button, ownership count, collection link
- Galleries: marketplace integration cues

---

## Key Patterns

**Container System**: min-h-screen flex (app), max-w-2xl mx-auto (feed), max-w-xl/4xl (modals), max-w-6xl (profile inner)

**Color & Hierarchy**: Use semantic color tokens, maintain WCAG AA contrast, progressive disclosure for complex data

**Performance**: Skeleton loading, optimistic UI updates, lazy load media, virtualize long feeds

This creates familiar social UX elevated with Web3 components. Three-column layout provides density while glassmorphism signals decentralization. Typography balances readability with technical precision. Every interaction respects blockchain constraints while maintaining fluid social media expectations.