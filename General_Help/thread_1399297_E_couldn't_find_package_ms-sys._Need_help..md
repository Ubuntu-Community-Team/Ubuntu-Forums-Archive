---
title: "E: couldn't find package ms-sys. Need help."
date: 2010-02-05
forum: General Help
---

### Post by blackearth99 on 2010-02-05
Hi, so rite now I'm trying to fix my mbr for windows through ubuntu because I don't have the actual windows xp recovery disk and Grub will not load windows xp.

I entered the command "sudo apt-get update"  and it loads all the packages but when i am supposed to type in "sudo apt-get install ms-sys" i get the message "E: couldn't find package ms-sys."

How do I fix this?

---

### Post by kellemes on 2010-02-05
Not in the repositories, you have to [get it here]("http://ms-sys.sourceforge.net/#Download").
You can also use [Super Grub Disk]("http://www.supergrubdisk.org/") for 'fixing' the MBR. Download, burn and boot with it..

Edit: And if you happen to find a Windows-installdisk.. this is how to fix MBR using the disk.
[http://pcsupport.about.com/od/fixtheproblem/ss/rconsole.htm]("http://pcsupport.about.com/od/fixtheproblem/ss/rconsole.htm")

---

### Post by blackearth99 on 2010-02-05
> **kellemes said:**
> Not in the repositories, you have to [get it here]("http://ms-sys.sourceforge.net/#Download").
You can also use [Super Grub Disk]("http://www.supergrubdisk.org/") for 'fixing' the MBR. Download, burn and boot with it..

Thx! ill try it out and hopefully it works.

---

### Post by drs305 on 2010-02-05
ms-sys has been replaced by the package "mbr".

You can also download the "lilo" package (but don't actually run it to replace grub). Afterward, you can use this to restore the MBR on sda if that is where Windows resides: 
```
lilo -M /dev/sda mbr
```

---

### Post by blackearth99 on 2010-02-05
> **kellemes said:**
> Not in the repositories, you have to [get it here]("http://ms-sys.sourceforge.net/#Download").
You can also use [Super Grub Disk]("http://www.supergrubdisk.org/") for 'fixing' the MBR. Download, burn and boot with it..

Edit: And if you happen to find a Windows-installdisk.. this is how to fix MBR using the disk.
[http://pcsupport.about.com/od/fixtheproblem/ss/rconsole.htm]("http://pcsupport.about.com/od/fixtheproblem/ss/rconsole.htm")


OMG Thank you so much! windows booted up and everything.

+1000 internets to you.

---

