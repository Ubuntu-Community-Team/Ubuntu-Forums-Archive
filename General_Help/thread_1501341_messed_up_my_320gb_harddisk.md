---
title: "messed up my 320gb harddisk"
date: 2010-06-04
forum: General Help
---

### Post by jsriz on 2010-06-04
don't know what actually happened, I generally remove the harddisk without safely removing and suddenly i lost my whole collection of video tutorials and my windows box started asking for disk checking I started the process but as it was slow (but by then some of my files started showing up in a folder "found", which was hidden in windows but visible in linux ) I decided to use test disk don't know how but it showed up a linux partition on it I wrote the partition tables as insisted by the TestDisk.
From then windows does not detect the hdd(as if it were partitioned in extX fs )
and ubuntu shows this error
"
Unable to mount 320 GB Filesystem

[B]Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]
"

after this I tried something that I think only added to my woes I ran
sudo fsck /dev/sdd1
(where sdd1 was this hdd)
and answsered y to all the questions that followed
it suddenly started showing random numbers which seemed never ending...... something like 
" -(948005--948006) -(948008--948009) -948011 -(948013--948014) -(948016--948018) -(948020--948021) -948024 -(948026--948029) -(948031--948032) -(948034--948037) -(948040--948041) -(948043--948044) -948047 -948049 -(948052--948054) -(948057--948058) -948060 -948062 -948064 -(948066--948067) -948069 -948075 -(948077--948081) -948084 -(948086--948087) -(948090--948095) -(948097--948098) -(948103--948106)"
I Know that a format will fix everything but I dearly need those tutorials.
Please Help.......

---

### Post by srs5694 on 2010-06-04
> **jsriz said:**
> don't know what actually happened, I generally remove the harddisk without safely removing

The fact that you just unplug the drive is almost certainly the cause of your problem. I hope you'll learn from this experience and always select an "unmount" or "safely remove" or similarly-named option in the future.

You didn't mention in your post what filesystem the disk used. You strongly implied it was used in Windows, which suggests it was probably NTFS or FAT, but that's not clear. If it was one of those filesystems, or especially NTFS, then any complete filesystem fix will be in Windows, not Linux; Linux lacks any but the most rudimentary NTFS maintenance tools. Better advice depends on your specifying what filesystem you used, so please post back with this information.

If all else fails, you could try using [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which can recover files from an otherwise trashed disk. The files are likely to have strange names, though, so you could end up spending many hours wading through the files to figure out what's what.

---

### Post by jsriz on 2010-06-04
Guess its a really hard way to learn a lesson......
yup it was in ntfs format before test disk wrote some linux partition tables....:(
photorec retrives files i had deleted earlier but not the ones 1 need..
Do I need to format it and try photorec again???

---

### Post by srs5694 on 2010-06-04
***Don't write [i]anything* to the disk until you've recovered your files!**[/i] Doing so could easily make matters worse rather than help. Creating a fresh filesystem is almost certain to hurt your recovery chances. If you think a procedure that involves writing to disk will help, you should do a low-level backup of the disk to another disk before trying. In Linux, something like this will do the trick:

```

sudo dd if=/dev/sdb of=/dev/sdc

```

This copies /dev/sdb over /dev/sdc. *Be sure to get the if= and of= options right!* If you reverse them, you'll end up destroying your data rather than backing it up.

There's no such thing as "Linux partition tables" (as distinct from the implied "Windows partition tables"), although there are Linux partition *type codes* as distinct from Windows-native filesystem type codes. If you could post the output of the "sudo fdisk -lu" command (that's a lowercase "LU", not a digit "1" followed by "u"), somebody can tell you if you've got the wrong type code. This would affect Windows' ability to read the disk, but it won't affect Linux.

---

