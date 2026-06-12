---
title: "How to rename and delete lines in boot list (GRUB 2), Lucid Lynx"
date: 2010-08-28
forum: General Help
---

### Post by VirtualWaver on 2010-08-28
Hi all,

It is a long time since I am searching for the solution and still I can't find it. 

My question is simple: how to change (rename, delete) lines from boot list in grub 2, Ubuntu 10.04? For example, when I boot my pc, I have a boot list with options "Ubuntu 10.04", "memtest" and "Windows 7". I want to delete "memtest" line, as I don't need it, and rename "Windows 7" line to, for example, "Windows 117". How can I do that? Where I should look and edit? 

In old grub it was enough to edit /boot/grub/menu.lst, but in Ubuntu 10.04 there is no such file and other grub2-related files (like grub.cfg) do not contain this info to rename or delete lines. So, I can't figure out what to do.
 
I will highly appreciate your help. Thanks in advance.

---

### Post by Mark Phelps on 2010-08-29
It is a LOT harder to do this using GRUB2 because you have to (1) disable the default config files, and (2) hand-code your own custom config files.

Details on doing this can be found in the linked post below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by Quackers on 2010-08-29
The tips in this thread did it for me :-)

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub](http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub)

---

### Post by VirtualWaver on 2010-09-03
> **Quackers said:**
> The tips in this thread did it for me :-)

[http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub](http://ubuntuforums.org/showthread.php?t=1541785&highlight=delete+entries+grub)

Thanks a lot, Quackers! This was exactly what i need. The link helped me to completely solve my problem!

Thank you too, Mark Phelps, your link contains a lot of useful information!

---

