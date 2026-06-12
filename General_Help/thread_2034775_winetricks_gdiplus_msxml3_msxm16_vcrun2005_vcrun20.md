---
title: "winetricks gdiplus msxml3 msxm16 vcrun2005 vcrun20008 vrun2010 atmlib"
date: 2012-07-29
forum: General Help
---

### Post by shaquille110 on 2012-07-29
I'm trying to install the following

[LIST]
[*]winetricks
[*]gdiplus
[*]msxml3
[*]msxm16
[*]vcrun2005
[*]vcrun20008
[*]vrun2010
[*]atmlib
[/LIST]
I've tried using the SH command but it says the files couldn't be located for all of them. I'm trying to install Photoshop CS6 however i'm encountering issues and i have seen in a couple of forum posts that install the above should eliminate the error messages


Thanks
Shaq

---

### Post by shaquille110 on 2012-07-29
BTW, i'm using Ubuntu 12.04 with the latest updates!

---

### Post by raja.genupula on 2012-07-29
use synaptic package manger to install them .

---

### Post by shaquille110 on 2012-07-29
> **raja.genupula said:**
> use synaptic package manger to install them .

I tried that just than i can't find what i need in it, they don't seem to exist in the synaptic package manager.

---

### Post by raja.genupula on 2012-07-29
do you have those sources files with you ? If not get them then you can install them manually .

---

### Post by shaquille110 on 2012-07-31
Issue has been resloved. Instead of using SH i used Bash and that resoved the issue.

For example don't use:

```
sh winetricks gdiplus msxml3 msxm16 vcrun2005 vcrun20008 vrun2010 atmlib
```

Instead use

> bash winetricks gdiplus msxml3 msxm16 vcrun2005 vcrun20008 vrun2010 atmlib

---

