---
title: "Panel  access"
date: 2010-05-19
forum: General Help
---

### Post by hikaribg on 2010-05-19
Hello!
I'm kinda new to this, so the problem will be probably with me. 

I have a Asus EEE PC, I installed a fresh copy of Ubuntu Netbook Remix, but it seems, that I don't have access to the panel or to say it simply i want to remove the "chat" icon and the user icon from the panel(7'' screen it's pain with more icons in the panel) but the option "Remove from panel" is gray and I can't click it, so are the "Move" and "Lock To Panel".
I was working with Ubuntu 10.04 before and I had access to it.

---

### Post by dino99 on 2010-05-19
try to grag & drop these icons into the trashbin, or right click on the panel/icon

---

### Post by hikaribg on 2010-05-19
Won't let me drag them.

---

### Post by hikaribg on 2010-06-03
This did the job:
```
sudo apt-get remove indicator-me indicator-messages
```

---

### Post by ubun_two on 2010-06-03
Lack of customizing panel capabilities in UNR 10.04 LTR has been discussed before.  No one likes it.

[http://ubuntuforums.org/showthread.php?t=1467257&highlight=netbook+remix+panel](http://ubuntuforums.org/showthread.php?t=1467257&highlight=netbook+remix+panel)

---

