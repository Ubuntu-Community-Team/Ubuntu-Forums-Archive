---
title: "Sos!"
date: 2006-05-13
forum: General Help
---

### Post by cyber_alex on 2006-05-13
**Help me!**

I was currently running WinXP when I decided to install Ubuntu. The installation noticed that I already had WinXP installed and installed support for dual-boot.
**I installed Ubuntu on a partition on an extern harddrive.**

But know, after the installation, when I try to boot my computer, I get an error from the bootloader (I think it's called GRUB). The error says: '**Error 5**'.

I've also tried to disconnect the extern harddrive and boot, but then I get an '**Error 21**'. (I think it was 21).

I've now booted my computer from a Ubuntu Live-CD. That's how I'm able to write this.
[B]
PLEASE HELP ME![/B]

//Alex

---

### Post by dsokus on 2006-05-13
[QUOTE=cyber_alex]**Help me!**

I was currently running WinXP when I decided to install Ubuntu. The installation noticed that I already had WinXP installed and installed support for dual-boot.
**I installed Ubuntu on a partition on an extern harddrive.**

But know, after the installation, when I try to boot my computer, I get an error from the bootloader (I think it's called GRUB). The error says: '**Error 5**'.

I've also tried to disconnect the extern harddrive and boot, but then I get an '**Error 21**'. (I think it was 21).

I've now booted my computer from a Ubuntu Live-CD. That's how I'm able to write this.
[B]
PLEASE HELP ME![/B]

//Alex[/QUOTE]
Hmmm.... [http://www.uruk.org/orig-grub/errors.html#stage2](http://www.uruk.org/orig-grub/errors.html#stage2) gives a list of GRUB error messages in Stage 2... 

5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.


I would first definitely try to check if in my BIOS it is set right ("boot from hard disk"), just in case... Otherwise maybe you need to do a partitioning of your external hard drive? 

I am also relatively new to this so unfortunately that's all I can suggest off the top of my head right now.... Good luck!

---

### Post by cyber_alex on 2006-05-13
Okey, please come with more help...I'd like to be able to boot my WinXP and Ubuntu.

---

### Post by dsokus on 2006-05-13
One more thing - I think you can get GRUB to display the options and allow you to boot into Windows by going in to /boot/grub/menu.lst - at the very end, include

```

title Windows
root (hd0,1)
makeactive
chainloader +1
```

The "root" bit tells where your OS is going to be booted from: "hd0" is hda, "hd1" is hdb; and the partition numbers start from partition 1 = 0, partition 2 = 1. So for example (hd0,0) is 'hda, partition 1', (hd1,1) is disk 'hdb, partition 2'. The partition in my example is hda2.

But don't boot Windows. You don't need to. :p

---

### Post by dsokus on 2006-05-13
[QUOTE=cyber_alex]Okey, please come with more help...I'd like to be able to boot my WinXP and Ubuntu.[/QUOTE]
Get a terminal window. Type after the $: 

```
sudo gedit /boot/grub/menu.lst
```

Type your password. Edit the file as I said in the earlier post and save... When you reboot, Windows is supposed to be on the list. 

Before you restart, though, can you tell us what kind of partitions you have? Go to System->Administration->Disks, they are supposed to be there...

---

### Post by Herman on 2006-05-13
Here's the most popular how-to on installing Ubuntu on an external USB drive: [http://www.ubuntuforums.org/showthread.php?t=80811&highlight=dabrugo](http://www.ubuntuforums.org/showthread.php?t=80811&highlight=dabrugo)

To get you booting Windows at least, again for now, why not try out [GAG Boot Manager]("http://gag.sourceforge.net/")? Here's some easy information on how to use it: [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
That should help you, I hope, Regards, Herman

---

