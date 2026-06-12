---
title: "gparted filesystem mess"
date: 2009-12-18
forum: General Help
---

### Post by balta on 2009-12-18
Hi everybody!
I have an external harddisk that was partitioned in 2:
one (smaller) part was FAT32 (labeled XT), the other NTFS.

I moved the contens of the FAT32 part into the NTFS one.

Using gparted under Ubuntu 9.04:
First I deleted the FAT32 partition (wich was on the left).

Everything fine: on the left some unnalocated space on the right the big NTFS partition.

Then I started the moving\resizing of the NFTS one: I wanted it to take the entire hard disk so it had to be first moved to the left then grown.

Unfortunaltely during the "read-only" test (wich is made after the selection of the optimal blocksize) my (idiot) little sister pushed "cancel"...

The situation is now this:

gparted sees the hard disk is partitioned in 2: 
The right part is unnalocated and has the size that the unnalocated (on the left) had before the beginning of the process.
The left size is the big one but it's FAT32, labbeled XT and seem to be full of stuff (as full as it was before moving it) but when I try to browse it using nautilus I can only see one folder: the very same folder (which is way smaller than the size marked as used by gparted) that was in the initial FAT32 partition.

Please tell me there is a way to recover the data that gparted seems to see inside the partition!

Even without ubuntu, even using some commercial software: there was too much important data in there.

Thanks for your time: God bless you my savior!

.balta

---

### Post by audiomick on 2009-12-18
hi.
I am afraid I can't help all that much, but as far as I know, you should be able to get that back. As I understand you, you hadn't got to the stage of actually changing things. From what I understand of things, it should be just a matter of re-constructin the partition table or whatever it is called. The bit that knows where the partitions start and end, and what is in them.

Keep a cool head. I hope someone can be more helpful soon.

---

### Post by northern lights on 2009-12-18
Please post the output of```
sudo fdisk -l && blkid
```Thank you.

---

### Post by audiomick on 2009-12-18
Hallo again.
Look what I found:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Hope it helps.:)

---

### Post by balta on 2009-12-19
Huge thanks *audiomick *and *northern lights*, that's why I love Ubuntu and the Ubuntu community.

I'll post the command output and read through the article as soon as I get home (22 December, afternoon).

I feel far more confident now, big thanks again!

.balta

---

### Post by balta on 2009-12-20
Hi veryone!
I made it a bit earlier so I'm already here!
Here is the output from ```
sudo fdisk -l && blkid
```

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c4b3c4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19221   154390288+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           19222       19246      200812+  82  Linux swap / Solaris
/dev/sda3           19247       24321    40764937+  83  Linux



Disk /dev/sdf: 750.1 GB, 750156373504 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042c0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf2               1       65706   527775412+   7  HPFS/NTFS
/dev/sda1: UUID="8CACB0C9ACB0AED8" TYPE="ntfs" 
/dev/sda2: UUID="81acf489-7714-471b-a704-aca71df1d933" TYPE="swap" 
/dev/sda3: UUID="ecae136f-26cf-4f26-b46b-af4d50796a2a" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"
```

Personally I believe only the second half matters but just to be sure I posted both.
What now? Is it recoverable?

and

I read the article but I'm not sure if I must follow advices from the ***Lost Partition*** section or from the ***Data Recovery from damaged filesystem or drive*** one... any hint about which describes best my situation?

and

If the right one is *Lost Partition*, which of the 3 presented tools you advice me to use? (personally *testdisk* was the one that seems to me the most n00b friendly but now I just care about results so I can try "complex" programs ^^ )



Hoping to hear from you as soon as possible! 
Happy Holidays!

.balta

---

### Post by pogush on 2009-12-25
same mess here :oops:
have you tried yet? 
if yes, could you post the results?
if no, could someone keep on going the explanations? 
thx

---

### Post by balta on 2009-12-27
bump!

---

### Post by pogush on 2009-12-28
I bumb this too!

---

### Post by audiomick on 2009-12-28
Hallo.

First of all, I have never done this, so my opinion  is just that: an opinion and not expert advice.

After reading through the article I gave a link to, and a bit of associated stuff, I would be trying the following.

Run ddrescue to make a copy of the messed up HD to somewhere else.
Try testdisk, maybe on the copy. 

You should read up on these programs yourself to be sure that they really do what I think they do.

---

### Post by balta on 2010-01-01
Thanks for that! 
Maybe I'm just a bit dumb but making a copy of the hdd and working on it seems to me pure geniality :worship:
I'll get a new hdd as capable as the old and try to make the copy!
I'll post results here as soon as I can try this!

Huge thanks again|

---

### Post by balta on 2010-03-11
> **audiomick said:**
> Hallo.

First of all, I have never done this, so my opinion  is just that: an opinion and not expert advice.

After reading through the article I gave a link to, and a bit of associated stuff, I would be trying the following.

Run ddrescue to make a copy of the messed up HD to somewhere else.
Try testdisk, maybe on the copy. 

You should read up on these programs yourself to be sure that they really do what I think they do.

\\:D/ HELL YEAH MAN!
that perfectly did the trick! you are awesome!
testdisk is fantastic, extremely user frinedly and, safe (I believe) thankyou very very VERY MUCH MAN. I OWE YOU A LOT THANKS

---

