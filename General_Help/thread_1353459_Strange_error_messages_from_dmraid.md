---
title: "Strange error messages from dmraid"
date: 2009-12-12
forum: General Help
---

### Post by b166er on 2009-12-12
Hi
I recently installed "Karmic Koala" (fresh install). 
All disks seams to work fine. And I've had no real problems really. But ever since I installed Karmic I've seen these error messages all over the place:

ERROR: ddf1: Cannot find physical drive description on /dev/sdb!
ERROR: ddf1: setting up RAID device /dev/sdb
no raid disks

I Dosen't seam to do anything bad. but I see it every time I boot or drop into a shell with "ctr-alt-f1".
If I would have to guess, I'd say that something is making dmraid "think" that it should treat sdb as a raid device, but when it discovers that sdb isn't a raid, it stops. 

Iv'e never played around with raid in linux, and have therefore no experience in this area. And I have never wanted sdb to be a raid-device.
But why am I seeing this? and how do I solve the error?

---

