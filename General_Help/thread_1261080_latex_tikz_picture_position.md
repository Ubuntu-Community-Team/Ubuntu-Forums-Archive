---
title: "latex tikz picture position"
date: 2009-09-08
forum: General Help
---

### Post by krishna1650 on 2009-09-08
hi all, i made a image using tikzpicture. now i want to shift whole picture in x direction by value 5. is there any direct way, where i have to just set the value 5 in one place and get the total image shifted in x direction.

is it possible to set starting point of a tikzpicture ? i mean can we make a tikzpicture relative in position.

please help me.
thanks.

---

### Post by Stefan_K on 2009-09-10
Hi,

you could use the textpos package for absolute or relative positioning of a tikz picture. Or use the current page node, like in this example: [Fancy chapter headings with TikZ]("http://texblog.net/latex-archive/layout/fancy-chapter-tikz/"). There you will find code positioning relatively to the page corners and using shifting.

Stefan


--
[TeXblog]("http://texblog.net")

---

