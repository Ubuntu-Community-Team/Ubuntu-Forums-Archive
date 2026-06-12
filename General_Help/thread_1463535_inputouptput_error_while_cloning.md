---
title: "input/ouptput error while cloning"
date: 2010-04-27
forum: General Help
---

### Post by ub007 on 2010-04-27
i'm trying to clone 2 raid sets using dd.( have done this successfully many times in the past)
this time however running into issues.

dd stops with a 
> 'input/output error'

dmesg shows

> cciss: cmd f7300000 has CHECK CONDITION sense key = 0x3
end_request: I/O error, dev cciss/c0d0, sector 31083240
cciss: cmd f7300000 has CHECK CONDITION sense key = 0x3
end_request: I/O error, dev cciss/c0d0, sector 31083240

a little above this i find 
> Filesystem "cciss/c0d0": Disabling barriers, trial barrier write failed
XFS mounting filesystem cciss/c0d0
XFS: log has mismatched uuid - can't recover
XFS: failed to find log head

Background:
this is a proliant sevrer & has got XFS filesystem on it.
Last weeek it showed some XFS errors, tried to do a repair but didnt work.So thought would clone the raid set from a good 'source' server. ( we need this for a test purpose )

before cloning I deleted raid & created again. everything looked OK, all disks showed as GOOD , 
but then the dd copy failed with above msg
I'm sure the source raid set is in good condition. Any thoughts on what could be wrong here & how I may be able to recover it?

Thanks in advance
David

---

### Post by dcstar on 2010-04-27
> **ub007 said:**
> i'm trying to clone 2 raid sets using dd.( have done this successfully many times in the past)
this time however running into issues.

dd stops with a 


dmesg shows



a little above this i find 


Background:
this is a proliant sevrer & has got XFS filesystem on it.
Last weeek it showed some XFS errors, tried to do a repair but didnt work.So thought would clone the raid set from a good 'source' server. ( we need this for a test purpose )

before cloning I deleted raid & created again. everything looked OK, all disks showed as GOOD , 
but then the dd copy failed with above msg
I'm sure the source raid set is in good condition. Any thoughts on what could be wrong here & how I may be able to recover it?

Thanks in advance
David

1/ Please never quote data, use the Code tags.

2/ There is probably a bad block at the sector that reports the error.

---

### Post by ub007 on 2010-04-27
is there a way for me to track which disk could be the problem using that sector number. my raid comprises of 4 disks...

---

