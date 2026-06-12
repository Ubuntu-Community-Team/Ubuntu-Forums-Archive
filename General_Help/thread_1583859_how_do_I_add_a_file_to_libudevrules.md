---
title: "how do I add a file to /lib/udev/rules"
date: 2010-09-28
forum: General Help
---

### Post by Grafens on 2010-09-28
Please help I tried searching for an explanation on howto add a file but couldn't find anything.

---

### Post by lrgmmc on 2010-09-28
Just curious, what are you trying to do?

---

### Post by Grafens on 2010-09-28
I am trying to configure a drawing tablet.
[https://help.ubuntu.com/community/AiptekTablet#Ubuntu%2010.04%20%28Lucid%20Lynx%29]("https://help.ubuntu.com/community/AiptekTablet#Ubuntu%2010.04%20%28Lucid%20Lynx%29")

---

### Post by lrgmmc on 2010-09-28
this looks like it maybe of some use. [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by Grafens on 2010-09-28
Thanks for the link, I will try it out when I have enough time.

---

### Post by Favux on 2010-09-28
Hi Grafens,

Use:
```
gksudo gedit /lib/udev/rules.d/69-xserver-xorg-input-aiptek.rules
```
And copy and paste the contents into the empty file.  Save, Close, and reboot.

---

