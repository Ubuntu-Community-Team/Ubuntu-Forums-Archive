---
title: "Display problems"
date: 2006-05-31
forum: General Help
---

### Post by Arildo on 2006-05-31
HI!

I've just installed Ubuntu for my first time, and I've just been configuring and installing som packages. As far as I know I haven't done anything with my display settings, but still this strange problem occured after a reboot:
[http://armosolution.net/feil/Skjermdump-2.jpg](http://armosolution.net/feil/Skjermdump-2.jpg)

It's very hard to read any text, but it also affects graphics

I'm running on a Toshiba laptop with a NVIDIA graphics card

---

### Post by deja2004 on 2006-05-31
It looks as if you switched your default language to Swedish. I'm asssuming you're running gnome, so follow these steps:

Click on "System" -> Then "Administration" (or second menu down) -> Then "Language Support".

From there, you can reset your default language back to English.

---

### Post by hollywoodb on 2006-05-31
that link gives me a '403 Forbidden' error

---

### Post by Arildo on 2006-05-31
The problem isn't the language. Actually, it's Norwegian, but since I'm Norwegian that isn't a problem. The problem is how the text (and the graphics you see up to the left) is displayed. This is not due to a resize or something of the image.

EDIT: Obiously, the pictures look normal for everybody else, so I'll try to describe the problem. It looks like I'm in heavy loss of Anti-aliazing or something. It's very easy to see on all font types,  in stead of solid lines, each letter is consisting of grey dots. I can also see this on graphics, it looks like it's missing antialiasing (even where this normally wouldn't been required)

---

### Post by Arildo on 2006-06-02
I've finally fixed the problems. Since everything worked fine in the beginning, until this problem suddenly occured, I didn't think it was related to the display drivers. But since I now had tried everything else I could think of, I thought that it maybe was worth a try to (re)install the display drivers, and it really was! Now, everything is perfect:-D

---

