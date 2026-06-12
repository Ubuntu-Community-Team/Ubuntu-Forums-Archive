---
title: "WIndows - UNDER Ubuntu?"
date: 2010-01-27
forum: General Help
---

### Post by LGFUAD on 2010-01-27
Is there any way to install WINDOWS 7 under Ubuntu?  I tried just booting off of the setup disk, and it brings me to a black screen where if I hit any keys the loud speaker releases a god awful sound.   I also tried just running the setup, but Wine only runs certain .exe files for some reason..  I even tried re-compiling all the files from the original .ISO into another .ISO and making a USB startup of it, failed.  I made a serperate partition for it with GpartED already too.  So, all in all, is there a way to install WINDOWS 7 under Ubuntu.  I'm using Ubuntu 9.10, in case anyone was wondering.  Help would be appreciated.

---

### Post by t4thfavor on 2010-01-27
In a VM, yes. But installing win7 like when you put the XP disk into your win98 PC, No. Windows does not support that, and likely never will.

---

### Post by Megafag on 2010-01-27
> **LGFUAD said:**
> Is there any way to install WINDOWS 7 under Ubuntu?  I tried just booting off of the setup disk, and it brings me to a black screen where if I hit any keys the loud speaker releases a god awful sound.   I also tried just running the setup, but Wine only runs certain .exe files for some reason..  I even tried re-compiling all the files from the original .ISO into another .ISO and making a USB startup of it, failed.  I made a serperate partition for it with GpartED already too.  So, all in all, is there a way to install WINDOWS 7 under Ubuntu.  I'm using Ubuntu 9.10, in case anyone was wondering.  Help would be appreciated.

By UNDER Ubuntu do you mean running Ubuntu and Windows 7 at the same time?

EDIT: ^yes using a VM would be the way to go.

I suggest Virtualbox

---

### Post by running_rabbit07 on 2010-01-27
[Sun VirtualBox.]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by Megafag on 2010-01-27
> **running_rabbit07 said:**
> [Sun VirtualBox.]("http://www.virtualbox.org/wiki/Linux_Downloads")

or

```
sudo apt-get install virtualbox
```

---

### Post by LGFUAD on 2010-01-27
I didn't even think of virtualbox...  Stupid me, thanks everyone.

---

### Post by Ordes on 2010-01-27
if using virtualbox, than u wont need an extra partition, as the whole virtual system will be just a folder/file.

u only need an extra partition if you want to dual boot, win7 / ubu.

depending on what u wanna do with win7, like playing games, than Vbox wont do it and u need dual boot.

If u just need it to run some windows only applications, than Vbox should do it. e.g adobe products....

---

