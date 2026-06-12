---
title: "How do I recover lost files?"
date: 2006-03-18
forum: General Help
---

### Post by teasum on 2006-03-18
Relative Newbie here.  After copying a bunch of files over from another pc to my Dell Inspiron 8600 laptop, and getting some work done, I had a system crash.  All my documents are stored on a Fat32 partition shared with XP.  After booting to XP, I think checkdisk went to work on my files.  Long story short, the files I recently copied and worked on are in the "found.000" folder on my Fat32 partition.  I assume this happened when I booted to XP, although I'm not sure.  Does Ubuntu run anything similar to scandisk when booting after a crash?

Nothing that I lost is too critical, although a couple of files I'll have to write all over again.  Anyhoo, I want to know if there is a utility that I can use from within Ubuntu to attempt recovery of .chk files.

SUM: 1) Does Ubuntu run something similar to checkdisk after a bad crash, and 2) is there a linux utility I can use to attempt recovery of .chk files?

Thanks!

---

### Post by cwaldbieser on 2006-03-18
[QUOTE=teasum]Relative Newbie here.  After copying a bunch of files over from another pc to my Dell Inspiron 8600 laptop, and getting some work done, I had a system crash.  All my documents are stored on a Fat32 partition shared with XP.  After booting to XP, I think checkdisk went to work on my files.  Long story short, the files I recently copied and worked on are in the "found.000" folder on my Fat32 partition.  I assume this happened when I booted to XP, although I'm not sure.  Does Ubuntu run anything similar to scandisk when booting after a crash?

Nothing that I lost is too critical, although a couple of files I'll have to write all over again.  Anyhoo, I want to know if there is a utility that I can use from within Ubuntu to attempt recovery of .chk files.

SUM: 1) Does Ubuntu run something similar to checkdisk after a bad crash, and 2) is there a linux utility I can use to attempt recovery of .chk files?

Thanks![/QUOTE]

Ubuntu runs fsck (file system check) after every 30 reboots or so-- not sure if it does it after a crash.  It usually puts the dredged up remenants of files in /lost+found.  I'm not sure about a recovery utility, though.

---

### Post by Lunixfanboy on 2006-03-18
[QUOTE=teasum] Does Ubuntu run anything similar to scandisk when booting after a crash?
Nothing that I lost is too critical, although a couple of files I'll have to write all over again. 
SUM: 1) Does Ubuntu run something similar to checkdisk after a bad crash, and 2) is there a linux utility I can use to attempt recovery of .chk files?
Thanks![/QUOTE]First, fsck (and the various other file system fscks like reiserfsck) is run after a predetermined number of mounts of the partition, and does a much better job of tidying things up than the wonder that is chkdisk/scandisk. Second, if the files you were writing are text, then you can use a Linux text editor to examine those .chk files directly, and save the contents to a recognizable filename. For example, open file0001.chk, find that it contains some text from Letter to Fred, save file0001.chk as Letter to Fred, then continue in the same manner, and you can copy/paste the text into the existing newly saved document to recover. Binaries, however, are quite another thing, and you are usually up the proverbial creek there.

---

### Post by teasum on 2006-03-19
Thanks for the information.  I was able to recover a few of the files, but since I'm really just looking for 2 or 3 files amongst about 100, I think I'll just give up and start writing again--more efficient use of my time!

---

