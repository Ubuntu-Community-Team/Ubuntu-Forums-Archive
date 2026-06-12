---
title: "grub rescue&gt; Problems after Update"
date: 2011-01-22
forum: General Help
---

### Post by Sor3nt on 2011-01-22
Hy all, i have problems with my new netbook.
I have installed ubuntu netbook remix, all fine, system starts but the wifi driver doesnt works. so i googled and found this [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
this page says, do a update... so i do a apt-get update and a apt-get upgrade, after 15 minutes all done (also grub is upgraded!). i want to reboot my maschine, the system hangs on the ubuntu shutdown screen, i wait 10 minutes, nothing happend. i do a hardreset. and now if i start the netbook comes this :
grub rescure>

****, okay now i googled again and found this [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
but if i type ls into the rescue console only comes this up :
(hd0)
nothing more, no (hd0,1) or any other partitions and if i try "ls (hd0)" it says unknown filesystem

any ideas ? :) i hope :D

Thanks !

//edit :
and if i type set into the console this comes :
prefix=(hd0)/boot/grub
root=hd0

---

### Post by kansasnoob on 2011-01-22
Was this a Wubi install in an existing Windows OS?

---

### Post by Sor3nt on 2011-01-22
yes i installed the ubuntu via wubi

---

### Post by kansasnoob on 2011-01-22
Look here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Sor3nt on 2011-01-22
okay thanks, im not sure maybe it doesnt help... i have created a external bootable hdd drive with ubuntu netbook remix (i have at the moment no working usb drive ;( ) and if i try to boot from the external hdd it says like this : kernel panic, cant mount root device...
i will try to find / buy a usb drive and try this again.

or exists other ways to recover it direct in the rescue shell ?

Thanks anyway
Bye
Matthias

---

### Post by kansasnoob on 2011-01-23
> **Sor3nt said:**
> okay thanks, im not sure maybe it doesnt help... i have created a external bootable hdd drive with ubuntu netbook remix (i have at the moment no working usb drive ;( ) and if i try to boot from the external hdd it says like this : kernel panic, cant mount root device...
i will try to find / buy a usb drive and try this again.

or exists other ways to recover it direct in the rescue shell ?

Thanks anyway
Bye
Matthias

Not sure what's up? Does this machine also have Windows? If so you need to begin by restoring the Windows MBR as shown in the link I posted.

Not sure what's wrong with the external drive installation. I suppose we'll need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rubi1200 on 2011-01-23
If you are getting the grub rescue prompt and this is a Wubi install, it won't help you.

Follow the advice posted by kansasnoob and post the results of the boot info script so we can get a better idea of what is going on.

---

### Post by kansasnoob on 2011-01-23
> **Rubi1200 said:**
> If you are getting the grub rescue prompt and this is a Wubi install, it won't help you.

Follow the advice posted by kansasnoob and post the results of the boot info script so we can get a better idea of what is going on.

I'm wondering if Sor3nt somehow used Wubi to install Ubuntu to an external drive, is that even possible?

I know it's possible to install to a separate NTFS partition, how about a separate drive?

---

### Post by Rubi1200 on 2011-01-24
> **kansasnoob said:**
> I'm wondering if Sor3nt somehow used Wubi to install Ubuntu to an external drive, is that even possible?

I know it's possible to install to a separate NTFS partition, how about a separate drive?

In a word, yes.

Basically, any partition that  Windows can see will do. 

You can use NTFS (preferred) or FAT32 (but this  has a 4GB file size limit, so if you ask for more than 4GB Wubi creates  multiple virtual disks, root.disk, usr.disk and, if big enough,  home.disk).

---

