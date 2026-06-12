---
title: "Bash sees command but won't execute"
date: 2011-03-02
forum: General Help
---

### Post by redcodefinal on 2011-03-02
Ok,
Kind of a weird issue I've been having, I was trying to run the boot installer for [Katana ]("http://www.hackfromacave.com/katana.html")(bootinst.sh) but I keep running into the same problem. See it for yourself

```

ian@ian-Inspiron-600m:/media/KATANA/boot$ ls
bootinst.bat  isolinux      menus         test.sh       wallpaper_high.png
bootinst.sh   make_iso.bat  pxelinux.cfg  ubcd4win      wallpaper.png
chain.c32     make_iso.sh   reboot.c32    uninstall
econfig.c32   menu.c32      syslinux      vesamenu.c32
ian@ian-Inspiron-600m:/media/KATANA/boot$ ./bootinst.sh
bash: ./bootinst.sh: Permission denied
ian@ian-Inspiron-600m:/media/KATANA/boot$ sudo !!
sudo ./bootinst.sh
sudo: ./bootinst.sh: command not found
ian@ian-Inspiron-600m:/media/KATANA/boot$

```

It sees that bootinst.sh is valid and produces a "permission denied" error. But, when I try to sudo the previous command it refuses to let me. Either way I need some help as I have run into this problem before.
Any help appreciated!

-Ian

---

### Post by hawkmage on 2011-03-02
If you do an "ls -l" does the file have execute permission?  If no do a chmod u+x bootinst.sh.

---

### Post by mwray on 2011-03-03
you could try
sudo sh ./bootinst.sh
if bootinst.sh doesnt start with a #! line or if it's path to the shell is incorrect, ./bootinst.sh won't run.

e.g.

#!/usr/bin/bash
Often time these scripts on cd's can be run by typeing the name of the correct shell and passing the script  as a parameter.

---

### Post by redcodefinal on 2011-03-03
> **hawkmage said:**
> If you do an "ls -l" does the file have execute permission?  If no do a chmod u+x bootinst.sh.
After trying that it won't change the permissions! Even with sudo....

I tried both +x and 777

---

### Post by redcodefinal on 2011-03-03
> **mwray said:**
> you could try
sudo sh ./bootinst.sh
if bootinst.sh doesnt start with a #! line or if it's path to the shell is incorrect, ./bootinst.sh won't run.

e.g.

#!/usr/bin/bash
Often time these scripts on cd's can be run by typeing the name of the correct shell and passing the script  as a parameter.
This works, although now I am hitting a large number of errors.... Oh well Thanx anyways

---

### Post by breadin on 2013-01-12
I fixed this issue on another forum, the problem is you can't change file permissions on FAT formatted drives, when they're mounted, but if you mount the drive as sudo you will have the authority to run the script without errors.

Here's a link to the forum and the topic. My solution should be at the bottom.
[http://forums.hak5.org/index.php?/topic/20854-problems-with-installing-katana/](http://forums.hak5.org/index.php?/topic/20854-problems-with-installing-katana/)

---

