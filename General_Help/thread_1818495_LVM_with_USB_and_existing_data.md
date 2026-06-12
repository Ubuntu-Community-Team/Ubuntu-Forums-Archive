---
title: "LVM with USB and existing data?"
date: 2011-08-04
forum: General Help
---

### Post by hakras on 2011-08-04
I've been thinking about this pretty heavily and am thinking about using LVM to store my media collection.  The USB hard drives (3x1TB) are plugged into my Mythbuntu server and are never unplugged.  The only issue I forsee is that the USB drives spin down when not in use.  Will this cause any issues with LVM?  I have about 750GB of data on one of the drives and, obviously, want to keep this data.  I think the existing data makes it not possible to use a LVM mirror (correct me if I'm wrong).

I was thinking that I could create a 2 disk LVM with the unused data.  Then, copy the existing data to the logical volume.  Lastly, add the third disk into the volume group.  I know doing this does not add any redundancy.  Would it be wise to add a RAID1 or RAID5 on top of the volume group?  Does using USB drives make this unstable?

---

### Post by xdominex on 2011-08-04
Well, the disks' spinning down will cause delays in access time, as I'm sure you already know, but it shouldn't affect the LVM. When hdd disks spin down, the hard drive's processor typically remains active and ready to receive requests/orders. Even when the disks spin down, the hdd remains mapped to the LVM as long as it is still powered on. I suppose I could be wrong, but this is what I believe to be the case. My personal policy is to play it safe and test it out before risking any data loss, though, so go ahead and do that and let me know how it works out. I hope my reply has been helpful!

With regards,
XDomineX

---

### Post by hakras on 2011-08-04
I figured that it probably wouldn't affect the LVM, but would probably affect any RAID sitting on top of it.  Has anyone ever done this?

Also, currently my USB drives come up as /dev/sdd to /dev/sdf.  Is there anything I need to configure to make sure the USB drives are always detected the same on a reboot?

---

### Post by hakras on 2011-08-05
I created the volume without RAID using 2 USB drives for now.  I will keep a backup of the data on the 1 USB drive for a while.
I created an entry in /etc/fstab to mount the volume.  Is there anything else I need to do?  Will the USB drives keep the /dev/sdd - /dev/sdf on reboot or could it change?

---

### Post by xdominex on 2011-08-05
To be safe, in fstab I would change the "sd*" type identifiers to the UUIDs of the drives. This ensures that each drive goes where it needs to regardless of which "sd*" label it is assigned, though I believe they would *theoretically* be fine if you left them plugged into the same USB ports since they most likely get those labels according to which USB port gets scanned first.

With regards,
XDomineX

---

