---
title: "Mounting error"
date: 2011-01-15
forum: General Help
---

### Post by mharrison on 2011-01-15
Ok, so up until yesterday, I had Ubuntu 10.04 installed entirely on my 750 gig SATA drive.  Yesterday I backed up my /home and installed a 200 gig drive and reinstalled using the 200 gig drive as / and swap...The 750 gig drive was all /home.

Now, whenever I reboot it comes up saying it had serious errors mounting /home and I have to reboot again to get it to boot up.  I never had this issue when the 750 gig drive was running the entire show.  

Has anyone else run into this?  S.M.A.R.T. hasn't been throwing any warnings or errors so I am at a loss as to what "serious" errors Ubuntu could be running into.

---

### Post by dcstar on 2011-01-15
> **mharrison said:**
> Ok, so up until yesterday, I had Ubuntu 10.04 installed entirely on my 750 gig SATA drive.  Yesterday I backed up my /home and installed a 200 gig drive and reinstalled using the 200 gig drive as / and swap...The 750 gig drive was all /home.

Now, whenever I reboot it comes up saying it had serious errors mounting /home and I have to reboot again to get it to boot up.  I never had this issue when the 750 gig drive was running the entire show.  

Has anyone else run into this?  S.M.A.R.T. hasn't been throwing any warnings or errors so I am at a loss as to what "serious" errors Ubuntu could be running into.

You have probably changed the UUID of the new /home partition - fix /etc/fstab to reflect the change.

You also better have formatted the /home as EXT4 (or another Linux partition type).

---

### Post by mharrison on 2011-01-15
> **dcstar said:**
> You have probably changed the UUID of the new /home partition - fix /etc/fstab to reflect the change.

You also better have formatted the /home as EXT4 (or another Linux partition type).

Actually, this happened after a fresh install, so no, I did not change the UUID.  And, when I get the error message, I can hit the reset switch and it won't throw the error again until some random time that I reboot the system.

And yes, I'm aware that I would need to use a Linux partition type on /home.

---

### Post by mharrison on 2011-01-17
Ok, finally got to check the logs and I do apologize.  The UUID was not the direct problem.  The problem was FSTAB had everything mounted by it's /dev entry, and the /home and SWAP kept fighting over /dev/sda1.  Changed FSTAB to mount everything by UUID and all is well now.

I probably should have done this right after the initial install, but I have honestly never had this issue in the 2 years I have been using Ubuntu.

---

