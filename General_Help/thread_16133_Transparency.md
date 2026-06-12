---
title: "Transparency"
date: 2005-02-19
forum: General Help
---

### Post by Demon on 2005-02-19
I have seen it where some people have windows such as their terminals and stuff transparent. How can I do this?

---

### Post by DirtDawg on 2005-02-19
>   	I have seen it where some people have windows such as their terminals and stuff transparent. How can I do this? 

This is a good question. I would like to know too, please. The terminal window has a "transparent" setting, but it's not true transparency. When I turned it on, it simply recreated the desktop image. If anything was open, however, when I moved the terminal over an open window, the desktop still appeared "behind" the transparent terminal instead of the open window.  (sometimes the English Language seems so cumbersome when trying to describe such a simple concept)

    Thanks all

---

### Post by Demon on 2005-02-19
[QUOTE=DirtDawg]This is a good question. I would like to know too, please. The terminal window has a "transparent" setting, but it's not true transparency. When I turned it on, it simply recreated the desktop image. If anything was open, however, when I moved the terminal over an open window, the desktop still appeared "behind" the transparent terminal instead of the open window.  (sometimes the English Language seems so cumbersome when trying to describe such a simple concept)

    Thanks all[/QUOTE]

I didnt see that option... but from what you explained its like the Knoppix terminal with how the transparency acts which is fine for me.

---

### Post by GilGalad on 2005-02-19
The only way of getting "real" transparency and seeing the background window is using the Composite extension of the X server (Xorg) and utilities like xcompmgr and transset. This extension is however disabled by default since it is not stable yet and not all the applications support it. 

There are some posts in the forum about setting it to work. It is nice as eyecandy (also shadow windows & menus are possible) but as I said not stable enough (or at least not for me).

Cheers.

---

### Post by yatesco on 2005-02-23
I am using xcompmgr on hoary on my Presario 3228 AMD64 lappy with nvidia and it works a treat for me.

---

### Post by wulf on 2005-02-23
The trick is to make sure you've got nothing else behind your "transparent" terminals! ;)

It does look nice but in practice I find a solid background better for working on - otherwise the varying contrast makes the text hard to read. It's a neat trick but not useful enough for me to pursue it avidly.

Wulf

---

### Post by DirtDawg on 2005-02-23
[QUOTE=wulf]The trick is to make sure you've got nothing else behind your "transparent" terminals! ;) [/QUOTE]

lol. Exactly. :-)

---

