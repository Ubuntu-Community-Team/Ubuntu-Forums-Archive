---
title: "Cannot login (blank screen then back to login screen)"
date: 2012-03-03
forum: General Help
---

### Post by yonyz on 2012-03-03
Hi,

I've installed Ubuntu 11.10 yesterday using the Windows installer. Occasionally it would crash and throw me back into the login screen, but now I cannot log back into my account. The guest account is accessible though. Also, I am able to access my account through the terminal, but not through the GUI. I tried using Gnome, Ubuntu 2D and the rest, but none of them work. I also removed the .Xauthority file and researched and tried other methods for hours, but none of them seem to work for me.

I also tried a command that involves ICEauthority.

What else can I try?

---

### Post by raja.genupula on 2012-03-03
[http://ubuntuforums.org/showthread.php?t=1849798&page=2](http://ubuntuforums.org/showthread.php?t=1849798&page=2)

have you tried that ?

---

### Post by yonyz on 2012-03-03
Yes, the keyboard thingy is true. The installation was done using Hebrew and when I boot it's set to English. How can I change that?

---

### Post by raja.genupula on 2012-03-03
open keyboard layout in system settings  (i think now you have to move from failsafeX mode from recovery mode of grub )

---

### Post by yonyz on 2012-03-03
I don't quite understand. You're saying I should change system layout settings after booting into recovery mode?

---

### Post by raja.genupula on 2012-03-03
> **yonyz said:**
> Yes, the keyboard thingy is true. The installation was done using Hebrew and when I boot it's set to English. How can I change that?

you said like this and then you said you're unable to login . so i suggested you that way.

---

### Post by yonyz on 2012-03-04
I entered recovery mode, but it's text-only, no GUI. How do I change default keyboard layout of my account from over there?

---

### Post by raja.genupula on 2012-03-04
[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

look for this **Keyboard configuration - console**

---

### Post by yonyz on 2012-03-04
OK, I fixed the problem, and it had nothing to do with system locale/keyboard layout. I had to remove some OSX Lion theme files I copied into the usr/share/theme folder. Now I am able to login my user. Thanks for the suggestions!

---

### Post by raja.genupula on 2012-03-04
thats good news , please mark the thread as solved from thread tools .

---

