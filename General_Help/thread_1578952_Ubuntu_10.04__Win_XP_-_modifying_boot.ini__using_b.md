---
title: "Ubuntu 10.04 / Win XP - modifying boot.ini / using bootpart ?"
date: 2010-09-21
forum: General Help
---

### Post by Tuliku on 2010-09-21
Hi, on my laptop at work (win xp), i have a lot of free space left, and decided to make a dual boot with ubuntu.

Is it possible to install ubuntu on the second partition, as well as the bootloader (grub), and then modify the boot.ini file somehow to show the choice of ubuntu when i start up ?

I did some googling and found that a tool called bootpart can do this, but also found that this tool does not work properly on NTFS and large disks.

Any other idea's / suggestions / etc ?

---

### Post by wilee-nilee on 2010-09-21
> **Tuliku said:**
> Hi, on my laptop at work (win xp), i have a lot of free space left, and decided to make a dual boot with ubuntu.

Is it possible to install ubuntu on the second partition, as well as the bootloader (grub), and then modify the boot.ini file somehow to show the choice of ubuntu when i start up ?

I did some googling and found that a tool called bootpart can do this, but also found that this tool does not work properly on NTFS and large disks.

Any other idea's / suggestions / etc ?

Why do you need to do it this way rather then let Ubuntu use grub as the bootloader?

---

### Post by lmarmisa on 2010-09-21
I am not sure if I understand you. If you wish to see the grub menu at startup, open a terminal and type:

```

sudo gedit /etc/default/grub

```Then delete the #char of this line
```

GRUB_HIDDEN_TIMEOUT=0

```Save &exit and type this other command:

```

sudo update-grub2

```

---

### Post by Tuliku on 2010-09-21
It's a company laptop, and i don't want to mess with the MBR.
If for some reason i need to get rid of the linux partition, i can simply delete the partition without needing to do anyting with the MBR.

Thats why i want the whole installation on the linux partition, and rather play around with the boot.ini / bootpart / whatever will work.

---

### Post by lmarmisa on 2010-09-21
If your PC is able to boot from a pendrive (check your BIOS menu), you could install the grub loader in the pendrive and so start your Ubuntu system (installed in a partition of the hard drive) from this pendrive. The MBR of the hard drive will be not touched at all.

BTW: you have to define a second partition for swap in your hard drive.

---

### Post by searchfgold6789 on 2010-09-21
Well, if you know what you're doing you can try popping in the Live CD, and adding an option to Windows' boot menu using the recovery console that points to GRUB(2). But if you want the windows boot selection screen to come up instead of the GRUB screen you will have to do a fixmbr from the recovery console, as well.
GRUB(2) and the Windows boot loader do exactly the same thing, except that Windows might not be able to boot linux if you select it from the boot menu after you have used the recovery console in prescribed way. If it doesn't work and Linux is pretty much inaccessible to you, go into the Live CD and type (XY being the linux system partition on your hard disk)
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
sudo umount /mnt
```to reinstall GRUB2.
You could also try that great idea with the pendrive. You could even try installing Ubuntu onto the pendrive instead of just the ubuntu bootloader O.o)
Hope this helped.

---

### Post by lmarmisa on 2010-09-21
Another option is to install Ubuntu with Wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by philinux on 2010-09-21
> **lmarmisa said:**
> Another option is to install Ubuntu with Wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I wouldn't do that with a company laptop. Updates to grub can wreck the windows mbr.

@tuliku,

Are you sure you should mess with a works laptop?

---

### Post by Tuliku on 2010-09-21
Thanks for the replies.
I used to use a USB harddisk with a ubuntu installation on it, and boot from that, but it is slow.
I will do some googling about this wubi, what i found till now looks promising.

But simply editing the boot.ini in some way, or using bootpart is not recommended / possible / sufficient ?

---

### Post by lmarmisa on 2010-09-21
My last proposal: virtualization. 

Install VirtualBox in your XP and define one or more Ubuntu virtual machines. The advantage is that you could use XP and Ubuntu at the same time. I really like VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

**EDITED:** 

In relation with the personal use license of VB, this comment is important:


[LIST=1]
[*]**What exactly do you mean by *personal use* and *academic use* in the [Personal Use and Evaluation License]("http://www.virtualbox.org/wiki/VirtualBox_PUEL")?**
[/LIST]
[INDENT]  Personal use is when you install the product on one or more PCs yourself  and you make use of it (or even your friend, sister and grandmother).  It doesn't matter whether you just use it for fun or run your  multi-million euro business with it. **Also, if you install it on your  work PC at some large company, this is still personal use.** However, if  you are an administrator and want to deploy it to the 500 desktops in  your company, this would no longer qualify as *personal use*. Well,  you could ask each of your 500 employees to install VirtualBox but  don't you think we deserve some money in this case? We'd even assist you  with any issue you might have. 
 [/INDENT] [INDENT]  Use at academic institutions such as schools, colleges and universities  by both teachers and students is covered. So in addition to the personal  use which is always permitted, academic institutions may also choose to  roll out the software in an automated way to make it available to its  students and personnel. 
 [/INDENT][http://www.virtualbox.org/wiki/Licensing_FAQ](http://www.virtualbox.org/wiki/Licensing_FAQ)

---

### Post by Tuliku on 2010-09-24
How is this with the virtual box regarding the performance ?
I have the i5 520 processor, intel graphics card, 2 gb ram, running xp.

I managed to make to make it work with bootpart. It's relatively simple and easy to remove the whole linux part now if needed.

But... ubuntu does not seem to like my laptop
- 10.04, installation is only possible with using a external screen. Although i googled and found several instructions on how to make the main screen of the laptop work, it does not work for this one, most likely cause everyone else has the nvidea graphics card.
- 10.10 beta, when booting up the installation, it stops with an error message that the keyboard is unknown..
- 9.10 Installation goes great, and boots up perfectly, but once on the main screen, after 5 seconds whole laptop freezes.
I will play around a bit more :-(

---

