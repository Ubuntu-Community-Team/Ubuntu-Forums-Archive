---
title: "[grub2] insmod=ext2 while I use ext4 root partition"
date: 2010-04-23
forum: General Help
---

### Post by gawadelnil2002 on 2010-04-23
guys I got a problem booting ubuntu 10.4 RC but i solved it by replacing root partirion uuid in grub boot menu then I disapled totally uuid passing to linux from /etc/default/grub .
but something else i noticed why grub choosed insmod=ext2 why not ext4 specially I use now ext4 .
I tried by editing the grub boot menu replacing "insmod=ext2" by "insmod=ext4" it booted and the three lines error during booting that i used to see them science ubuntu 9.10 totally disappeared . 
really I dont understand can anybody explane for me.
and if what i did was right ,can anybody tell me how to make grub always and permenantly detect ext4 as ext4 not as ext2.

---

### Post by drs305 on 2010-04-23
ext2 covers ext 2,3 and 4. If you look in /boot/grub, where the Grub 2 modules are stored, you will find ext2.mod. There is no ext4.mod

What were the three error messages that you were getting?

---

### Post by gawadelnil2002 on 2010-04-23
Exactly I'm not sure that those three lines is errors because i dont see them in now kernel log but those three lines will not appear if I boot with insmod=ext4
 
But I booted with insmod=ext4 so its strang it booted without ext4.mod
 
I will see I may have it :)
 
edit "5 Minutes i willcome back I have to reboot and see something"

---

### Post by drs305 on 2010-04-23
The next time you get to the Grub2 menu, type "c" to get to the Grub prompt. Type "lsmod" and it will show which modules are loaded. You will find ext2 listed as one of the loaded modules.

Hint: If too many modules are loaded, they may scroll off the page. To see them all, type "set pager=1" and you will be able to scroll through the list using the ENTER key.

Try to load ext4 with "insmod ext4". On my computer, I get a "error: file not found" since the ext4 module doesn't exist.

---

### Post by gawadelnil2002 on 2010-04-23
> **drs305 said:**
> The next time you get to the Grub2 menu, type "c" to get to the Grub prompt. Type "lsmod" and it will show which modules are loaded. You will find ext2 listed as one of the loaded modules.
 
Hint: If too many modules are loaded, they may scroll off the page. To see them all, type "set pager=1" and you will be able to scroll through the list using the ENTER key.
 
Try to load ext4 with "insmod ext4". On my computer, I get a "error: file not found" since the ext4 module doesn't exist.
 
You are totally right in everything there is no such ext4.mod in /boot/grub
I dont how my system boots with this insmod ext4 it drives me insane specially after U said that gives u an error no such file.
I use ubuntu 10.4 basic sysem no gui yet just i love to built my stuff codecs my own java before i install gui :)
So do u use the same version or what ?
 
Edit: I think when it boots with insmod ext4 and it dosnt find it it automatically falls back to ext2.mod then start again I noticed too that my system take alittle bit more time to boot with that option ext4,It explains now why it take more time to boot.

---

### Post by psusi on 2010-04-23
The ext2 module is built in so it doesn't need loaded.  When you changed it to ext4 it probably just printed an error that it couldn't find it, then continued with the boot.

---

### Post by drs305 on 2010-04-23
> **gawadelnil2002 said:**
> 
I dont how my system boots with this insmod ext4 it drives me insane specially after U said that gives u an error no such file.

So do u use the same version or what ?
 
Edit: I think when it boots with insmod ext4 and it dosnt find it it automatically falls back to ext2.mod...

Your analysis is correct. It will *try* to load modules specified in the grub.cfg file, but when it can't, Grub2 continues. It can do so because the ext2 module is already included in the "preloaded" modules.

---

