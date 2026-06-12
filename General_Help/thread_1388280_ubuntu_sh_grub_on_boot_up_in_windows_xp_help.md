---
title: "ubuntu sh grub on boot up in windows xp help"
date: 2010-01-22
forum: General Help
---

### Post by 777lorenzo on 2010-01-22
Thank for the help in advance. please help a ubuntu newb. i installed ubuntu 9.10 for the third time on my lenovo s10e running windows xp. my first two installs went good until ubuntu tried to update gnome to the latest version and my computer went to sh grub on reboot, so on my third install of ubuntu 9.10 using wubi i turned off  updates and the computer was working wonderfully for weeks until i let my netbook battery die.then the dreaded sh grub on reboot. can some one please help i saved alot of information that i really need. please keep it very simple i do not under stand all that linux lingo. thanks  alot i really like ubuntu and prefer to use it over xp. :D

---

### Post by meierfra. on 2010-01-23
> tried to update gnome to the latest version and my computer went to sh grub on reboot,

This was  caused by a bug in Grub2. It can be fixed fairly easily:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Try that, but I doubt it will cure your current problem.

> i let my netbook battery die.then the dreaded sh grub on reboot.

You probably did some damage to your Wubi file system. So I suggest to run a file system check on the  partition  containing Wubi and also on your Wubi file.

Boot into Window XP. Go to "start>run", type "cmd" and press enter. That will open the XP command line

Type

```
chkdsk /r C:
```

This  assume that Wubi is on your C: drive. If not, replace "C:" by the drive letter of the partition containing "Wubi"

If you are asked  to run "chdsk" after to next reboot, answer  "yes" and reboot into XP.

If chkdsk fixed some errors, run "chkdsk /r C:" again, until it finds no more errors.

Next boot from your Ubuntu Live CD. Open a terminal  and type

```
sudo mount /dev/sda1 /mnt
```
This assume that Wubi is on /dev/sda1.  If not, use the correct device name for the partition containing Wubi. 

Then

```

sudo e2fsck -fyv /mnt/ubuntu/disks/root.disk
```

If e2fsck fixed some errors, run it again, until it no longer fixed any errors.

If this did no cure your problems, or you would like more detailed instruction, boot from the  Ubuntu LiveCD and follows these [instruction ]("http://bootinfoscript.sourceforge.net/")to run the Boot info script and post the RESULTS.txt:

---

### Post by 777lorenzo on 2010-01-23
Thank meierfra i will try that.i am on a netbook no cd drive.

---

