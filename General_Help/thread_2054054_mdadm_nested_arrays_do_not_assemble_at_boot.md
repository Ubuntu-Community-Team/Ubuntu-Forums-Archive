---
title: "mdadm nested arrays do not assemble at boot"
date: 2012-09-06
forum: General Help
---

### Post by cmcguire on 2012-09-06
I have a raid 5 array constructed of three partitions, one of which is another array.  This array should be assembled during boot so that it can be mounted and other services can access the mounted data.  **The OS itself is not booting from this array.**

General md setup:
/dev/md0 = sda + sdb  (raid 0)
/dev/md1 = md0 + sdc + sdd (raid 5)

The /dev/md1 array has no problem assembling when the OS is running.  However, once the system is rebooted the second array always falls into a degraded state because /dev/md0 does not seem to be added to the /dev/md1 array during the boot sequence.  

Any ideas why /dev/md0 does not seem to get scanned or added to the array during boot?  Shouldn't the boot sequence be able to handle nested arrays?


As a proof of concept that the OS is not able to handle the nested arrays, I wiped 2 drives and added 4 small partitions to one and 2 to the other.  Then I constructed 3 fresh raid0 arrays from those (md0,md1,md2).  Then I constructed 1 raid5 array from that (md3=md0+md1+md2).  Arrays md0,md1,md2 all assemble during boot, but md3 fails and is not available.  After the boot sequence, running "mdadm --stop --scan" then "mdadm --assemble --scan" successfully reconstructs all arrays, even md3.  

So what's up with the boot sequence?  

FYI.  This machine was recently upgraded from 9.04 to 12.04.  This worked in 9.04.

---

### Post by cmcguire on 2012-09-07
Using a fresh install of ubuntu server x64 12.04 on a virtual machine I was able to produce the same results.  

Setup:  4 virtual drives (all with a single primary partition)
2 - 1GB (sdb1,sdc1)
2 - 2GB (sdd1,sde1)
sda is the linux install

md0 = sdb1 + sdc1 (raid0)
md1 = sdd1 + sde1 + md0 (raid5)

All is well until the server is restarted.  Upon restart, md1 is degraded as it does not see md0.  I have a sinking feeling that nested arrays are not supported in 12.04.  Has anyone seen this work?

---

### Post by cryptotheslow on 2012-09-07
Sounds like a classic race condition in that md0 is not ready before md1 tries to assemble itself.

I don't use software raid so I may be way off with what follows, for all I know raid is not started this way.

Ubuntu is now using Upstart rather than more traditional initscripts, the benefit of Upstart is that it speeds things up by starting things for a particular run level in parallel rather than sequentially. This can cause problems if you have two services that start at the same run level where one depends on the other and the depender service starts faster than the dependee (is that even a word? hopefully you know what I am getting at!).

I think you may have to get down and dirty with your Upstart job configs to ensure md0 is up before md1 tries to come up with some script wizardry.  I messed with them a while back for something entirely different and am by no means an expert so I'll just point you to a jumping off point: 
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

I'll re-state - I'm not even sure raid is started by Upstart so the above is just a thought on a possible area to look into.

---

