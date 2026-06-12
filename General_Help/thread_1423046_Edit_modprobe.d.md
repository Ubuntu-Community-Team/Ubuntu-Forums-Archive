---
title: "Edit modprobe.d"
date: 2010-03-06
forum: General Help
---

### Post by Ric321 on 2010-03-06
Please help complete [COLOR=#CC0000] [/COLOR][***beginner***]("http://www.google.co.uk/search?hl=en&client=firefox-a&hs=6mX&rls=com.ubuntu:en-US:unofficial&ei=-DeSS9-lNob60wTYtcDqDA&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBIQBSgA&q=beginner&spell=1") .
      I am trying to edit alsa-base in /etc/modprobe.d and I get   p, li { white-space: pre-wrap; }  "The document could not be saved, as it was not possible to write to /etc/modprobe.d/alsa-base.
 
 Check that you have write access to this file or that enough disk space is available."
       This is probably a root issue but I can not find any way to change to root 

    Any help including select this then that would be fantastic.


                 cheers    Ric :)

---

### Post by nothingspecial on 2010-03-06
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Then try again

---

### Post by Ric321 on 2010-03-06
Brill thanks very much it works......


            Ric

---

