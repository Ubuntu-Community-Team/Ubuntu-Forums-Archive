---
title: "RAID1 SoftwareRAID or fakeRAID"
date: 2011-11-21
forum: General Help
---

### Post by william200mph on 2011-11-21
Hi there,

I've extensively read documentation on this subject, and have taken the trial and error approach too, but having spent many evenings I am a bit stuck. Hope you can help.

I have 2 x 1TB Sata drives I wish to use to store my media (80GB Sata used as boot drive) and my aim is to run in RAID1, mirrored.

My mobo is Asus P5QC with Intel driver Raid (fakeRAID, I believe?). Initially I tried linux software raid (followed mdadm tutorials and suchlike) but was puzzled that I could store data on the array without partioning it. Any thoughts on that? Anyway, biggest problem was I couldn't get the array to automount on boot (maybe due to partion problem?); it was almost as if the raid array didn't exist in certain contexts (rc.local or /etc/fstab didn't have entries the tutorials said it should have, for example).

SO...

I removed that array and went down the route of Intel RAID on motherboard (also heard this would ease dual-booting, which I might consider). This is fine and dandy except I got wholly confused with there being TWO arrays (dm0 and dm1) formed.

I'm sorry - in a muddle! Hope somebody can help a little. Does anyone have experience with Intel fakeraid in ubuntu 11.10? This sounds like the best for my situation as I might consider dual-booting in the future (~Windowsboy hangs head in shame~). I should make clear these drives are for data storage and not for booting.

Thanks a million, in advance!:D

---

