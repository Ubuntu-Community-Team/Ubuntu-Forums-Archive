---
title: "Show dropbox info in conky?"
date: 2010-08-30
forum: General Help
---

### Post by Ultra_Man on 2010-08-30
I'm think I remember being able to show info about dropbox like space used, space free, status using conky. Does anyone know how I can do that?

---

### Post by aleblanc on 2010-12-03
This is what I use:

  ${offset 240}${color slate grey}Dropbox status: ${color }${execi 6 dropbox status}

Adjust the offset and color to your tastes (and maybe add a ${font ...} setting to change the font size/style), and place that line in the "TEXT" section of your .conkyrc file

---

### Post by movistress on 2012-02-24
in my .conkyrc

{exec dropbox status | sed -n 1p}

works for me, but does high cpu usage when dropbox daemon is not started.

peace.

---

