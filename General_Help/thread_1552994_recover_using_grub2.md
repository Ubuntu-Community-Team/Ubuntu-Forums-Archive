---
title: "recover using grub2"
date: 2010-08-14
forum: General Help
---

### Post by kanukatchit on 2010-08-14
I setup Wubi 32 bit on my desktop AMD 64 with three drives SCSI (winXP), SATA (ubuntu), IDE

got it up and running and ran update on Ubuntu. On Update GRUB2 asked to update mapping to all drives and I said yes. After this point havent been able to boot into either Winxp or ubuntu

Got in with live cd and tried to mount the Ubuntu drive to boot. But after mount it reboots to grub command prompt. I need to run 'update-grub' to regenerate grub.cfg but cannot seem to do it ?

I get is error probe:.. /dev/sda mounted ?

how should i go about recovering

---

### Post by bcbc on 2010-08-14
> **kanukatchit said:**
> I setup Wubi 32 bit on my desktop AMD 64 with three drives SCSI (winXP), SATA (ubuntu), IDE

got it up and running and ran update on Ubuntu. On Update GRUB2 asked to update mapping to all drives and I said yes. After this point havent been able to boot into either Winxp or ubuntu

Got in with live cd and tried to mount the Ubuntu drive to boot. But after mount it reboots to grub command prompt. I need to run 'update-grub' to regenerate grub.cfg but cannot seem to do it ?

I get is error probe:.. /dev/sda mounted ?

how should i go about recovering

You need to restore the bootloader(s). When you selected to install grub to each drive from wubi, it installed grub (but since grub can't directly load a wubi install, this will never boot).

Usually with wubi you need the windows bootloader. So restore it using the following howto: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (sroll down to instructions for XP).

You can also use lilo (in a form similar to windows) - which can be installed from a live CD (useful if you don't have windows disks). You can safely ignore the warnings it shows after entering the first command, and then before entering the second, make sure /dev/sda is the drive you boot from.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

You indicate you have an ubuntu install on the second drive - is this a proper installation or are you referring to the wubi install? If it's a direct install, you probably need the grub bootloader installed. I'm not really certain from your description, so if you aren't either, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by kanukatchit on 2010-08-14
Solved it

booted into using live cd ubuntu 10.4
then use

sudo fdisk -l 

to find where your windows partition is loaded

then use

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

replace /sda with your windows drive and it will restore the mbr for windows

used this thread

[http://ubuntuforums.org/showthread.php?t=1549194](http://ubuntuforums.org/showthread.php?t=1549194)

---

### Post by kanukatchit on 2010-08-14
Thank you for the reply bcbc

I did exactly as you mentioned for lilo and it worked. lilo recovered my windows beautifully. 

I did use Wubi and like you mention grub did not recognize the drive as a linux drive. so my question is does grub not takeover when you install with Wubi ? isnt this a major fyi... for new installations, because wubi makes it so easy to install anywhere. maybe i am missing something.

i am going for a full install from live cd, any idea how can transfer my existing wubi installtion to a full hard disk installtion ? 

thanks again

---

### Post by bcbc on 2010-08-14
> **kanukatchit said:**
> Thank you for the reply bcbc

I did exactly as you mentioned for lilo and it worked. lilo recovered my windows beautifully. 

I did use Wubi and like you mention grub did not recognize the drive as a linux drive. so my question is does grub not takeover when you install with Wubi ? isnt this a major fyi... for new installations, because wubi makes it so easy to install anywhere. maybe i am missing something.

i am going for a full install from live cd, any idea how can transfer my existing wubi installtion to a full hard disk installtion ? 

thanks again

See this to migrate a wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Regarding you questions on Wubi - wubi installs use a virtual disk (it's a file called root.disk). It boots using grub4dos via the windows boot manager. To get to windows it requires the windows boot manager in your drive MBR.

That screen where you installed grub is just where to put the bootloader, not the rest of grub which is still required. The problem is that the grub bootloader needs the modules on the root.disk, in order to loop mount it, so cannot function when installed direct to the MBR. 

In fact, wubi installs are supposed to prevent this from happening, but there is a bug: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

