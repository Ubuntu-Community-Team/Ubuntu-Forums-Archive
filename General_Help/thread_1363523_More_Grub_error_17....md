---
title: "More Grub error 17..."
date: 2009-12-24
forum: General Help
---

### Post by gfxguy on 2009-12-24
I haven't been able to find a solution on the many threads on the subject...

First of all, I want to say this all worked great up until I tried to install 9.10 from 9.04.  I got the grub menu, I could boot into Windows or Linux without any problems.  After I couldn't get 9.10 to work (again, because of grub), I reinstalled 9.04, but now can't get it to work correctly.

So, here's the situation (yes, it's complicated); I have two sata drives - one is Linux:

```
/dev/sda1   *           1        7781    62500851   83  Linux
/dev/sda2            7782       30401   181695150    5  Extended
/dev/sda5            7782        8267     3903763+  82  Linux swap / Solaris
/dev/sda6            8268       30401   177791323+  83  Linux
```

The other is the drive I used to "share" between Linux and Windows, sdb, it's got a single partition, sdb1.

I have a third IDE drive with Windows XP.  Linux sees this as sdc, it's got one partition (sdc1).  Now, here is the problem; without the IDE drive connected, the BIOS allows me to pick either of the two SATA drives for a boot device.

**When the IDE is connected**, the BIOS makes it the ONLY available drive to select to boot from!

So I've tried this using grub to set the root as (hd0,0) = sda1, but "setup" (hd2) = sdc.

It does not work.  Yes, grub can find stage1 on hd0,0.

So this is what I have now... if I disconnect the IDE drive, I get the Grub menu and can boot Linux.  If the IDE drive is connected, I get error 17.  If I use the XP boot disk to fixmbr on the IDE drive, I can boot Windows, but need to disconnect the IDE drive to boot Linux.

I hope it's clear...
sda = hd0 = SATA1 = Linux drive with sda1 = (hd0,0) as the boot partition.
sdb = SATA2 = shared NTFS drive
sdc = hd2 = IDE1 = XP drive.

I can't seem to install a valid grub configuration on sdc, and the BIOS will ONLY let me boot from an IDE drive when an IDE HDD is connected (the CDROM is IDE, too, but that doesn't seem to be a problem).

Yes, the BIOS sucks.  AMI on an ASUS board... incredibly stupid to limit me to IDE just because one is connected.  But I don't feel like buying a new MB or reinstalling Windows onto a SATA.

Yes, I've tried grub:

root (hd0,0)

It finds /boot/grub/stage1 on (hd0,0), I know this is correct.

setup (hd2)

Says it installs, but ultimately doesn't work.

At the same time, it seems like you can setup all your drives... hd0, hd1... as long as they all look at hd0 to find the grub data, then whichever one boots it should work (theoretically, I'd think).

Nothing seems to work.

TIA, and Merry Christmas.

---

### Post by BigCityCat on 2009-12-24
I really don't know much but maybe this could help.

[http://notroswell.com/etcetera/etceterakarmic/](http://notroswell.com/etcetera/etceterakarmic/)

---

### Post by Drakkenkill on 2009-12-24
Maybe you can help me with my cd burning problems i'vebenn trying to burn puppy linux and i've used brasero Gnomebaker and k3b and they all won't work i put a blank cd in and try to burn it and it always freezes or says unknown error all i wanna do is install puppy linux because karmic koala uses requires too much RAM got any ideas

---

### Post by running_rabbit07 on 2009-12-24
> **Drakkenkill said:**
> Maybe you can help me with my cd burning problems i'vebenn trying to burn puppy linux and i've used brasero Gnomebaker and k3b and they all won't work i put a blank cd in and try to burn it and it always freezes or says unknown error all i wanna do is install puppy linux because karmic koala uses requires too much RAM got any ideas

Please start your own thread.:)

---

### Post by oldfred on 2009-12-24
I converted to 100% Sata 3 years ago. Then I did plug in my ide drive to copy some data & it was not the boot drive but sdd.

With pata drives master/slave was set with jumpers or newer pata with the location on the cable. If you have two cables one for CD and one for hard drive what happens if you set pata drive to slave setting? I have not tried it, its just a guess.

You should be able to install grub to the pata drive and get it to boot. I prefer having an operating system on each drive and that drive's MBR have that system set to boot and  with Ubuntu as the first drive as it is easy to select other systems to boot. But I have seen many others with your issue where mixed sata and pata cause issues.

---

