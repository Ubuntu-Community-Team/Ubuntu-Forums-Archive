---
title: "&quot;Disk has a few bad sectors&quot; Help me plz."
date: 2010-05-08
forum: General Help
---

### Post by Buying_Some_Time on 2010-05-08
I have a fairly new 100GB HD on my laptop and lately I've been getting a error when ever I boot up Lucid "Disk has a few bad sectors" and I want to know how I would go about fixing these sectors?

---

### Post by Ocxic on 2010-05-08
Replace the drive. Bad sectors are normally fixed automatically by the hard drives firmware without any intervention on your part.

if it's new it should be under warranty.

---

### Post by maury on 2010-05-08
Replace the disk is the best advice but if you are short on cash you might work around the problem by partitioning out the bad area and if you are lucky and it doesn't grow more bad spots, it may run a long time. Most of the time once a drive begins to go it just gets worse. On the other hand I had a 20 GB drive hat I used that way for years and finally just threw away. Is your bad drive under warranty, I have returned many bad drives over the years and gotten replacements but it takes a couple of months.

---

### Post by Buying_Some_Time on 2010-05-08
I have a quick question, if I back up my HD on to a external HD will that also back up my OS? Or will I have to reinstall it?

---

### Post by lmarmisa on 2010-05-08
The answer is that you don't need to reinstall your OS but only if you are able to make a reliable backup.

Maybe you need clonezilla:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

I recommend the stable Ubuntu based version.

Best regards,

Luis

---

### Post by seeker5528 on 2010-05-08
> **Buying_Some_Time said:**
> I have a quick question, if I back up my HD on to a external HD will that also back up my OS? Or will I have to reinstall it?

Typically if there are bad sectors I would use ddrescue to clone the drive 'ddrescue input output'.

Your external drive would have to be equal or larger than the internal drive to go from device to device.

Assuming you don't already have stuff on the external drive you want to keep... If your internal drive shows up as sda and the external as sdb it would look like this.....

```
ddrescue /dev/sda /dev/sdb
```

Your input or output can be a file as well, in which case you would have to have enough free space on the external drive to create an image the size of your internal drive, if I remember right the file has to exist first, I use touch to create empty files.....

```
touch /path/to/location/laptop.img
ddrescue /dev/sda /path/to/location/laptop.img
```

Clonezilla isn't designed to recover from errors, so if it detects any issues during it's pre-clone checks or runs into an error while cloning, it's going to bail on the operation.

Typically I use [System Rescue CD](http://www.sysresccd.org/Main_Page) for these things. If you need to create a image file of the hard drive, and are less familiar with the commands to mount/umount stuff from the command line, you might prefer [RIP](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/), the X session RIP provides has a menu item that makes mounting/unmounting partitions a snap.

Later, When you are ready to copy the stuff back you just reverse the process using the device name of the external drive or name of the image on the external drive as the input and the device name of the internal drive as the output.

Once you have everything copied to the replacement drive, rebooted, run fsck to fix things if necessary, then if the replacement drive is bigger than the original you can use gparted to adjust the size of the partitions.

Later, Seeker

---

### Post by Buying_Some_Time on 2010-05-08
Okay, I see. Thank you seeker for your help.

---

