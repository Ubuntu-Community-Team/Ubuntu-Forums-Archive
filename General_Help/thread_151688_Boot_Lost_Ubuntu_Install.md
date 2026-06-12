---
title: "Boot Lost Ubuntu Install"
date: 2006-03-28
forum: General Help
---

### Post by Minn3h on 2006-03-28
I had grub all set up to dual boot windows and ubuntu, but overwrote that to use the windows bootloader, is there a way I can boot to that linux partition now? Using a live cd? Unplugging ide cables to make my linux hdd the only one? Other ways?

---

### Post by Qrk on 2006-03-28
The easiest way I've found is to use the install Cd, but only the "Grub" portion of the installation process. 

Heres the howto:

[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Minn3h on 2006-03-28
Here's what I did.

Booted to Knoppix.
Used terminal and went "su" "grub" "root (hd1,0)" "setup (hd1,0)" "quit".
Then I used "dd if=/dev/hdb1 of=/home/ubuntu.bin bs=512 count=1"
Took ubuntu.bin from the temp folder in Knoppix and put it in C:\ubuntu.bin on my windows partition.
Entered a line in boot.ini: C:\ubuntu.bin="Ubuntu"
Rebooted and when I selected Ubuntu, all I got was "GRUB _"

Any ideas what I did wrong or what I can do?  Seems like it should have worked to me? Maybe I need to edit my menu.lst in some way to reflect that GRUB is now installed on hdb1 and not the MBR, I wouldn't know how though.

---

### Post by jerrykenny on 2006-03-28
That was good advice Qrk gave you . . . .

---

### Post by Minn3h on 2006-03-28
I followed the advice in that thread, not the first set of advice because it didn't apply (I don't want GRUB on my MBR), but it still didn't work...

---

### Post by AndrewCaul on 2006-03-28
[QUOTE=Minn3h]I followed the advice in that thread, not the first set of advice because it didn't apply (I don't want GRUB on my MBR), but it still didn't work...[/QUOTE]
You need GRUB on your MBR to boot Linux. Windows only allows Windows operating systems to boot.
It's possible to install GRUB and make it boot Windows by default, if that's what you want.

---

### Post by Minn3h on 2006-03-28
[QUOTE=AndrewCaul]You need GRUB on your MBR to boot Linux. Windows only allows Windows operating systems to boot.
It's possible to install GRUB and make it boot Windows by default, if that's what you want.[/QUOTE]

Well, that's just not true because I'm already booting one other operating system from the windows bootloader, not to mention there are lots of guides for how to boot ubuntu/linux with the windows bootloader.

What I did after installing GRUB I'm almost positive was what I need to do, can anyone explain what I might have done wrong installing GRUB to hdb1?

---

### Post by ukris03 on 2008-02-20
I don't even see the Ubuntu partition. Please help... I'm not very savvy in these matters

---

