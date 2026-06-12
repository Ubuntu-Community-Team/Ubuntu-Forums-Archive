---
title: "Boot Help Please"
date: 2010-04-06
forum: General Help
---

### Post by Jake Dawkins on 2010-04-06
Well i installed ubuntu studio 9.10 and I really like it but... I decided It's not really worth it in my eyes so I'd like to uninstall it. the only problem is im not sure how to modify the master bootloader. last time I attempted something like this i was incredibly... stupid and just deleted the partitions that contained the OS but on the next boot I got a nice message saying...

grub loading...
error: file not found
<GRUB rescue>_ 

and my computer refused to boot. I'm not sure how to completely remove that so anyone who can help I'd highly appreciate it. THANKS!

---

### Post by N92 on 2010-04-06
First are you dual booting?

If not just do a clean install of whatever OS you want to use.

---

### Post by firedragoneater on 2010-04-06
But first make sure your BIOS is set to load CD/DVD Drive over HDD etc - To access the loading options it should be as simple as holding f9 as soon as you turn the computer on.
Hope I helped!
The Warlock.

---

### Post by oldfred on 2010-04-06
Grub is in the MBR or master boot record and is looking for the rest of its boot files in the partition you deleted. You need to reinstall the windows boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by CLEARviewF on 2010-04-06
Which operative systems do you finally want to have in your system? Do you already have Windows in it?

---

