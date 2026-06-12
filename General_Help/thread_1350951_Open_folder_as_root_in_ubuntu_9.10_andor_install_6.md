---
title: "Open folder as root in ubuntu 9.10 and/or install 64-bit flash."
date: 2009-12-09
forum: General Help
---

### Post by bix15 on 2009-12-09
I'm pretty darn new to ubuntu, and just linux in general.
I'm trying to install flash on my 64-bit ubuntu as a firefox plugin.
sooooo..... I need to open the following folder, /filesystem/usr/lib/mozilla 
as root so that I can drag and drop my libflashplayer.so file into the mozilla plugins folder. I've tried this normally and I now know that I need to open it as root. 
How do I do this??

P.S. If you guys have any other way for me to install flash on my system I will gladly take answers! I just want to watch my youtube videos and chat on facebook and I've noticed that I can watch youtube videos and click play/pause. BUT when I want to chat on facebook through the IM client, when I try to click in the textbox to type somthing, I can't.

Thank you for your help!!

---

### Post by b0b138 on 2009-12-09
gksudo nautilus  will open nautilus with root privledges.  or...  /home/username/.mozilla/plugins  (create plugins folder if needed)


oh and a new 64 prerelease just came out [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by Clancy_s on 2009-12-09
> **bix15 said:**
> I'm pretty darn new to ubuntu, and just linux in general.
I'm trying to install flash on my 64-bit ubuntu as a firefox plugin.
sooooo..... I need to open the following folder, /filesystem/usr/lib/mozilla 
as root so that I can drag and drop my libflashplayer.so file into the mozilla plugins folder. I've tried this normally and I now know that I need to open it as root. 
How do I do this??

Open a terminal, go 

```
sudo nautilus
```

enter your password.  A root version of nautilus will open.

> **bix15 said:**
> P.S. If you guys have any other way for me to install flash on my system I will gladly take answers! I just want to watch my youtube videos and chat on facebook and I've noticed that I can watch youtube videos and click play/pause. BUT when I want to chat on facebook through the IM client, when I try to click in the textbox to type somthing, I can't.

Thank you for your help!!

I use this:

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

