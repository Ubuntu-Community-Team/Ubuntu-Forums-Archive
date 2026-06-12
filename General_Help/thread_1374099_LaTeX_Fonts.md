---
title: "LaTeX Fonts"
date: 2010-01-06
forum: General Help
---

### Post by JMJ_coder on 2010-01-06
Hello,

I am running Ubuntu 9.10 Karmic. I installed the texlive package and have:

TeX -> TeX 3.141592 (Web2C 7.5.6)
LaTeX -> pdfTeX using libpoppler 3.141592-1.40.3-2.2 (Web2C 7.5.6)

I am trying to get different fonts working, but have struck out thus far. I have the gnu-freefont installed system wide (which is a ttf font), but it doesn't seem to recognize when I use:

```
{\fontfamily{freeserif}\selectfont ...}
```

How exactly do I (1) figure out which fonts latex has available to it and what they are called and (2) how to make other system-wide installed fonts available (particularly ttf fonts)?

In particular, I am trying to insert some unicode characters (U+211F and U+2123). However, uni-33.def doesn't have them listed. I know that gnu-freefont has them. I tried after attempting to switch to the freeserif font to issue ```
\unichar{"2123}
``` but, it still complains about not finding that unicode character in uni-33.def.

I also tried to switch to a special ttf font (installed system-wide) I have that has those characters mapped to V and R, but still no go (I don't even know what latex would call that font).

Note, I have put in my preamble ```
\usepackage{ucs}
\usepackage[utf8x]{inputenc}
```


Any thoughts?

---

### Post by JMJ_coder on 2010-01-06
I found a solution to this using XeTeX and the fontspec package.

---

