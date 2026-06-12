---
title: "gparted messed up partitions / merging partitions &amp; recovering"
date: 2010-01-14
forum: General Help
---

### Post by chezybezy on 2010-01-14
Please forgive how long this is but i am trying to explain everything as this is not my area of expertise, and if i use the wrong term to shorten the explanation i worry i will lead off into the wrong direction.
booted gparted to join what is now an empty partition onto its neighbour on my second hdd.

when gparted was loaded i noticed it identified a 50/60gb partition as unused on my first hdd (earlier that day id had a nightmare with gparted crashing mid way through a resizing operation - but luckly managed to recover everything (or maybe most) via chkdsk /f. during this there was a task to shrink the partition by roughly that same amount, which was graphically in the same place.)
so i assumed (yes i know i can hear the groans) that this was performed before the crash and was in fact free unused space.

i then selected to join this (identified as an empty partition(VISTA - refer to layout below) onto its neighbour partition (STORAGE), about halfway through its 'read of data before moving' section i realised that it should have been my vista partition (which worked perfectly fine an hour before and gparted for some reason identified it incorrectly). i checked 3 times that gparted was still in the 'reading data before moving' (im unable to recall the exact name but thats how i understood it) phase before actually moving the data, then hit cancel due to thinking that when it crashed during this stage before that i will be able to at least recover this partitions data as nothing had been moved yet. and maybe the other data on vista partition if im lucky.

when i booted up after cancelling n rebooting, into my win7 OS - it identifys one partition as the exact size of the data that had to be moved and thus joined to the falsely empty partition (169.26gb - shown below in 'current messed up state' diagram) and shows the other original to be moved and joined containing data partition as empty ( the 68.29 unallocated partition below [will get exact wording when i can get back onto the pc]).

so i booted into gparted to see what state my primary hdd (hdd1) was in - diagramatically things have shifted to the left as though the partition starting point had been changed ( see diagrams below [as instructed however mistakenly by myself]) - so it looks as though partition 3 had been (at some level - maybe not completely) merged with partition 2. 
now im hoping that seeing as nothing has not actually been written on top of anything - i.e. no datas been moved / rewritten that there is hope. (this is how i understand it) its just a case of moving partitions to back to where they were and running something like checkdsk /f as i did after gparted crashed on me - as to me they seem that they are essentially the same problem.
i am less hopeful with recovering the vista partition, as partition 3 (storage) has been marked as being moved over it however it may be just the same 'rescue' process i described hopefully as above.
please tell me that i have not gotten this wrong and i have some hope! im desperate. To me it (recovering my v stupid mistake) seems easier than recovering from a dead / dying hdd / a formatted hdd or one which has a OS installed on top of it.

i cant help but wonder if its like recover partition table or use something like spindisk or something along those lines.

Partitions:
ORIGINAL: 
HDD1 (500gb): XP 28.15 | VISTA 60ish | STORAGE | Win7 200.03
CURRENT MESSED UP STATE:
HDD1 (500gb): XP 28.15 | 169.26gb | unallocated 68.29 | Win 7200.03
[SIZE=2][COLOR=gray]Chez[/COLOR][/SIZE]

---

### Post by mechro on 2010-01-14
To recover a partition table you could try Testdisk.

Testdisk may be on your "gparted" that you "booted" assuming it's some sort of LiveCD Distro.

Otherwise, you can run Testdisk from a Ubuntu LiveCD; you'll have to install it via Synaptic first.

---

### Post by chezybezy on 2010-01-17
Sorry for the delays in replying i work over weekends so its a bit difficult with the long shifts.


ive had a poke around with teskdisk basically seeing what it can recover / find. using deeper search,it appears to locate my STORAGE partition and ive managed to copy all files to my secondary hdd. i used 'find and mount' to do so via explorer - graphically i figure i cant mess up as badly (then again look at the mess im in lol). 



i believe everything shown is everything on that partition. i am just about to back these up to dvds ASAP. So obviously ive not re-written my partition yet - and dont really want to until im using an image (New Larger HDD should be arriving soon) - i couldn't figure out if this can be done on the image and thus preserve the original?


The same cant be said for the VISTA partition - teskdisk appears to identify a partition that i believe is my vista partiion (actually twice - from memory i think one is from backup boot record but when i use p to list the files on the partition i receive "cant open filesystem. filesystem seems damaged." im guessing that maybe something has somehow been written or altered? via gparted? (to be fair i noticed avg dumped a hidden file on the 'new partition' - which i believe is the one 'ontop' of the VISTA partition.


Does this mean that my hope now lies with recovery software? and also how is it best to limit the recovery scope- idealy i do not want to include the XP and Win7 partitions and thus include everything in-between regardless of partition state?

---

### Post by mechro on 2010-01-18
Testdisk should be able to create a partition table using an image.

If you have Testdisk then you also have Photorec which can recover many types of files.

---

