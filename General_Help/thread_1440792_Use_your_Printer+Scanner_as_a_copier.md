---
title: "Use your Printer+Scanner as a copier"
date: 2010-03-27
forum: General Help
---

### Post by superyounan1 on 2010-03-27
My dad loves using our multifunction inkjet printer for making copies, it costs a lot to replace that ink. We do have a laser printer, but getting him to learn how to use scanning software Xsane was just confusing him way too much.

So, I came up with this shell script to make it easy. I'll make an icon on his desktop and tell him to double click it when he needs a copy.

```
scanimage --resolution 200 -x 215 -y 279 --format=tiff > image.tiff && convert -quality 100 image.tiff image.ps && lp -o fitplot -o media=letter image.ps && rm image.tiff image.ps

```

Thought I'd share it in case it might be useful to you.

I'll probably add a prompt for number of copies using Zenity. If you guys have any ideas on how to improve the output quality, please chime in.

---

