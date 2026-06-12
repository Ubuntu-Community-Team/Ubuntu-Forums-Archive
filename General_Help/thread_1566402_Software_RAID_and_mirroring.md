---
title: "Software RAID and mirroring"
date: 2010-09-02
forum: General Help
---

### Post by Azdour on 2010-09-02
Hi all,

I've set up a test machine with Ubuntu 10.04. It has two drives making one RAID 1 drive using mdadm. This RAID drive is where /home is mounted.

I like to break things just to see what happens :) and to know what to do to resolve it before it happens for real. So I physically removed one of the drives that made up the RAID 1 (while it was off). I then rebooted the machine. I thought since it was mirrored then /home would mount correctly using the other mirror. 

What actually happened was on the Ubuntu splash screen it said there was a problem mounting /home.

I skipped the mounting, logged in and looked in /proc/mdstat. It reported one drive that was inactive it did not report the missing drive.

Anyone any ideas as to why the RAID 1 did not do its job?

---

### Post by Azdour on 2010-09-03
I think I may have answered my own question. Since mdadm is software based it seems it can only cope with a drive failure while it is switched on - which now I think about it is sensible as how can the software work when the machine is switched off :). Taking the drive out while the machine was on worked, my /home was still there even after a reboot.

---

### Post by epsolon77 on 2010-09-03
it should still show the raid array in a degradded state and should not allow access to the raid set.  I'm a little rusty on my MDADM commands, but you should need to add another drive in and tell MDADM to rebuild the array using the new drive and the info from the old drive.  After the array is built back up the software drive should be mountable again.

Remember with raid there are two levels, the physical drive and the software drive.  Ubuntu is mounting the software drive, not the hardware drive.  So if a hardware drive is missing, MDADM may not be able to keep running the software drive in a failed state.  The exception should be some live setups on MDADM involving higher raid levels.

Again please someone check this, it's been a while.

---

### Post by Azdour on 2010-09-03
Hi,

It did show the RAID as inactive but only one drive, no mention in mdstat that it was 2 drives. I agree with you that in my case, having switched the machine off and removed one of the mirrors, mdadm was not able to cope but I think this is working as expected. Like you say if I ever did power off the machine and the drive broke while off I should be easily able to rebuild it.

At least I know now that if a drive fails while it is on, it will not fall over but rely on the mirror until the failed drive is replaced and rebuilt.

---

### Post by epsolon77 on 2010-09-03
> **Azdour said:**
> Hi,

It did show the RAID as inactive but only one drive, no mention in mdstat that it was 2 drives. I agree with you that in my case, having switched the machine off and removed one of the mirrors, mdadm was not able to cope but I think this is working as expected. Like you say if I ever did power off the machine and the drive broke while off I should be easily able to rebuild it.

At least I know now that if a drive fails while it is on, it will not fall over but rely on the mirror until the failed drive is replaced and rebuilt.

There are different raid schemes that have live failover.  Generally what I would recomend is build in a hot spare on the MDADM group.  That way, off or on, if a drive fails, it notifies you and moves on with life, then you can replace the dead drive at will.

Also look into the new INTEL northbridge chipsets.  Mobo's with these chips gernerally support hot swap on the onboard sata connections.

---

