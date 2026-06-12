---
title: "Diacritics don't work correctly"
date: 2009-11-25
forum: General Help
---

### Post by vladu on 2009-11-25
I've attached a screenshot to illustrate the problem. At first I thought it was a problem with the Microsoft fonts, but it turned out to affect quite a lot of the fonts on my computer.

Any ideas on how to fix this?

---

### Post by StuartN on 2009-11-25
> **vladu said:**
> I've attached a screenshot to illustrate the problem.

The screenshot isn't enough, you need to explain what is wrong.

If you just mean the outline blocks replacing some characters, this means that the glyphs are not present, which you can only fix by creating (i.e. drawing) them.

Fontmatrix or gnome-specimen will show you what is contained within your font files.

---

### Post by vladu on 2009-11-25
The only difference between say t and &#539; should be the diacritic (the small coma in this case). Look for instance at the t or s in Arial bold. They look so different from the variants with diacritics that you might think they're written in different fonts. It is an annoyance to say the least.

Another interesting note is that it doesn't affect all letters with diacritics. The German letters ä ö ü for instance display just fine.

---

### Post by StuartN on 2009-11-26
> **vladu said:**
> They look so different from the variants with diacritics that you might think they're written in different fonts.

They may be - whoever drew the fonts might have copied another font and only altered the characters they cared for. The most practical solution is to note the fonts that work well for your needs.

Máirín Duffy regularly posts open fonts at [http://mairin.wordpress.com/2009/11/25/unpackaged-open-font-of-the-week-chemist/](http://mairin.wordpress.com/2009/11/25/unpackaged-open-font-of-the-week-chemist/)

---

### Post by vladu on 2009-11-26
Thanks for the link, it seems quite useful.

Fontmatrix could also be quite handy, but with me it has a bug that doesn't let me scroll down through the glyphs. 

Anyway, I did a little bit of research and found out that the default font family in Ubuntu is DejaVu. It turns out that the letters with diacritics that are wrong are in fact their DejaVu variants. Please note that I've been using those Microsoft fonts for many years and that OO.o documents using them look like they should under windows - the letters exist.

What else should I look for?

---

### Post by StuartN on 2009-11-26
> **vladu said:**
> Fontmatrix could also be quite handy, but with me it has a bug that doesn't let me scroll down through the glyphs.

I have version 0.4.2 from the repository and it works, but you could also try gnome-specimen.

> **vladu said:**
> Anyway, I did a little bit of research and found out that the default font family in Ubuntu is DejaVu.

I see exactly what you mean now. I have looked at (Ubuntu) Arial Bold in Specimen and at some characters in OpenOffice (version 2.4.1 installed with Ubuntu 8.10) and, for instance, t and &#355; are definitely the same outline and not substituted as in your image.

I assume that a default is substituted only when the correct glyph is absent, but there must be another explanation if you and I are using the same font files (/usr/fonts/truetype/msttcorefonts/Arial_Bold.ttf, Monotype:Arial Bold:Version 2.82 (Microsoft)).

Perhaps posting the original text of your image sample would help, and I will look at the other font and character combinations in my OpenOffice and in Specimen.

---

