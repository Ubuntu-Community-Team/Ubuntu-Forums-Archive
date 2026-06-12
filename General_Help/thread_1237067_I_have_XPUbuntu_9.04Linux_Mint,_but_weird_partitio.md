---
title: "I have XP/Ubuntu 9.04/Linux Mint, but weird partition problem?"
date: 2009-08-10
forum: General Help
---

### Post by NiacinFlush on 2009-08-10
Ok, so I first had XP. Then I installed Ububtu 9.04. Gave that about 20GB partition. Then I installed Linux Mint, gave that about 18GB too, but now when I booted to Ubuntu, I have about <1 GB of hard drive partition space!

I have no idea how that happened. Did linux mint gobble it up or something? I will attach the screen shot of the partition image I took. Somehow the Ubuntu parition is locked, and I cannot resize it to the left to give more HD space. 

/SDA2 should be XP

/SDA5 should be Mint

/SDA7 should be Ubuntu
_________________

I have no idea what SDA1 and SDA 8 are :confused:

Thank you for any help! :)

---

### Post by hibliss on 2009-08-11
SDA1 may be a recovery partition from Acer. It is formatted NTFS, so that would not surprise me. If you did not create it, this is most likely the case. You can mount it and see what is on it. If it is Windows stuff, you can safely wipe it as long as you have Windows disks to restore with in case on emergency (and it is Windows, so there will always be an emergency ;))

SDA8 is a Linux swap partition, like a Windows paging file. It is actually rather small IMO, so was most likely auto created by Mint.

The reason you cannot resize the Ubuntu partition is because it is mounted (you must be booted in to Ubuntu). To fix this, boot in to Mint and run gparted from terminal:

```
sudo gparted
```

Or you can run a liveCD to resize both partitions at once. Mounted partitions cannot be resized.

---

### Post by starcraft.man on 2009-08-11
SDA1 is a service partition installed by an OEM manufacturer and likely required for reinstall of OEM windows, I advise you NOT touch that unless you no longer want windows or have alternative means of install.

sda8 is your swap space, like paging in Windows. It's fine though a bit small.

The rest of your partition table is as follows:
sda1 > service partition
unallocated > 502 MB
sda2 > XP likely since NTFS
unallocated > 22 GB
sda3 >Extended space - 22 GB
sda7 > Root partition -2 GB
sda8 > swap - 174
sda5 > /home - 18 GB

There's lots of problems here. First the lock I imagine is because your trying to edit partitions that are currently in use and mounted, a no no. Like trying to pull a chair out from under ya while your standing on it. Second, the unallocated space partitions are too large and waste almost 23 GBs of your partitions, this should be merged into existing partitions or made into new ones. Next, your root partition at 2 GB is WAY too small. As you can see your base install filled it up and you'll never be able to install more programs. The root needs at least 5-10 GBs for an average user. Most people could get away with just 6 or so as long as they don't go on a binge and install every program in repos. Also, since your installing mint and ubuntu consider using a unified home partition. Make one for the first you install, and then when your installing the second, tell the partitioner to do a custom selection and instruct it to mount the home partition and NOT format it. If you do this, use a different username for each, each will get own folder.

You need to read this gparted [documentation]("http://gparted.sourceforge.net/documentation.php"). Start with general, and read down. By the end, I think you'll understand much better how to partition. You'll need to clean up the mess. I can give you step by step, but I believe it's better if ya learn for future. I'll make these notes however:

When your done reading, boot a live CD and open the partitioner. Ensure all information VITAL to your life is backed up off this drive, not my responsibility, problems happen unexpected like power outages. Ensure no drives are mounted, and now your set to change partitions (by default none are, if they are they will be locked until unmounted). Now, to fix table do the following:

- Don't touch sda1.
- Use move and resize to move the free space unallocated to partitions ya want to move it to.
- Resize existing root (sda7) to at least 6 GB. Make a second partition also ext3 or 4, and that will be root for Mint or Ubuntu (the other install not sda7), whichever ya need. At least 6GB as well. 
- Increase swap to at least 500 mb. Then, remaining space can be put to home or merged somewhere else like XP.
- You may want to reconsider a reinstall of both one after the other after fixing partitions, simply instruct them to use existing partitions and format the roots but NOT home.

How this happened, is beyond me. I can only guess that you tried using guided partitioner maybe? Never liked em. Partitioning is serious business.

/end long explanation.

---

### Post by NiacinFlush on 2009-08-11
Ok, thank you got that awesome answer! I will let you know how it goes! :) It will take a while. Just resizing something takes about 1-2 hours.

---

