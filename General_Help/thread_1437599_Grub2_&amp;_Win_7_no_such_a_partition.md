---
title: "Grub2 &amp; Win 7: no such a partition"
date: 2010-03-24
forum: General Help
---

### Post by l4zy on 2010-03-24
Hi,

I installed 9.10 Karmic yesterday. 
I've have my Win 7 on /dev/sda.

/dev/sda3 has boot flag, grub2 did find to windows bootloader from there. When choosing Win 7 from Grub menu i get error: no such a partition and it prompts me back to Grub mene.

I have tried with "e" to choose hd(0,1) & hd(0,2) which are /dev/sda1 and /dev/sda2 but no solution.

I reinstalled windows bootloaders with Win 7 cd and booted to windows to see that it works again. After that i reinstalled Grub2 via Live-CD.

Again it finds Win 7 bootloader but same "error"

Any ideas what is causing this problem? 

I've installed many many dual-boots due my work and not this kind of problem. Sometimes Grub doens't find Windows but installing again it proper way it works.

---

### Post by john newbuntu on 2010-03-24
When you fixed win7 and re-installed grub, did you install it into the MBR of sda?

The way I understand it, /dev/sda3 has the boot flag set and has Win7 installed and running satisfactorily. /dev/sda1 is probably your ext* filesystem having Ubuntu root partition and /dev/sda2 is probably the swap.  Please correct me if I am wrong.
Once this setup works, insert Karmic liveCD, mount the Ubuntu root partition and install grub to the MBR of sda.  Finally a "sudo update-grub" should do it.

---

### Post by l4zy on 2010-03-24
i've got two different disks. 

I'm sorry that i didn't write about that.

/dev/sda has win7 ( /dev/sda1 /dev/sda2 /dev/sda3)

/dev/sda1 is Dell's some support partition
/dev/sda2 has some M$*stuff in it
/dev/sda3 has win 7 with boot flag

Ubuntu is installed on /dev/sdb, and when reinstalling grub2 i pointed it to /dev/sda3.

At the first install installed installed grub automatically to /dev/sda3, i think it's the right partition since it has the bootflag...

---

### Post by andrewthomas on 2010-03-24
> **l4zy said:**
> i've got two different disks. 

I'm sorry that i didn't write about that.

/dev/sda has win7 ( /dev/sda1 /dev/sda2 /dev/sda3)

/dev/sda1 is Dell's some support partition
/dev/sda2 has some M$*stuff in it
/dev/sda3 has win 7 with boot flag

Ubuntu is installed on /dev/sdb, and when **reinstalling grub2 i pointed it to /dev/sda3.**

At the first install installed installed grub automatically to **/dev/sda3, i think it's the right partition since it has the bootflag**...
You want grub2 on the MBR of sda.  Installing it to a windows partition is what is causing your problem.  By the way, Ubuntu does not care at all about the boot flag.

---

### Post by Mark Phelps on 2010-03-24
> **l4zy said:**
> ... Ubuntu is installed on /dev/sdb, and when reinstalling grub2 i pointed it to /dev/sda3.

I'm surprised you didn't get an error message because GRUB can't be installed to an NTFS partition.  

You need to install it to your first /sdb partition.

After that, when you boot into Ubuntu, do "sudo update-grub" from a terminal and it should find the Win7 loader and create the proper menu entry for it.

---

### Post by andrewthomas on 2010-03-24
> **Mark Phelps said:**
> 
You need to install it to your first /sdb partition.

Wouldn't the OP have to either install grub to the **MBR of sdb** and change the boot order in BIOS to boot sdb 1st, or to chainload grub 2 from the windows bootloader for this to work?

---

### Post by l4zy on 2010-03-24
Mark Phelps:

Could you explain me when ubuntu installed grub2 to /dev/sda at the first time (i mean the time when you install ubuntu)

And yes, i've tried installing grub2 also to /dev/sdb, and i created proper menuentry to for Windows 7, which was pointing to /dev/sda3.

Still the same problem, ubuntu works perfectly but Win 7 doens't.

Ofc Ubuntu works, but i can't understand why win 7 wont boot even tho grub2 finds the win bootloader from /dev/sda3

---

### Post by l4zy on 2010-03-25
I tried to install Grub2 to /dev/sdb as you guys told me to. It seems that i can't install it there, /dev/sdb is GPT partition table and grub2 install fails. It complains that the partition table doens't have BIOS boot partition or something like that?

Any ideas ?

---

### Post by Mark Phelps on 2010-03-25
Sorry, can't explain why GRUB didn't complain when you installed it to sda.  It's not supposed to be installable to MS Windows partitions.

The process that I've seen work most often is to install GRUB to the MBR and first Linux partition of a drive, boot from that drive, and use "update grub" to find the other OSs and add the proper entries to the GRUB menu.

Since you said you installed Ubuntu to sdb, I figured it would be a simple matter to install GRUB to sdb as well.  And then do what I indicated above.

However, has Win7 ever launched OK since you did the Ubuntu install?

IF not, there may be something basically broken with the Win7 boot loader -- independent of GRUB.  If you didn't have GRUB installed to sda, you could disconnect the other drive and boot it to confirm you can still boot into Win7.  To do that now, you would have to overwrite the GRUB in the MBR of SDA using an Win7 Repair CD -- and then, you would only be able to boot into Win7.

---

### Post by l4zy on 2010-03-26
I installed Win 7 bootloader again via Win-CD. It worked. 

I tried to install GRUB2 to sdb which is GTP partition. I did made grub_boot on flag to that small partition which i greated with gparted.

Grub2 install didn't show any errors and when i rebooted grub wasn't working at all. When i reinstalled grub2 to /dev/sda Ubuntu was booting and if did find Win 7 bootloader again with no problem.

But Win 7 wasn't booting from grub2 menu.

Gonna try to install Ubuntu again but this time usin MBR instead of GPT.

---

### Post by Mark Phelps on 2010-03-26
Looks like whatever you install last, wins!

If you simply can't get both Win7 booting and Ubuntu booting to work, an alternative would be to download and install EasyBCD from the NeoSmart Technology forums.  

It will install GRUB4DOS in yout Win7 partition and will add an entry to your Win7 BCD to allow you to select Ubuntu at boot time.

Good luck.

---

### Post by l4zy on 2010-03-26
Thanks for the reply.

I got setup working.

Solution. 

I mage MBR to disk insteat of GBT and reinstalled ubuntu. Now grub2 is installed to /dev/sda3 and Ubuntu & Windows 7 are booting. Seems that there was some problems with GPT.

Thanks

---

### Post by spaik on 2010-03-26
if u searched the forum u would have find this :) [http://ubuntuforums.org/showthread.php?p=9003311#post9003311](http://ubuntuforums.org/showthread.php?p=9003311#post9003311)  

i got the same problem or kinda the same and everything is working fine now.

---

