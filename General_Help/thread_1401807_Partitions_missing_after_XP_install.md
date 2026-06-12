---
title: "Partitions missing after XP install"
date: 2010-02-08
forum: General Help
---

### Post by googleworldblog on 2010-02-08
Alright, so I've been reinstalling OSes quite a bit lately, mostly Linux distros.  I decided I wanted to play a game that I had that only worked in XP, so I cleared a partition for it and installed it there.  I figured I'd be able to reinstall GRUB2 later and get back into my Ubuntu install - and even if I couldn't, my home folder was stored in a separate partition so it wouldn't be lost...

...well whoops, that was a mistake.  When I booted up the live CD, GParted showed that entire hard disk as unallocated space.  Disk Utility's output shows everything but the Ext4 partitions (and displays some ridiculously large amount of unallocated space near the end).  Fdisk gives me this:

```
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00016075

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25496   204796588+  83  Linux
/dev/sda2           25497       51115   205777142    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           38245       51115   103376896    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4   *       51115       76610   204795904    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           25497       31870    51199092   83  Linux
/dev/sda6           31871       38237    51142896    7  HPFS/NTFS
/dev/sda7           38238       38244       56196   82  Linux swap / Solaris
```

From what I've read while searching about this, the Windows install screwed up my partition table... but I haven't yet figured out how to fix this.  My two Ext4 partitions are missing (though my one Ext3 partition is still there)... does anyone have any advice?

I can still read my Ubuntu partition (/dev/sda5) in the terminal, but not through file managers, and the partition where my home folder was stored is just missing altogether - exactly the opposite of what I intended when I created it. =/

---

### Post by houseworkshy on 2010-02-08
That is a lot of partitions as the maxium for a disc is four.  According to that and subtracting the extended one it's over the limit, so it could be something to do with that.  I have also read elsewhere that changes to partitions can cause enumeration problems, UUID. This is beyond me but I noticed you'd been waiting a while for a reply and, if it was me, I'd be going spare so thought I'd give the thread a bump.  If it turns out to be a total disaster and start fresh time, try puppy linux loaded to ram first.  If it can read it then you could save whatever you can salvage of what is irreplaceable via the dvd.  Once that is done, you could have a fiddle with the tools on Puppy ( which are pretty good for such a little thing ) before going back to scratch.  From scratch of course I guess you know the routene, delete all partitions> new MSdos file system> make partitions> and set the bootable flag. Give this post a little longer though as that is pretty drastic. For next time virtual box is a good option if it is only for the odd windows game and trying out distros.  Good luck with it.

P.S.  I went distrowatch mad over the Christmas holidays and broke my system lots of times.  Because I had some time and all my works was safe it was quite an interesting rather than a maddening experiance.  I used the command "apropos" in the terminal in front of words which related to the problems I'd made, then man in front of whatever seemed relevant and saw what came up. One can learn far more from a system which hasn't got precious data on it because one dares to try things out.  Of course it tranceforms into a horror show when the data is precious and one needs the pc for work.

Welcome to the forums by the way.

---

### Post by googleworldblog on 2010-02-08
A few of those are (were) within the extended partition - it wasn't over the limit before the installation.  It does appear to be that way now, though... disk utility also shows my old Ubuntu partition as an extended partition, but it was previously one of the ones inside an extended partition itself.  I'm really just trying to recover some of the files on the other Ext4 partition, which (annoyingly) is the only one I can't find somewhere on the hard drive.

I'll have to try Puppy Linux in a bit and see if it can find that elusive partition.

---

### Post by houseworkshy on 2010-02-08
Ah exe4.  Are you using Ubuntu 9.04, or later, live cd as I don't think the earlier ones support exe4.  du ( in terminal ) might give some clues

---

### Post by houseworkshy on 2010-02-08
You've had the misfortune to meet a novice but looking through the man pages apropos fsck, gives a lot of what may be useful commands.  Just reading up on fsck.ext4.  there are probably more default commands for exe4 in 9.10 than the 9.04 which I'm running on.

man fsck is good reading, the cautious use of it in diagnostic, but not doing anything modes could be a good first step.

Work off safe on removeable media first if it can be done.

I'm sorry but I have to go now.  When I get back I'll look in again and if the problem remains unsolved even if I can't help I can at least give the thread a bump.  Good luck.

---

### Post by houseworkshy on 2010-02-09
Disturbingly quiet.  Any luck?

---

### Post by mixmaster on 2010-02-09
It is possible that when you installed linux you created a GPT (GUID partition table).  This has many advantages if you have compatible operating systems but I do not think it is supported by XP 32 bit.  Also, fdisk will incorrectly interpret GPT data. I'm afraid I have no advice as to how you can recover if you've written windows partition table info into a GPT.

It is too late now, but if you are constantly installing and removing operating systems my advice would be to keep important data on a separate hard disk so that in a situation like this you can at least wipe and reinstall without losing anything significant.

---

### Post by john newbuntu on 2010-02-09
I have seen a number of forum users use "testdisk" utility and restore their partitions.  Please search for this utility.  This runs from a liveCD.  You would normally install it after sticking in your liveCD and enabling universe option in your synaptic respository.  This should clean up the partition table. This could be your lifesaver.

---

