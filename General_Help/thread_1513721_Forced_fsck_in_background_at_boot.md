---
title: "Forced fsck in background at boot"
date: 2010-06-19
forum: General Help
---

### Post by Sensiva on 2010-06-19
As described in this question [https://answers.launchpad.net/ubuntu/+question/112657](https://answers.launchpad.net/ubuntu/+question/112657)

When I was using Karmic, boot process continues  with the routine fsck running in background (unless it is checking root  or home).
i.e. if a routine filesystem check is due for a partition (other than  root, home or any partition needed to run the system) it runs in  background and the boot process doesn't wait till it finishes.
 Now this is not happening in Lucid, Boot process waits till fsck  finishes then continues, although the partition is being checked isn't  mandatory to get the desktop running.
 How can I make boot process to continue and keep fsck running in  background? or what is the package responsible for that fsck at boot?


 I am using Lucid (upgraded from Karmic using AlternateCD) 64-bit
 

Thanks
/**Sensiva**>

---

