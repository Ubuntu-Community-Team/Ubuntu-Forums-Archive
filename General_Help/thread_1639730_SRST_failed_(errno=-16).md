---
title: "SRST failed (errno=-16)"
date: 2010-12-07
forum: General Help
---

### Post by abstraction on 2010-12-07
Hi there, I've had a good search on this error but none of the threads/site's I've found have offered a solution to me.  

I have a 64bit system which is dual booting W7 and Ubuntu, I was running x64 Ubuntu 9.10 which worked fine but after I updated to 10.10 I started  getting this error

```
ATA4: SRST failed (errno=-16)
```

4 times on boot until eventually it says 

```
reset failed, giving up
```

Then gives up and boots into Ubuntu. Once I've booted in all my hard drives aside from my 1.5TB drive appear.

I have a 74gig WD Raptor split into two partitions for each of the OS installs.
I've then got 3x 500 gig drives (no Raid) and 1x 1.5TB drive on Sata along with my DVD drive.

I tried to fix the error by formatting and reinstalling a fresh copy of Ubuntu but it still persists.

The 1.5TB drive appears in the Bios, works fine in Windows 7 and chkdsk doesn't find any problems, but I can't run any tests on it from within Ubuntu as it isn't recognized.  

The solutions I've read have included ' turning my drives to cable select' but i have no idea what setting that refers to. People have also  had success removing the faulty HD but I don't want to consider that an option just yet as it works fine in windows. Running some fdisk commands also seems to have worked but as i can't get Ubuntu to mount the disk I can't see how to do that.

Can someone here offer me some light on how to fix this error and get this drive working?

Any assistance is appreciated

Thanks, Abstraction

More system details in case they're relevant

Mobo: Nforce 780i 
GPU: 2x 8800GT in Sli
CPU: Intel E6850
Ram: 4gig
onboard sound

---

### Post by abstraction on 2010-12-08
Is no one able to help?

---

### Post by matr07 on 2011-02-22
Hello Abstraction,

I'm not sure if you were ever able to fix your issue with the SRST failed, but I recently had this issue and spent quite some time trying to fix it myself.  I learned that updating my BIOS was the fix.  If you haven't tried that yet, I recommend completing the update to the latest BIOS version for your mobo and see if that fixes the issue.  

If that doesn't help, unfortunately I don't have any other advice as that was the only thing that worked for me. 

Hope this helps.

-Matr07

---

