---
title: "Ubuntu not booting, VV Urgent"
date: 2009-06-30
forum: General Help
---

### Post by 7raTEYdCql on 2009-06-30
I should blame this on myself.
I messed with the /boot/grub/menu.lst file, and now there is no ubuntu option on my startup. It only has memtest.

Is there anyway in which i can manually boot into the system, i can't format because there are important files on the comp.

---

### Post by Aearenda on 2009-06-30
I think I would try using the [SuperGrub CD]("http://www.supergrubdisk.org/") to get your system booted, and then try to fix the menu.lst.

---

### Post by nikgare on 2009-06-30
You can use the ubuntu live/install cd (or any other!) to gain access to your disks, then edit the grub file.
you'll need something like this in your menu.lst

> 
title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		828ceb64-d9c7-4efb-82b5-98d73c256bf6
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=828ceb64-d9c7-4efb-82b5-98d73c256bf6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet


This might help to get the uuid of the disk:
[http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/](http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/)

---

### Post by 7raTEYdCql on 2009-06-30
there is a problem. My ubuntu is 9.04 and the iso file that i have is 8.04. There is a controversy with the filesystems.

---

### Post by t4thfavor on 2009-06-30
both are ext3 I would think, you should have no problem soing what was stated above.

---

### Post by themusicalduck on 2009-06-30
If you used ext4 when you installed 9.04 then you will need to use a 9.04 live CD to access your files. Also once you have access it might be worth posting the contents of your menu.lst here so we can help.

---

### Post by 7raTEYdCql on 2009-06-30
I tried using reinstalling grub from a live cd, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).

It is getting hung, everytime i do setup(hd0)
Is there anyway in which i can change menu.lst from the grub menu. Someone please help. This is very urgent.

---

### Post by t4thfavor on 2009-06-30
at the grub menu press escape, and the e. modify it to your hearts desire, and then it should load. after loading into your os you must change menu.lst as the changs made at grub do not stick around.

---

### Post by 7raTEYdCql on 2009-06-30
when i press e. i get a menu with all the options. On pressing any of the options Memtest begins. None of the options, give me a clean boot.

---

### Post by 7raTEYdCql on 2009-06-30
The issue is that my linux partition does not get mounted. Due to the conflicting file systems.

---

### Post by thespirit3 on 2009-06-30
When you press 'e' for edit it should let you edit the boot line.   You'll probably need to know what kernel you were using though - change kernel from /boot/memtest to /boot/vmlinuz-2.6.whatever and then boot.   However, I suspect you don't know which kerner version you were on, so booting a current live CD and manually fixing menu.lst is probably your best bet :(

---

### Post by 7raTEYdCql on 2009-06-30
By current you mean, 9.04??

---

### Post by 7raTEYdCql on 2009-06-30
Will supergrub help in any way??

---

