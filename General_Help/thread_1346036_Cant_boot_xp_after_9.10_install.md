---
title: "Cant boot xp after 9.10 install"
date: 2009-12-04
forum: General Help
---

### Post by DJack on 2009-12-04
First post :D
Reason for post :cry:

I'm a complete newbie but tonight I installed Karmic Koala on my XP machine via a cd.  It appeared to go well then I restarted the machine meaning to boot XP. I got the XP ain't well do you wish to continue in normal mode or (the various) safe modes - none worked...HELP (please)

---

### Post by JBAlaska on 2009-12-04
Did you get Ubuntu running on your Harddrive? Can you boot into Ubuntu now?

If not, please boot from the LiveCD and go to System, Administration, Gparted and have a look at your HD partitions.

Let us know.

---

### Post by ComputerHermit on 2009-12-04
xp The message is XP ain't well? Microsoft ain't well in general when. I use to duel boot I had a another hard drive to put. Ubuntu on and I had XP on another. You might have to use the XP CD to delete the linux partitions and then run. Fix boot and fix mbr from the XP CD. But what do I know I really don't know what is the problem. Sounds like a boot problem!

---

### Post by DJack on 2009-12-04
JB I did get Ubuntu on my HDD and I'm currently using it on said machine.  I'll try the live CD... thanks

---

### Post by JBAlaska on 2009-12-04
When you get the LiveCD booted, run Gparted as I mentioned above and look for your NTFS partition, hopfully it is still there.

---

### Post by NFblaze on 2009-12-04
What happens when you click Start Normally, Last Known Good Config, Safe Mode, etc....

---

### Post by JBAlaska on 2009-12-04
Yes the exact message NTLDR is giving will help.

Also in the LiveCD open the terminal and post the output of:
```
sudo fdisk -l
```

---

### Post by DJack on 2009-12-04
@ NFBlaze  It appears to start loading until it gets to *system32*mups.sys or something like that.  Then it goes to a restart

@JBAlaska GParted shows my NTFS "boot" drive it also shows an "unallocated" drive which is a bit of a surprise to me and will probably be the cause of my drama.  sudo fdisk to follow

---

### Post by DJack on 2009-12-04
... as requested


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4a0fe34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         574     4610623+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         575       12468    95538555    7  HPFS/NTFS
/dev/sda3           16159       18260    16884315    7  HPFS/NTFS
/dev/sda4           18261       24792    52468290    5  Extended
/dev/sda5           18261       24519    50275386   83  Linux
/dev/sda6           24520       24792     2192841   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20043a73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         574     4610623+   b  W95 FAT32
/dev/sdb2             575       40539   321018862+   7  HPFS/NTFS
/dev/sdb3           40540       81887   332127810    7  HPFS/NTFS
/dev/sdb4           81888      121601   319002705    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by DJack on 2009-12-04
I'll leave this for now.  In the New Year I'll track down my XP CD try and try the Hermits suggestion.  After that, if it does not play ball, I'll call on you gentlemen again.:biggrin: Thank you all.

---

### Post by NFblaze on 2009-12-04
You might have the exact same problem I had back in October with the infinite rebooting which I made a bug report over on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/458506"). 
I originally thought it was caused by not mounting my ntfs partitions when I boot ubuntu, but that wasnt it. I was stumped. I think the devs were stumped. It no longer does this anymore, but I dont know what I did (besides standard updates) it seemed to just fix itself. As of now my current grub2 is 1.97 beta4 1ubuntu4. So next year try using the latest version of grub2.

---

### Post by JBAlaska on 2009-12-04
> **DJack said:**
> I'll leave this for now.  In the New Year I'll track down my XP CD try and try the Hermits suggestion.  After that, if it does not play ball, I'll call on you gentlemen again.:biggrin: Thank you all.

ComputerHermit's method will repair your MBR (Master boot record) back to it's original state, but you will no longer be able to boot Ubuntu.

If you want to mess with it further, you'll need to boot Ubuntu from your HD and do this from a terminal:
```
sudo os-prober
sudo update-grub
```

Then try to boot xp, if it still will not boot, try to post the exact error text you see.

---

### Post by DJack on 2009-12-04
[

---

### Post by DJack on 2009-12-04
desktop:~$ sudo os-prober
/dev/sda1:Windows NT/2000/XP (loader):Windows:chain
/dev/sda2:Microsoft Windows XP Home Edition:Windows1:chain
/dev/sdb1:Windows NT/2000/XP (loader):Windows2:chain
desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
Found Windows NT/2000/XP (loader) on /dev/sdb1
done
jason@jason-desktop:~$ 


I'm off to bed now. Thanks again.

---

### Post by JBAlaska on 2009-12-05
This one should be your XP:
```
Found Microsoft Windows XP Home Edition on /dev/sda2
```

---

