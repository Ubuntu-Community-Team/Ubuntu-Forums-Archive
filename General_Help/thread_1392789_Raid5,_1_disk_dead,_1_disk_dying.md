---
title: "Raid5, 1 disk dead, 1 disk dying"
date: 2010-01-28
forum: General Help
---

### Post by scotthernandez on 2010-01-28
System background: 
Ubuntu 64-bit, 9.10 (latest updates applied), kernel 2.6.31-17.
Raid5(in order) md0: sdd, sdc, sdf (C-failing), missing(A-dead), sda, sdb (B-unsync'd spare) 
LVM2: I have two lvm volumes on md0
 
I have a raid5 soft-raid array and I lost a disk last week (A). It now makes a horrible clicking sound and is recognized (inconsistenly). I got a replacement and ran in a "clean,degraded" state (trying not to write much). The new disk (B) got here and I added it to the array; it started sync'n but at ~55% another disk (C) was marked faulty (and smartctl also show errors on it) and the sync stopped. I saw this and took the array down.
 
I was able to get the array back up (by re-creating it, minus the missing disk). I added the new disk (B) and again it faulted disk (C) at about ~58%. Smartctl reports more errors on disk (C) and it is clear its time to total failure is close. I'd like to get the array back and recover as much data from the array as possible.
 
I can think of only one good solution for recovery (with data loss). That is to make a copy of disk (C) to disk (B) and then try to re-create the array by swapping disk (C) with disk (B), but still with one disk missing from the set.
 
Does anyone have any other suggestions?
 
I'm going to start with the dd while I wait for an answer. That seems harmless enough (and will take a while).
 
Thanks in advance,
Scott

---

