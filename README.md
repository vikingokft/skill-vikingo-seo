# Vikingo SEO skill

Claude Code skill elkészült weboldalak **SEO + GEO + AEO alapozásához**.

Nem audit-riportot ír, hanem **elvégzi** a belépőszintű beállításokat a kódban, gépi ellenőrzéssel bizonyítja, hogy kész, és javaslatokat ad arról, ami döntést igényel.

## Mit csinál

- **Title + meta description** — egyedi, jó hosszúságú, minden oldalra (ami már jó, ahhoz nem nyúl)
- **Open Graph + Twitter card** — hogy megosztáskor szépen jelenjen meg az oldal
- **Favicon** — ha nincs, készít egyszerűt a márka színeivel
- **Canonical tagek**
- **Schema.org JSON-LD** — a vállalkozás típusához illő entitás (LocalBusiness altípusok, kész sablonokból)
- **Címsor-hierarchia + alt szövegek** javítása
- **Lazy loading** a hajtás alatti képekre
- **sitemap.xml + robots.txt**
- A végén **gépi ellenőrzés** (`scripts/ellenorzes.py`) — addig nincs kész, amíg nem zöld

## Amit tudatosan NEM csinál

- Nem ír át látható szöveget engedély nélkül
- Semmi kulcsszó-halmozás vagy rejtett trükk
- Nem ígér helyezést — a belépőszint azt biztosítja, hogy a keresők és az AI-motorok pontosan értsék az oldalt; a helyezés a tartalmon és az időn múlik

## Telepítés

```bash
git clone https://github.com/vikingokft/Vikingo-SEO-skill.git ~/.claude/skills/vikingo-seo-skill
```

Ennyi — a következő Claude Code sessionben már elérhető. (Projekt-szintű telepítéshez a projekt `.claude/skills/` mappájába másold.)

## Használat

Claude Code-ban:

```
/vikingo-seo-skill
```

vagy csak kérd természetes nyelven: „optimalizáld az oldalt keresőre", „csináld meg a SEO alapokat".

A skill egyetlen kérdéskört tesz fel (végleges domain + hiányzó vállalkozás-adatok), elvégzi a beállításokat, majd a gépi ellenőrzés eredményével és javaslatlistával zár.

## Az ellenőrző szkript önállóan is futtatható

```bash
python3 scripts/ellenorzes.py [oldalak mappája] --domain https://pelda.hu
```

Oldalanként méri: title/description megléte, hossza és egyedisége, og-tagek, canonical, favicon, lang, viewport, H1-darabszám, alt-lefedettség, JSON-LD érvényesség, sitemap + robots.txt, GSC-hitelesítési nyomok. Kilépési kód: 0 = zöld, 1 = van hiba — CI-ba is beköthető.

## Felépítés

```
vikingo-seo-skill/
├── SKILL.md                    ← a folyamat
├── scripts/
│   └── ellenorzes.py           ← gépi ellenőrzés (csak Python stdlib)
└── references/
    └── schema-sablonok.md      ← JSON-LD minták vállalkozás-típusonként
```

## Frissesség-védelem

A skill fejléce tartalmazza az utolsó frissítés dátumát. Ha a futáskor ennél 3 hónapnál régebbi, a skill webes kereséssel ellenőrzi, változtak-e az alapszintű best practice-ek, és felajánlja saját maga frissítését.

---

Készítette: Vikingo Kft. · Claude Code skill
