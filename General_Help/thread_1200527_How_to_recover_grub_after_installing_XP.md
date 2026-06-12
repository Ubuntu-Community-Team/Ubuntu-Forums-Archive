---
title: "How to recover grub after installing XP"
date: 2009-06-30
forum: General Help
---

### Post by bcbotha on 2009-06-30
I'm running Ubuntu 9.04 on my laptop and decided to dual boot with XP. I have XP installed but only to realize that i never made a copy of my grub menu list. how can I recover my ubuntu partition or recover grub?

thanks

---

### Post by JayRott on 2009-06-30
This one has happened to me a lot see this post :[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

it will walk you through it step by step.

---

### Post by Sef on 2009-06-30
Check out [Super GRUB Disk]("http://SuperGRUBDisk.org").

---

### Post by bcbotha on 2009-07-01
thanks grub is now working but i cant load XP for grub. ive listed XP in grub as:
```

title Windows XP
root (hd0,1)
chainloader +1
makeactive
boot
```

but this does not work. when i type sudo fdisk -l i find XP on /dev/sda1.
the error im getting is: Error 13: Invalid or unsupported executable format

Press any key to continue...

Anything i can do?

thanks

---

### Post by bcbotha on 2009-07-01
no worries i had the wrong partition. i logged on and changed the grub/menu.lst from (hd0,1) to (hd0,0) and it works. i can now boot to both now.

thanks anyway

---

