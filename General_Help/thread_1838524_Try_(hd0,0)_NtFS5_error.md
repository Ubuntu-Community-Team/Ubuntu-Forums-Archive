---
title: "Try (hd0,0): NtFS5 error"
date: 2011-09-03
forum: General Help
---

### Post by Intzi1992 on 2011-09-03
I try to boot my computer and I have this message NTFS5 "prefix" is not set
Error no such device: ......
Error no such device: ..........
And after this it take's to the grub menu
Grub>_
( my computer is using windows and the ubuntu is installed with wubi program) 
Does anyone know how can I fix it?

---

### Post by bcbc on 2011-09-03
Check the \ubuntu\disks\ directory in Windows and make sure you have your root.disk.

If not check this out: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by Intzi1992 on 2011-09-03
You Are Great Man... Your Guide Helped Me And My Problem Is Fixed.
But The Question Is How Can I Avoid To Have The Same Problem Again?

---

### Post by bcbc on 2011-09-04
Great! Glad to hear it's working again.

Sometimes the problem is caused by forced shutdowns. These can be avoided by [Alt+SysRq R-E-I-S-U-B]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen"). If this is not the cause, then there could be some hardware incompatibility... but this is speculation. I run a wubi install most of the time to see what problems there are and this hasn't ever happened to me.

But the easiest way to avoid this is to switch from a Wubi install to a direct install - then if there is a problem you at least still have all your data. Your could [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") your existing wubi install to a partition; or just backup your data and reinstall.

This is the intention of Wubi - to try out Ubuntu without risk - and then either uninstall or switch to a dual boot.

e.g. here is a [guide]("http://members.iinet.net/~herman546/index.html") to partition and install

If you decide to stick with Wubi, just keep backups up to date or store important data on the /host partition.

---

### Post by Intzi1992 on 2011-09-04
Yes You Are Right But.. Is There Any Way To Keep My Files My Programs And Options Like The Way There Are Now?
Or I Will Have To Install Everything From The Beggining.

---

### Post by bcbc on 2011-09-04
Yes. That link I posted to [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the Wubi install will be exactly the same as your current Wubi install.

---

### Post by Intzi1992 on 2011-09-04
Bcbc i am trying your guide but i have a problem to this point.
[http://www.megaupload.com/?d=XM7OYCRJ](http://www.megaupload.com/?d=XM7OYCRJ) (sorry for that but i dont know how alse to upload this photo)

---

### Post by bcbc on 2011-09-04
Use [http://imagebin.org/](http://imagebin.org/) or click "Manage Attachments" to your next reply and upload the image. 

Otherwise, from a terminal, "select all" from the menu and copy and paste (Ctrl+Shift+C to copy; or use the menu again).

Also, please post the output of (lower case -L)
```
sudo fdisk -l
``` and indicate which partition you are migrating to. Thanks

---

### Post by greenberit on 2013-03-31
i have installed ubuntu 12.10 using wubi installer.
when i boot using ubuntu from boot menu then it shows "TRY(hd0,0) :NTFS5:"
and it stucks there forvever...
whats the problem.
please help

---

