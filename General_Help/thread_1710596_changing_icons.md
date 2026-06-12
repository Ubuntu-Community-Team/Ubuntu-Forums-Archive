---
title: "changing icons"
date: 2011-03-20
forum: General Help
---

### Post by slowwound on 2011-03-20
hi

how do i change the icon of HTML files, and the one for TXT files ?

i tried assogiate, but it doesn't work.

how can i do that, then ?

---

### Post by Krytarik on 2011-03-20
See this guide:
[http://swik.net/Ubuntu/Only+Ubuntu/How+To+Change+File-Type+%28mimetype%29+Icons+in+Ubuntu/chcrf](http://swik.net/Ubuntu/Only+Ubuntu/How+To+Change+File-Type+%28mimetype%29+Icons+in+Ubuntu/chcrf)

---

### Post by slowwound on 2011-03-21
well, i tried that, but my ~/.icons folder is empty, so i don't know what to do then.
i guess, that's necessary to be able to change the icons like in that tutorial, right ?

---

### Post by Krytarik on 2011-03-21
> **slowwound said:**
> well, i tried that, but my ~/.icons folder is empty, so i don't know what to do then.
i guess, that's necessary to be able to change the icons like in that tutorial, right ?
Because they are installed system-wide in "/usr/share/icons". Note that because of that you need to gain root access for the different steps, with "gksudo" or "sudo" respectively.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by slowwound on 2011-03-23
and how do i know, which icon is for the file type i want to change ?

let's say, i want to change the icons of txt (but keep the plain text icons), and the icons of htm/html.

then i replace them in the icons folder of the theme i'm using, right ?
then restart and that's it ?

---

### Post by Krytarik on 2011-03-23
Although I don't know where you see a difference between "txt" and "plain text", but yeah, it's like that. Of course you have to take into account what structure the icon theme has, and like the guide describes, you may have to replace a mimetype's icon in various sizes, in the according directories. And you may have also to create a new cache file, if there is one. With some icon themes the cache command creates an unreasonable big cache file, you can spare it then, and with some themes it doesn't work at all.

---

