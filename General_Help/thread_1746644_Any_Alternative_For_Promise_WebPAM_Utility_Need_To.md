---
title: "Any Alternative For Promise WebPAM Utility? Need To Rebuild RAID Setup"
date: 2011-05-02
forum: General Help
---

### Post by hayhursm on 2011-05-02
Hello Everyone,

I need a utility to rebuild RAID setups after a HDD failure.  I currently have two HDD's hooked up to a Promise FastTrak TX2650/TX4650 controller; under Windows I could use Promise's WebPAM utility to rebuild the RAID.  Well, I no longer use Windows (and never plan to again) so is there a native Linux program that can rebuild RAID configurations in the event of a HDD failure?  

Promise finally released WebPAM for Linux ([http://www.promise.com/support/download.aspx?m=93&region=en-global&rsn1=24](http://www.promise.com/support/download.aspx?m=93&region=en-global&rsn1=24)), but I believe you must install Promise's proprietary Linux driver in order to get WebPAM to work.  I would really like to avoid installing their proprietary Linux driver if at all possible.  Any help is always greatly appreciated!

P.S. I'm running Ubuntu 10.04 x64 as of right now.

---

### Post by hayhursm on 2011-05-17
Can anyone help me out on this?

---

### Post by aphatak on 2011-05-17
I assume your OS is not stored on the RAID array, and therefore in theory you can use a software RAID.  If this is correct, I would try installing mdadm : no guarantees that it would work, but at least you will be no worse off than before!  If you need help installing / using it, reply to this thread.  If not, could you please try it and post the results so others may learn from your experience?

---

### Post by hayhursm on 2011-05-17
> **aphatak said:**
> I assume your OS is not stored on the RAID array, and therefore in theory you can use a software RAID.  If this is correct, I would try installing mdadm : no guarantees that it would work, but at least you will be no worse off than before!  If you need help installing / using it, reply to this thread.  If not, could you please try it and post the results so others may learn from your experience?

Correct, the OS is not on the RAID configuration.  How reliable is a software RAID over a hardware RAID?  If I install a software RAID, wipe out my OS and do a fresh install (taking note that the OS is not on the RAID configuration) will I destroy my RAID data or is the configuration loaded on the RAID superblock?

---

### Post by aphatak on 2011-05-18
I have found software RAID solid and reliable in two+ years of personal use - just make sure you don't have a power failure while RAID is being written to.  I have had one disk in a RAID-5 array fail (it was a creaking old disk); it was automatically marked as failed.  I removed it from the array, and put a fresh disk in its place, and the array was re-built in the background.  All I lost was 15 minutes when the machine had to be shut down to install the new disk.

I has been a while since I tried it, but I remember that if I boot from a Live CD, the software RAID is recognized - which means enough of the RAID configuration is saved in the RAID superblock.  That, to me, means the software RAID would survive an OS transplant.  You could set up a software RAID, boot from a live CD (and/or install another Linux version in a separate partition) and confirm that it recognizes your RAID before committing yourself, of course!  Will you please post the results, so I may learn from it too?

Also, it is possible that you might not have to re-create your RAID configuration - your hardware RAID could quite possibly be recognized automatically, and all you might need to do is start and mount it.

---

### Post by hayhursm on 2011-05-18
> **aphatak said:**
> I have found software RAID solid and reliable in two+ years of personal use - just make sure you don't have a power failure while RAID is being written to.  I have had one disk in a RAID-5 array fail (it was a creaking old disk); it was automatically marked as failed.  I removed it from the array, and put a fresh disk in its place, and the array was re-built in the background.  All I lost was 15 minutes when the machine had to be shut down to install the new disk.

I has been a while since I tried it, but I remember that if I boot from a Live CD, the software RAID is recognized - which means enough of the RAID configuration is saved in the RAID superblock.  That, to me, means the software RAID would survive an OS transplant.  You could set up a software RAID, boot from a live CD (and/or install another Linux version in a separate partition) and confirm that it recognizes your RAID before committing yourself, of course!  Will you please post the results, so I may learn from it too?

Also, it is possible that you might not have to re-create your RAID configuration - your hardware RAID could quite possibly be recognized automatically, and all you might need to do is start and mount it.


Ok, it may take me a little while to implement this because I want  to be very cautious and make sure I fully understand everything.  I have  a lot of sentimental data on my RAID setup (family pictures, videos,  etc...) and I don't want to lose any of it.  I will post my results  after completion.  Thank you for all the help!!!

---

### Post by mpbarros on 2011-11-18
Hayhursm,

I've almost the same problem, my server has a 60GB disk where OS is installed and have a Promise Fastrack FX2650 with 2x 1TB HD with the data.
One of those 1TB HD has failed and I need WebPam or other software to rebuild the RAID with a new disk.
Can u help?

---

### Post by hayhursm on 2011-11-20
> **mpbarros said:**
> Hayhursm,

I've almost the same problem, my server has a 60GB disk where OS is installed and have a Promise Fastrack FX2650 with 2x 1TB HD with the data.
One of those 1TB HD has failed and I need WebPam or other software to rebuild the RAID with a new disk.
Can u help?

mpbarros,

I wish I could help you more but I did come across this on Promise's website: [http://www.promise.com/support/download.aspx?region=en-global&m=93](http://www.promise.com/support/download.aspx?region=en-global&m=93)

Select the FX2650 and you can download the WebPAM utility but I believe it requires the Promise driver (not the Linux one) to work.  I never got around to installing the Promise driver and ended up rebuilding the RAID through Windows (which I did as a last resort).  If you decide to install the Promise driver and WebPAM utility please let me know the results as I just had another HDD go out and need to rebuild the RAID again.

---

