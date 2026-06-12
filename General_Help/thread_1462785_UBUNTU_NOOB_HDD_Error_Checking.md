---
title: "UBUNTU NOOB: HDD Error Checking"
date: 2010-04-26
forum: General Help
---

### Post by curtisjwong on 2010-04-26
Is there an Ubuntu utility similar to the one in windows where you right click/select properties/tools/check disk?  How do you use it?

---

### Post by P4man on 2010-04-26
system > administration > disk utility.

---

### Post by Drenriza on 2010-04-26
what is it you want to exactly?

---

### Post by curtisjwong on 2010-04-26
Sorry if I wasn't clear enough.

Is there a way in Ubuntu to check the main file system on the hard drive for bad sectors and hopefully recover some of the data on them?  The way in windows to access it is to right click my computer/properties/ tools/ check disk for errors but I have no idea how to do the same in Ubuntu.

I tried googling it and I read about the fsck tool but I don't really understand how to use it.

---

### Post by P4man on 2010-04-26
For simple filesystem errors, just do like I wrote above, system > adminstration > disk utility. Select your partition and click "check filesystem".

To recover data from a damaged drive or badly damaged filesystem, boot from a livecd and install/run testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can run testdisk from an ubuntu livecd, you just need to install it first (in a terminal:
```
sudo apt-get install testdisk
```
)

Or download [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) and boot that.

You can run testdisk under windows as well, just make sure you are not running any OS on the disk you want to recover.

---

### Post by curtisjwong on 2010-04-26
Thanks for the quick replies.

So I'm opting for the first solution you described.  I've opened palimpsest disk utility and I've clicked on my primary file system but the program won't let me click the "check the file system" button (5th icon from the left).  What do I do?

---

### Post by P4man on 2010-04-26
Its your root partition! Its where ubuntu is installed upon, you cant check that from within that same ubuntu, it has to be unmounted. But why would you want to check it? Its automatically checked upon boot. Well actuallly its not, unless ubuntu has not been shut down properly or after each 30 boots its verified anyhow, so basically there is no need to manually check.

If for some reason you want to force a check upon the next boot, open a terminal and type

```
sudo touch /forcefsck
```

Type your password, and reboot. The root partition will be checked during the boot process upon next boot.

---

### Post by curtisjwong on 2010-04-26
Ah that makes sense.  will "sudo touch /forcefsck" automatically recover any bad sectors it finds?

Thanks for all your help, btw P4man I really appreciately it

---

### Post by P4man on 2010-04-27
actually, modern (less then 10 year old) drives will remap bad sectors all by themselves, mostly invisible to the OS and to tools like fsck or chkdsk. If they encounter difficulty reading or writing a sector they will mark them as bad, and the next time something tries to write to that sector, the drive's controller will relocate the sector to a spare one. No user intervention is needed here at all. 

You can check the status of your drive (number or relocated sectors, and sectors pending relocation as well as other data) using that disk utility and checking the SMART status.

The only time you will encounter "bad sectors" is when the drive ran out of spare sectors and is just marking them as bad with no way to remap them. If that happens, you dont need to run a disk utility to fix anything, you desperately need to replace the drive.

Palimpsest (disk utility) will warn you well in advance though as the drive starts degrading.

---

