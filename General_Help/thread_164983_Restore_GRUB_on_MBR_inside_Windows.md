---
title: "Restore GRUB on MBR inside Windows?"
date: 2006-04-23
forum: General Help
---

### Post by lezz on 2006-04-23
Hi

Is it possible to restore GRUB on MBR from Windows? That is, I dont want to restore it with a floppy disc or from Linux. I has to be done from Windows XP.

Any ideas?

---

### Post by xXx 0wn3d xXx on 2006-04-23
[QUOTE=lezz]Hi

Is it possible to restore GRUB on MBR from Windows? That is, I dont want to restore it with a floppy disc or from Linux. I has to be done from Windows XP.

Any ideas?[/QUOTE]
Do you have a ubuntu install disc ? By using [ this tutorial](http://ubuntuforums.org/showthread.php?t=24113&highlight=fix+mbr), you can fix your MBR.

---

### Post by Sef on 2006-04-23
> Is it possible to restore GRUB on MBR from Windows?

AFAIK, no.  The windows boot loader only sees itself.  The only way to do that is with a floppy or cd upon boot up.   Now, why do you want to do this?  Is it because you want Windows to be the default upon boot?  If so, install grub and set Windows as the default.

---

### Post by Qrk on 2006-04-23
Boot from your Windows CD into the recovery console, and use the command *fixmbr*

I don't believe you need to specify any options, it should know which drive to fix. 
You may need to tell it where the mbr is which should be \Device\HardDisk0. You can find out which device by using the *map* command.

This will erase Grub. completely. You need a Linux to install or modify Grub.

---

### Post by incubus on 2006-04-23
> 
Boot from your Windows CD into the recovery console, and use the command fixmbr


Oh wait, I think what the original poster meant was to reinstall GRUB, not erase it from the MBR.

incubus

---

### Post by Qrk on 2006-04-23
> 
This will erase Grub. completely. You need a Linux to install or modify Grub.

Yes, but that is all you can do from windows.

---

