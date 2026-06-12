---
title: "I need help. I want to remove it."
date: 2011-03-05
forum: General Help
---

### Post by DDarkusTriforce on 2011-03-05
Now don't get me wrong, I don't have ANYTHING against Ubuntu or it's users. I just have absolutely no idea how to use it, and I can't get any programs to run on it. Since I can't do anything on it in any way, shape, or form, I would like to remove it from my computer, because it is doing nothing but taking 100 Gigabytes away from Windows. Keep in mind, I still don't know how to do ANYTHING in Ubuntu. I will need exact, step-by-step instructions. If you give me the right instructions, I will be FOREVER grateful! Thanks in advance!

---

### Post by watgrad on 2011-03-05
Did you install ubuntu using wubi? (i.e., did you install Ubuntu within Windows)
if so you can just remove if from that windows add/remove programs control panel.

---

### Post by Irony on 2011-03-05
Restore windows bootloader by using your windows disk to do fixmbr - then boot into windows and format the ubuntu partitions.

You do not need to boot into ubuntu to do anything.

---

### Post by DDarkusTriforce on 2011-03-05
I installed Ubuntu along-side Windows 7 using a flash drive.
 And Irony, can you please explain. I really have no idea what you're saying.

---

### Post by DDarkusTriforce on 2011-03-05
Also, I don't NEED to uninstall Ubuntu. I just want to decrease it's partition space to the smallest possible ammount, so that WIndows is at least ALMOST the way it was before.

---

### Post by |{urse on 2011-03-05
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

Happy trails dude.

---

### Post by DDarkusTriforce on 2011-03-05
it now says

error: unknown filesystem.
grub rescue>


and I dont know what to do! MY comp didn't com with a disk. it may have a built in disk from the boot manager, but i dont know. I was careful to delete ONLY the linux partition, not the grub partition. im posting this on another computer.

---

### Post by oldos2er on 2011-03-05
You need to restore Windows' bootloader, as Irony said. [http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)

---

### Post by DDarkusTriforce on 2011-03-05
I don't have disk. I know the startup disk is on the boot manager, but which of the 6 options is it?

---

### Post by DDarkusTriforce on 2011-03-05
the 6 startup options are 
1. HDD/SSD
2. CD/DVD
3. FDD
4. LAN
5. eSATA
6. USB

which do i use?

---

### Post by cchhrriiss121212 on 2011-03-05
You will need some kind of bootable repair CD, there are free ones out there if you google. Or you could borrow a Windows disk from a friend. 
You could even install GRUB again from an Ubuntu live CD.

---

### Post by DDarkusTriforce on 2011-03-05
I can? How do  do so? I wanna install GRUB without reinstalling Ubuntu, though.

Oh! Idea!!! What if I do reinstall Ubuntu, but only give it like one gigabyte? Will tht work?

---

### Post by grahammechanical on 2011-03-05
> What if I do reinstall Ubuntu, but only give it like one gigabyte? Will tht work?

No. Most emphatically, no. Ubuntu will need from 10GB upwards.

The installer will just refuse to play the game with you.

Regards.

---

### Post by cchhrriiss121212 on 2011-03-05
Yeah, that would work, but it would need more than that, 8GB should be enough. After the installation, you could use startup manager to set Windows as the default OS, and set timeout to 0 seconds, so you won't know Ubuntu is there.

---

### Post by inkrypted on 2011-03-05
Check with your computer manufacture. Most systems that have the OS installed on a partition (the stupidest idea in history) usually have a key or key sequence to start Repair/Recovery.

---

### Post by DDarkusTriforce on 2011-03-05
I really dont know where to find this, so can yuo please find out? I know, m a n00b. It's a Toshiba Satelite L655-S5150

---

### Post by DDarkusTriforce on 2011-03-05
I am on buntu from my USB. When I go to instal it, it dosn't even recognize the freespace where my old Ubuntu used to be. How to I fill the Free Space with the Windows Partition?

---

### Post by DDarkusTriforce on 2011-03-05
How do I know how much space I give to windows to fill the free space?

---

### Post by DDarkusTriforce on 2011-03-05
SO sorry for the quadruple post, but if I reinstall Ubuntu, will I reinstall GRUB?

---

### Post by cchhrriiss121212 on 2011-03-05
> if I reinstall Ubuntu, will I reinstall GRUB?Yes.

> How to I fill the Free Space with the Windows Partition?
It's best to do that from within Windows, but gparted should work fine.

---

### Post by lisati on 2011-03-05
> **DDarkusTriforce said:**
> I really dont know where to find this, so can yuo please find out? I know, m a n00b. It's a Toshiba Satelite L655-S5150

Most computers I've used have one or more keys you can press for various options at boot time. They are usually clearly shown on the boot screen. On my laptop (a Toshiba Satellite M200) there's even a keypress that's not shown on the boot screen that will boot from the recovery partition. I'm a bit hesitant to share which key it is, because if you're not careful, you could wipe out **everything** on your Windows partition.

---

### Post by bcbc on 2011-03-05
Boot from the USB but don't install. Select "Try it" or "try without installing".
Then go to a command line (CTRL+ALT+t) and post the output of:
```
sudo fdisk -l
``` (that's a lower case -L)

Get that info back here and I'll tell you how to get it booting windows using lilo.

---

### Post by |{urse on 2011-03-06
Yeah, you can find various bootcd's also online. I like UBCD

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

You can use this instead of a windows disk to fix the mbr. The program on UBCD to fix the master boot record is called mbrwork.

Beyond that, If you don't own a copy of windows I really can't help you beyond suggesting either borrowing a disc from a friend or finding one in a ditch somewhere.

---

