---
title: "Boot to Windows is gone after update"
date: 2006-02-19
forum: General Help
---

### Post by kseise on 2006-02-19
I have posted this in two locations
[http://www.ubuntuforums.org/showthread.php?t=132604]("http://www.ubuntuforums.org/showthread.php?t=132604")
and here
[http://www.ubuntuforums.org/showthread.php?t=132397]("http://www.ubuntuforums.org/showthread.php?t=132397")

I don't know if they were in the right area.  After the last kernel update, the Grub entry to my windows xp disappeared.  Now, when I add in the entries to windows in the menu.lst, Grub loads stage one and then hangs on loading stage 2.  

My drives are as follows
HD0,0 Windows XP with NTFS
HD1,0 Linux ext3
HD1,1 Swap

I can't even get my XP installation CD to boot.  It works fine on my other box.  How Can I get back into windows?

---

### Post by ahlich on 2006-02-19
So your windows feels embarrassed by how much coffee you are brewing these days and decided to commit suicide?

Did you tryed this? 

[http://ebcd.pcministry.com/](http://ebcd.pcministry.com/)

---

### Post by abhaysahai on 2006-02-19
Here is my grub enties for Windows

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


If they might help

---

### Post by kseise on 2006-02-20
[QUOTE=ahlich]So your windows feels embarrassed by how much coffee you are brewing these days and decided to commit suicide?

Did you tryed this? 

[http://ebcd.pcministry.com/](http://ebcd.pcministry.com/)[/QUOTE]
Tried it, but on boot to XP, it says I need to load hal.dll under windows root /system32

---

### Post by kseise on 2006-03-02
Long LOng LOONG story short: Reformatted drive and reinstalled.  MBR corrupted, no backups on disk, MFT over written, data went bye bye.

---

### Post by mlind on 2006-03-02
Well there would have been XP's own recovery console with commands like
Fixmbr, Fixboot and I recall there was Fixmft aswell...

---

### Post by kseise on 2006-03-05
Unfortunately, I could not boot from the XP installation CD until the hard drive was reformatted.  XP reported that it could not find a swap space on my drive.  It was very bizarre.  I have restored XP like you said before, but NOTHING worked.  I am only posting this as a follow up for anyone else reading the thread.

---

