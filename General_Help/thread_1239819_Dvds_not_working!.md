---
title: "Dvds not working!"
date: 2009-08-13
forum: General Help
---

### Post by Codix121 on 2009-08-13
I've looked EVERYWHERE but all i get is issues on ISOs...
which is not my concern,
I'm talking about actual DVDs (store bought)
Don't work on my Jaunty 9.04 why?
They don't autostart,
and movie player won't play them,
neither will xine?

can anyone point me to a tutorial that could fix this?
Thanks :)

---

### Post by mthalis on 2009-08-13
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by rhcm123 on 2009-08-13
> **Codix121 said:**
> 
can anyone point me to a tutorial that could fix this?
Thanks :)

do this: 
```
sudo apt-get install ubuntu-restricted-extras vlc
```
The movie player (aka totem) dosen't support the encryption built-into hollywood DVD's (without some pain-in-the-neck workarounds) , and you need a program that does right out of the box. 

install those two pacakges, pop in the DVD, and it should open with VLC automatically. else, just right click the icon on your desktop and hit "open with vlc media player".

---

### Post by Codix121 on 2009-08-13
thanks got it working!
Uhm anyone know anyway that I can make the DVD's autostart?
and what are some good recommended DVD players?
I tried XINE but I dont like the interface..

---

### Post by rhcm123 on 2009-08-14
> **Codix121 said:**
> thanks got it working!
Uhm anyone know anyway that I can make the DVD's autostart?
and what are some good recommended DVD players?
I tried XINE but I dont like the interface..

did you do my fix or mthalis's. If you did his, try mine with vlc, i like it alot (looks great in fullscreen).

---

### Post by Codix121 on 2009-08-14
I did mthalis's first,
then tried yours but I already have VLC,
and yeah I tried it on VLC it did look good,
and worked better than Movie Player.

Any idea on how to autostart DVD's tho?

---

### Post by rhcm123 on 2009-08-14
> **Codix121 said:**
> I did mthalis's first,
then tried yours but I already have VLC,
and yeah I tried it on VLC it did look good,
and worked better than Movie Player.

Any idea on how to autostart DVD's tho?

err... i just slam them in and they play. I think i selected "always use vlc for this kind of file" but i forget.

---

### Post by Codix121 on 2009-08-14
damn not working for me,
guess I'll have to settle with right clicking > open with 
XD well thanks for the help :)

---

### Post by mc4man on 2009-08-14
multiple ways to set

insert dvd and hold down shift button

in terminal and then in system -> preferences enable file management
```
alacarte 
```
or in terminal
```
nautilus-file-management-properties
```
or nautilus -> edit -> preferences -> media

(( file management has other useful area's

---

