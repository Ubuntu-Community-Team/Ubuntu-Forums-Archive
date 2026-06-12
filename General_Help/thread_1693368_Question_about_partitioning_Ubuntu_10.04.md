---
title: "Question about partitioning Ubuntu 10.04"
date: 2011-02-22
forum: General Help
---

### Post by jacatone on 2011-02-22
I copied my installation of Ubuntu 10.04 to another bigger HDD because my existing drive was failing. Using Gparted and made the new Ubuntu partition 100GB and partitioned another 100GB with ext4 as a backup. But I can't seem to see this second partition anywhere. Did I do something wrong? Thanks.

---

### Post by SeijiSensei on 2011-02-22
Did you format the partition with mkfs?  Did you mount it into the filesystem either with the "mount" command or by an entry in /etc/fstab?

---

### Post by jacatone on 2011-02-22
No, how do you do that?

---

### Post by SeijiSensei on 2011-02-23
First you need to create a "mount point" for the new filesystem.  This is really nothing more than an empty directory.  By convention, these typically are placed under /media.  

We also need to know where the new partition is.  From your description it's on the same drive as the root of the Linux filesystem, so probably it's on the disk that Linux calls "/dev/sda."  Each partition has a separate number.  If there was one partition before, and you added a second, the first one is called "/dev/sda1" and the new one "/dev/sda2".  Finally, let's suppose you call the mount point  "/media/mystuff".  Then you'd proceed as follows:

```

sudo mkdir /media/mystuff
sudo chmod 0755 /media/mystuff
sudo mkfs -t ext4 /dev/sda2
sudo mount /dev/sda2 /media/mystuff

```

That will mount the filesystem for the current session, but to make it permanent you'll need to edit (as root with sudo) the file /etc/fstab. Add a line at the bottom that reads:

```
/dev/sda2     /media/mystuff     ext4     defaults     0 0
```

Now it will be mounted automatically when you reboot.

---

### Post by wiggly81 on 2011-02-23
i have done this in the past but i found that now and then i would reboot and /dev/sda1 would have changed to /dev/sda2 or other but wasnt always the same so when booting i would get can not mound /dev/sda so what i did was search the net a bit with my problem, i came to 1 page which gave me some info on using UUID instead of /dev/sda1 since changing to this method i have not had a single problem...

to get the UUID you would need to open terminal and type 
```
sudo blkid
```this will list all partitions and there UUID

next edit /etc/fstab as previous post but change /dev/sda2 to the UUID
```
UUID=???????????????? /media/mystuff ext4 defaults 0 0
```the ?'s being the number.

hope this helps

---

### Post by SeijiSensei on 2011-02-23
UUIDs are a good idea, especially if you're using removable media like USB drives.  I thought it best to start off more simply in the OP's case.  If he can get the partition formatted and mounted, then UUIDs in /etc/fstab are the next hurdle.

---

### Post by wiggly81 on 2011-02-23
my point was i done it the other way /dev/hda2 with a internal hard drive and was forever getting the unable to mount problem on startup so i thought it would probably save yet more problems in the future, i do agree it is easyer to learn the /dev/sda2/ option first but i think its always good to know there is a "more stable" way to do things from the get go and save any further problems.
i do agreed it is easier to understand what is actually happening with /dev/sda2/ thou.

---

