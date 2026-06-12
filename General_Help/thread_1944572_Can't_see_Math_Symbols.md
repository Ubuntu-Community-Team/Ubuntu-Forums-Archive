---
title: "Can't see Math Symbols"
date: 2012-03-21
forum: General Help
---

### Post by prunes4u on 2012-03-21
Hi,

I'm running Bodhi Linux and I see Rectangles in place of Integrals, exponents, and Summation symbols in my .doc files

I've tried Abiword, OpenOffice, and LibreOffice but none of them show the symbols.

What do I do?

PS: I'm very new to Linux so please explain

---

### Post by Hagar Delest on 2012-03-21
Welcome to the vendor lock-in policy!

That's why proprietary format should be avoided. Basically, if you need to work in .doc with complex features (like formulas), then better stick to MS Word.

The problem may be linked to a font missing. Have you tried to install the msttcorefonts package? Else, can you upload a sample file so that we try?

---

### Post by prunes4u on 2012-03-21
What kind of sample file do you need? The file I'm trying to open?

Also, when I tried to open it in Google Docs, I still had the issue.

I looked for the corefonts but I couldn't find it

---

### Post by SeijiSensei on 2012-03-21
As I recall, Microsoft has a Symbol font that includes most of these characters.  If you can track down the symbol.ttf file on your Windows machine, copy it over to Linux, then install it with your font manager.  See if that helps.

There are also the math[abc]___.ttf files.  You might need those as well, though from looking at them, they contain the more arcane characters like double-headed inference arrows and the like.

---

