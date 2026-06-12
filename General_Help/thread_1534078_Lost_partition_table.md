---
title: "Lost partition table"
date: 2010-07-19
forum: General Help
---

### Post by Ubermench on 2010-07-19
The Machine: Acer aspire One, Vista/Netbuntu Dual boot, 32 bit. 2Gib RAM.  AFIK all updates on both OS are current and up to date.

Vista was native to the machine, installed Ubuntu then used GParted to shrink the Vista partition and create another Linux partition.  So far all is well. Moved a few files to new partition and upon reboot I noticed not only is the new partition "free" the whole drive is "unallocated". They show fine under testdisk and fdisk -l. I tried to repair using testdisk but the partition table STILL seems to be absent.
 
Being a netbook there's no option to run a live CD or the like as there is no CD/Dvd player.
Suggestions?

Many Thanks

---

### Post by S.R on 2010-07-19
I have experience with this problem but got me to thinking. If you could put the live.iso on a thumb drive you should be golden I would think of course you might have to twiddle in the BIOS for it to pick up the bios thumb drive

---

### Post by Ubermench on 2010-07-19
I have live Ubuntu on a thumb drive. but where do I go from there?

Engel

---

### Post by S.R on 2010-07-19
Turn computer on and access the bios (way to do so varies with models but F2 and Del keys seems to be vary popular gor getting you into your bios. The look for the boot tab and change the order to something like usb then hdd then cd. exit save it will reboot. While the power is down stick your thumb and it should boot of that.

---

### Post by Ubermench on 2010-07-20
yes, I've done that. It's how I installed in the first place. Pardon my newness but, how does that help fix my partition table?  I have no problem booting from the HD.

Engel

---

### Post by oldfred on 2010-07-20
Gparted does not like to mount NTFS partition that have the chkdsk flag set. Resizing the NTFS partition with gparted automatically sets the chkdsk flag. Boot Vista and run chkdsk. You will have to reboot to get it to run. normally you would run from windows CD but obviously you cannot.

---

### Post by Ubermench on 2010-07-26
sorry for the delay. I now have regular internet access!! I tried running chkdsk but it seems to want to check a "D" drive instead of "C".  I'm at a loss as to what to do. It boots fine  to either OS, it's just #*&$ irritating to not be able to use gparted.  

Engel

---

### Post by oldfred on 2010-07-26
Can you specify drive. If defaults to current if not specified.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

### Post by Ubermench on 2010-07-26
thanks, I'll be tryng that straight off and get back to you this evening.

Engel

---

### Post by Ubermench on 2010-07-26
Houston?? Ahh Houston, we have a problem.  chkdsk C: /r ran with no problem - however gParted -still- says the whole drive is unallocated. I -WAS- going to give you an fdisk -l log but apparently Vista has decided that fdisk is not a valid command or batch file and it does nothing in terminal (linux). Argh..

I'm beginning to think my best bet is to buy an external drive and back up all my M$ files, reinstall Ubuntu and move the M$ to an entirely different machine.

Engel

---

### Post by oldfred on 2010-07-26
fdisk is a linux command, linux commands do not work in windows.

In linux you often have to use sudo, if it has anything to do with the system.

```
sudo fdisk -l
```

---

### Post by Ubermench on 2010-07-28
fidsk is also a msdos command ([http://support.microsoft.com/kb/255867](http://support.microsoft.com/kb/255867)).  Anyway, I "solved" the problem by moving all the important data off the drive and reinstalling Ubuntu on the whole disk.  I -do- wish I knew how to fix it but (shrug). Thanks for the help, the good is that I learned a lot, like "don't adjust windows partitions in Linux" and a few other things LOL.  Thanks again Fred and co. I'm sure this isn't the last you'll see of me.

Engel

---

