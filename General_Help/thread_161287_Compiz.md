---
title: "Compiz??"
date: 2006-04-16
forum: General Help
---

### Post by thunderduck3141 on 2006-04-16
hi everybody
i can't seem to find "compiz" in any of the repositories
i have everything enabled (manually by editing sources.list)
please help
thanks
anf Happy Easter
hooray for Christianity :)

---

### Post by sYs^ on 2006-04-16
Add these: 
```

deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```
then
```
sudo apt-get update
sudo apt-get install compiz-vanilla compiz-vanilla-gnome
```

---

### Post by Qrk on 2006-04-16
[QUOTE=sYs^]Add these: 
```

deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```
then
```
sudo apt-get update
sudo apt-get install compiz-vanilla compiz-vanilla-gnome
```[/QUOTE]

Is it that easy on Breezy? I haven't ever tried compiz on breezy, but I thought it required this guide:

[http://www.ubuntuforums.org/showthread.php?t=133772](http://www.ubuntuforums.org/showthread.php?t=133772)

---

### Post by sYs^ on 2006-04-16
I think he was looking for the package.
But of course if he wants to use compiz he will have to follow a guide or something like that :>

---

