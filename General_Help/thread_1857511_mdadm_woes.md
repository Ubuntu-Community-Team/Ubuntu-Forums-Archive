---
title: "mdadm woes"
date: 2011-10-10
forum: General Help
---

### Post by MrMakealotofsmoke on 2011-10-10
Hello all,
i have an md array of 5x1.5TB drives. Recently 1 of the drives died so its been running degraded. I sourced a second drive but another dreive has bad blocks so in the meantime until i source another drive ive just left the array stopped. 

Now i went to fire it up to see which was the bad drive so i could replace it but for some reason one of the 4 drives decided it had no superblock. Strange. Since the array drops drives alot ive just been using mdadm --create --asume-clean to build the array everytime i want to mount it and that has been fine. I just do mdadm -E to find the order and mount it. So i did that again this time and device 0 said no superblock, yet the others were 1,2,3 so, knowing that 5 has been missing for weeks, i just did 0,1,2,3,missing (like i always do).

Now this is were im loosing my head. I created the array etc but when i went to mount it, it spat out 
"mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
Crap. So i looked in dmesg and it says
"[XFS: bad magic number
XFS: SB validate failed"

Ok, ill try xfs_repair -n /dev/md1

Well thats been running for an hour or so and all im getting is a lot of .'s.

So, does anyone have any form of help?I dont want to loose another 6tb of data.

Cheers

---

### Post by MrMakealotofsmoke on 2011-10-10
Well before i went to bed xfs_check -n said it could do something, so i ran it without -n and it seemed to have done something. I can now mount the drive but dmesg says its dirty and stuff. What can i do now to make sure my data is fine?

Cheers

PS. Also the xfs_repair said it ran out of memory before it stopped if thats an issue?

---

### Post by MrMakealotofsmoke on 2011-10-11
I guess im boned then? lol

---

