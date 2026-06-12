---
title: "EDD information not available."
date: 2010-04-28
forum: General Help
---

### Post by kylegio on 2010-04-28
Just working a long on a program, have spent HOURS working on it, go to commit and my screen fades to black then i get a blinking cursor in top left of screen, couldnt recover from it had to hard reboot. get past grub, just the blinking cursor... waited 10 mins or so no change. boot in recovery mode, it halts boot and the last 2 lines are 
1.018839] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
1.018898] EDD information not available.


wont boot at all. i cant really find out anything about this on google etc, can someone please help me figure out whats going on?


kyle

---

### Post by duleorlovic on 2010-06-17
I have also a problem with booting Ubuntu 10.4.
I dont remember that I have changed anything in configuration, but today, after restarting Ubuntu, it wont get up. Just few lines (last one is "EDD information not available") on black screen.
I am very sad that I have problem with ubuntu.

---

### Post by maluka on 2010-07-07
I have this exact same problem. Has anyone been able to find a solution for it?

---

### Post by jschodde on 2010-07-12
Same problem here on a new PC that I built.

Specs:
mobo: msi **[p43-c51]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813130252")** + intel core 2 duo e8400 processor
graphics: **[msi n250gts]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127495")** (nvida chipset)
sata 1: intel 80gb ssd (brand new - never formatted)
sata 2: wd caviar black 500gb (new)

Several lines above this error message i see "please boot with i8042.nopnp"...not sure what that means yet.

---

### Post by jschodde on 2010-07-12
Aha! In my case, I had forgotten the SPDIF coax from the video card to S/PDIF (jsp1) on my mother board! I can now run Ubuntu from my CD or USB before I install it.

Next!...

---

### Post by jschodde on 2010-07-12
Crap, it worked one time only. Now I'm back to the same problem.

---

### Post by timbuckto on 2011-10-13
I don't know if you've found a solution to this yet, but this error seems to be an issue with using anything other than AHCI for the bus control on the motherboard.  I changed my dell to use AHCI instead of the default, and the system booted up without any problems.

Dell Optiplex 760 (2007)
Core 2 Duo 2.56GHz
4GB Ram
Installing: Xubuntu 11.04

---

### Post by freekb0y on 2011-10-31
I don't know if this information will be helpful but after a fresh  install of Ubuntu 11.10 I would encounter the same issue.  EDD, which is  enhanced disk drive, is something that the BIOS sometimes utilizes for  legacy purposes, and allows for the linux kernel to find the OS on the  correct drive or partition.  It was added in Linux kernel 2.6 etc (This  is all from memory so bare with me).  I had the same issue when booting  off a live cd so I went through all the command options that are on the  boot cd and found the if I turn on EDD and nolapic I could properly  boot.
       Using this information I went to the Grub menu and  edited the kernel line.  I removed the quiet splash and terminal handoff  statements and added edd=on and nolapic.  I am not sure if this is  going to work for you guys but I would at least try turning edd on this  may help

---

### Post by lordmayo on 2012-04-24
> **freekb0y said:**
> I don't know if this information will be helpful but after a fresh  install of Ubuntu 11.10 I would encounter the same issue.  EDD, which is  enhanced disk drive, is something that the BIOS sometimes utilizes for  legacy purposes, and allows for the linux kernel to find the OS on the  correct drive or partition.  It was added in Linux kernel 2.6 etc (This  is all from memory so bare with me).  I had the same issue when booting  off a live cd so I went through all the command options that are on the  boot cd and found the if I turn on EDD and nolapic I could properly  boot.
       Using this information I went to the Grub menu and  edited the kernel line.  I removed the quiet splash and terminal handoff  statements and added edd=on and nolapic.  I am not sure if this is  going to work for you guys but I would at least try turning edd on this  may help

freekb0y if you lived in New York I SWEAR I would buy you lunch OR dinner. Ubuntu Oneiric stopped loading about a week ago and nothing has worked... Believe me I've tried everything and even attempting an install didn't work because of this problem.

THANK YOU!!

---

### Post by tortilaman on 2012-06-02
> **freekb0y said:**
> I don't know if this information will be helpful but after a fresh  install of Ubuntu 11.10 I would encounter the same issue.  EDD, which is  enhanced disk drive, is something that the BIOS sometimes utilizes for  legacy purposes, and allows for the linux kernel to find the OS on the  correct drive or partition.  It was added in Linux kernel 2.6 etc (This  is all from memory so bare with me).  I had the same issue when booting  off a live cd so I went through all the command options that are on the  boot cd and found the if I turn on EDD and nolapic I could properly  boot.
       Using this information I went to the Grub menu and  edited the kernel line.  I removed the quiet splash and terminal handoff  statements and added edd=on and nolapic.  I am not sure if this is  going to work for you guys but I would at least try turning edd on this  may help

You sir are my hero. This ends weeks of frustration.

---

