---
title: "Flatten unity panel"
date: 2011-10-23
forum: General Help
---

### Post by Dark Slipstream on 2011-10-23
Does anyone know how to flatten the unity panel? Activate the dash, that's what I am looking for. (See below)

[img]http://i.stack.imgur.com/5u8Xx.jpg[/img]

---

### Post by Dark Slipstream on 2011-11-18
I flattened the unity panel by editing the following file (replace *Ambiance* with the theme you are using):

```
/usr/share/themes/*Ambiance*/gtk-3.0/apps/unity.css
```

Replace

```
background-image: -gtk-gradient (linear, left top, left bottom, from (shade (@dark_bg_color, 1.5)), to (shade (@dark_bg_color, 1.04)));
```

with

```
background-image: -gtk-gradient (linear, left top, left bottom, from (#141718), to (#141718));
```

---

