---
title: "Need some help with partitioning"
date: 2006-06-12
forum: General Help
---

### Post by grte on 2006-06-12
Okay, so I currently have a 274 GiB partition holding everything.  It's less then half full.  What I want to do is take all the empty space, throw all my personal files on it, and mount that partition as /home.

I'm using the gParted live CD to resize the partition.  It's ext3, and when I try to resize it, it gives me an error reading "please do e2fsck /dev/sda1 first."  So I do that, try again, and get the exact same error.

Anyone have any ideas what may be causing this?

---

### Post by aysiu on 2006-06-12
[QUOTE=grte]
I'm using the gParted live CD to resize the partition.  It's ext3, and when I try to resize it, it gives me an error reading "please do e2fsck /dev/sda1 first."  So I do that, try again, and get the exact same error.[/QUOTE] I don't know what that error is, but this tutorial may help you create a new /home partition (after you sort out that error):
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by grte on 2006-06-12
Okay, one more bit of information after reading that tutorial:  When trying to create another partition, I was trying to create a second primary partition rather than a logical partition - Might that be what's causing my problem?

[Edit] On second thought, I don't see why it would be.  The issue is occuring while trying to resize the partition, not in the creation of the new one.

---

### Post by aysiu on 2006-06-12
You say you already tried *e2fsck*. Did it do anything...? Did it seem to catch/correct any errors?

---

### Post by grte on 2006-06-12
[QUOTE=aysiu]You say you already tried *e2fsck*. Did it do anything...? Did it seem to catch/correct any errors?[/QUOTE]

No...It just ran through the process and didn't come up with any bad sectors, or anything.

I think I might give it a try with QTParted on a knoppix live CD.  It may just be the gparted live CD acting up on me.

---

### Post by grte on 2006-06-12
No luck with QTParted so far.  It won't even let me attempt to resize the partition.

---

### Post by grte on 2006-06-12
Okay, tried gParted on the Dapper CD.  It didn't work again, but this time it told me it failed because the partition was mounted.  It wasn't.  In fact, not only was it not mounted, I was unable to mount it when I tried.

Grr...

---

### Post by aysiu on 2006-06-12
I've had no problems with GParted on the new installer, but that's just me. I've read numerous accounts on these forums of people having trouble with the GParted that comes with the Dapper live CD.

People have had much better luck with the Alternate Install CD (the text-based partitioner). I've never had any problems with DiskDrake (which comes with the PCLinuxOS live CD), but most people are hesitant to download another distro just to do partitioning.

---

### Post by grte on 2006-06-12
[QUOTE=aysiu]I've had no problems with GParted on the new installer, but that's just me. I've read numerous accounts on these forums of people having trouble with the GParted that comes with the Dapper live CD.

People have had much better luck with the Alternate Install CD (the text-based partitioner). I've never had any problems with DiskDrake (which comes with the PCLinuxOS live CD), but most people are hesitant to download another distro just to do partitioning.[/QUOTE]

Doesn't seem to be a problem with gParted specifically, though.  QTParted didn't work either, and gParted didn't work on either the dapper CD or the gparted live CD.

Oh well, I think I'll just back up my data, wipe the whole partition, and start anew.  I wanted to do a fresh install of dapper, anyways.

---

### Post by talowe on 2006-06-12
[QUOTE=grte]Doesn't seem to be a problem with gParted specifically, though.  QTParted didn't work either, and gParted didn't work on either the dapper CD or the gparted live CD.

Oh well, I think I'll just back up my data, wipe the whole partition, and start anew.  I wanted to do a fresh install of dapper, anyways.[/QUOTE]

Try

```
sudo swapoff -a
```

to disable swap device (which is probably /dev/sda1, with /dev/sda0 being you root partion, the one you want to resize).

If any partition is busy, gparted may not want to do anything to the harddrive.

---

### Post by grte on 2006-06-12
[QUOTE=talowe]Try

```
sudo swapoff -a
```

to disable swap device (which is probably /dev/sda1, with /dev/sda0 being you root partion, the one you want to resize).

If any partition is busy, gparted may not want to do anything to the harddrive.[/QUOTE]

I'm afraid that didn't work either.

I am getting this output from the terminal:
```
dumpe2fs 1.38 (30-Jun-2005)
Error reading inode 620.
Error reading inode 660.
Error reading inode 1269.
Error reading inode 2019.
Error reading inode 3489.
Error reading inode 9280.
Error reading inode 10742.
Error reading inode 10750.
Error reading inode 10753.
Error reading inode 10758.
Error reading inode 10765.
Error reading inode 10781.
Error reading inode 10782.
Error reading inode 10785.
Error reading inode 10786.
Error reading inode 10787.
Error reading inode 11391.
Error reading inode 11564.
Error reading inode 11573.
Error reading inode 12197.
Error reading inode 12419.
Error reading inode 12581.
Error reading inode 12839.
Error reading inode 12841.
Error reading inode 12844.
Error reading inode 12845.
Error reading inode 12890.
Error reading inode 12891.
Error reading inode 12893.
Error reading inode 15383.
Error reading inode 18533.
Error reading inode 18534.
Error reading inode 18535.
Error reading inode 19555.
Error reading inode 20075.
Error reading inode 20077.
Error reading inode 22016.
Error reading inode 22112.
Error reading inode 22113.
Error reading inode 22114.
Error reading inode 22115.
Error reading inode 22116.
Error reading inode 30649.
Error reading inode 37779.
Error reading inode 37890.

```

---

### Post by talowe on 2006-06-13
[QUOTE=grte]I'm afraid that didn't work either.

I am getting this output from the terminal:
```
dumpe2fs 1.38 (30-Jun-2005)
Error reading inode 620.
Error reading inode 660.
Error reading inode 1269.
Error reading inode 2019.
Error reading inode 3489.
Error reading inode 9280.
.
.
.

```[/QUOTE]

Excuse my numbering  in earlier post, was thinking of grub:oops: 

Seems like a lot of errors, have you tried
```
sudo e2fsck -f [your root device]
```
to force checking?

---

