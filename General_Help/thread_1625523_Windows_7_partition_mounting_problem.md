---
title: "Windows 7 partition mounting problem"
date: 2010-11-19
forum: General Help
---

### Post by 1101001101 on 2010-11-19
Dear Ubuntu community,

I stand here before you asking for help with a problem I've been struggling with for 2 days now already.

Anyway, a little history: This is a Windows PC which originally had windows vista installed to it, and I upgraded to windows 7.
This is all installed to my primary HDD of 250 GB so it contains one recovery partition made by windows, labeled as "Vista-loader" in grub, and all other space is occupied by my windows 7 partition , labeled as "Windows 7 loader" in grub.

About a year ago I installed a new internal hardrive of 1 TB and made 3 partitions which took up 500 GB, 100 GB and 150 GB respectively. They are all used for data storage. Now, you may have noticed I still have some remaining space on that second HDD, so, a couple of weeks ago I went and made me a 100 GB ext4 partition and a 2 GB swap partition and installed the new Ubuntu 10.10 desktop edition on the partition.

Everything went well and Windows 7 and Ubuntu co-existed together peacefully, but about 2 days ago, suddenly, while booting Ubuntu this ominous message appeared:

```
udevd-work[118]: '/sbin/blkid -o udev -p /dev/sda2' unexpected exit with status 0x000b
```This still occurs every time I choose Ubuntu in grub, and it happens before anything else. I had already disabled the graphical startup, 'cause I like to see what's going on at startup, but this happens before Ubuntu gets to do its stuff.

Anyway, after getting this message, I thought it had something to do with grub, so I decided to run "update-grub", but as a result, my "windows 7" option disappeared from the grub menu.

Totally panicking, I decided to mount the partition using the fstab file and then "mount -a", adding the line:

```
/dev/sda2 /media/windows7 ntfs defaults 0 0
```and this succesfully mounts the partition in Ubuntu under the label "Windows7" whereas normally it is called "Hard Disk", but this is because I defined it like that in the fstab I guess.

Also, I noticed while snooping around for the error that a lot of mounting and partition checking programs started throwing around "Segmentation Fault"s, and I have no idea what that means...

I have already tried fixing the MBR of the partition and even overwriting from Windows, restoring the normal bootloader and reinstalling grub, but to no avail...


If you have any tips as to run any helpful logging programs to get more debugging info, please shoot!
And if I forgot to mention anything relevant, please say so!


PS: as you can see, I have not edited my windows partition in the progress of installing Ubuntu, but when I do "grub-update" I get an error saying something about sectors 32 and 33 occupied by FlexNet, and after that the install reports "No errors", which I find pretty strange, but haven't really paid attention to, since everything used to work fine, so I guess it's not Grub that is the problem...

PPS: Also, I have no idea if the problem lies in Windows itself or Ubuntu, but I can't remember making big changes to the file systems in either of them.

---

### Post by dino99 on 2010-11-19
try to desactivate FlexNet with msconfig into w7

about grub2:

sudo grub-mkconfig
sudo update-grub

---

### Post by searchfgold6789 on 2010-11-19
In the boot process, Ubuntu has to mount all of your partitions using their UUID, which is a small handful of hexadecimal numbers that uniquely identify the file system. If they are not specified in the fstab, and are replaced by /dev/sda2 or something, then instead of just mounting the UUID's, it has to find out the UUID's of the filesystems and then mount them.

This is where your problem appears to lie.

To specify the UUID, replace "/dev/sda2" in your fstab with "UUID=<the uuid of the filesystem>"

To find out what to replace <the uuid of the system> with, go into any terminal windows and type in ```
sudo blkid
```

I hope this solves your problem.
 - search

---

### Post by 1101001101 on 2010-11-19
@dino: Quick question, I tried the grub-mkconfig, does this do the same as update-grub, but instead print it to the terminal too?
Going to try and deactivate and then install grub again, will post results!

@search: Well, I know that, but the fstab seems to be working fine as is, because before, it didn't contain my entry and wasn't needed apparently, but now it mounts the partition after booting just fine, also, when I use "sudo blkid" I just get "segmentation fault', like I mentioned before...

---

### Post by dino99 on 2010-11-19
> **1101001101 said:**
> @dino: Quick question, I tried the grub-mkconfig, does this do the same as update-grub, but instead print it to the terminal too?
Going to try and deactivate and then install grub again, will post results!

@search: Well, I know that, but the fstab seems to be working fine as is, because before, it didn't contain my entry and wasn't needed apparently, but now it mounts the partition after booting just fine, also, when I use "sudo blkid" I just get "segmentation fault', like I mentioned before...

run both commands one by one (after flexnet deactivation)

*** about fstab: it only need /home & swap, the others are automatically mounted "on demand" with the installed mountall package (its automatic, dont follow oldish erroneous config)

---

### Post by searchfgold6789 on 2010-11-19
Whether or not the filesystems are mounted automatically now, adding the UUID to fstab will eliminate the blkid process that occurs on startup, which is segfaulting as mr. binary just proved ;) If blkid were working, this would not be an issue at all and just /dev/sda2 in the file would work perfectly. Mountall still has to use blkid by the way.

With this many segfaults, and so many errors in this many areas in your system, it has led me to believe that it is a hardware problem or something, and is not fixable by just editing a file, or reinstalling a package or something. You probably should examine your installation disk for errors, check the downloaded iso, test your memory, or ShipIt a CD at this point.

---

### Post by 1101001101 on 2010-11-19
Already did memcheck yesterday, no errors, tried everything on the recovery disk, strange thing is, windows acts like nothing is wrong, except for occasionally a chkdsk request after having fooled around with the disk in Ubuntu...

I removed the fstab entry, so now the drive just doesn't show up in the places menu, and still the blkid segfaults, and I don't know the uuid of the partition, but I don't suppose that's quite relevant?

So, it's either a blkid error or the whole prtition is messed up? 'Cause I did every check on the partition possible, and everything reports it's healthy...

Also, disabling flexnet didn't remove it from bootsector, so I guess it's installed there for some program which I can't identify, but Grub is also installed on sdb, my second harddrive, so I guess that's no problem either?

---

### Post by searchfgold6789 on 2010-12-06
You might want to install the GRUB bootsector to replace that of flexnet, because you can't just "remove" a boot sector as far as I understand, without using a very special bios tool that I encountered some years ago.

If it is a blkid error, then you might still be able to fix it.
Boot into the live CD and type in "blkid" in the terminal. Then edit the entry in your fstab so that /dev/sdb1 is now UUID="whatever-your-uuid-is".

Ubuntu only boots from UUID's. If no UUID is specified in your fstab, it will take the /dev/sdb2 that it thinks is your system hard disk partition, and run blkid to find out the uuid, and then boot from that.

So I am thinking if you specify your uuid, it will not try to find it out for itself on boot.

---

