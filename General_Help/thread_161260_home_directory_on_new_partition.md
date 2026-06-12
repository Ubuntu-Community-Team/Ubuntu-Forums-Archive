---
title: "home directory on new partition"
date: 2006-04-16
forum: General Help
---

### Post by qkslvrwolf on 2006-04-16
Ok, so I wasn't using my windows drive at all, so I freed up a bunch of space there and repartitioned it with qtparted and system recovery cd.  Then, I mounted the new partition (hda4) on /mnt/newdrive, and copied my home directory to the new drive.  Then I edited fstab and added /dev/hda4 to mount on /home.

Then I rebooted. Everything came up and worked just fine. mtab showed /home mounted on hda4.

So I rebooted into system recovery cd and blew away hte /home directory on hda3.  Then I rebooted.  At this point, the ubuntu splash screen shows that I'm failing to mount the filesystem, and I can't get into my box.  What did I do wrong?

---

### Post by qkslvrwolf on 2006-04-16
I think I figured it out.  Partially.  /home still needs to exist on hda3, the drive with the root directory.  I made /home with system recovery cd, but didn't add any files, and now I'm back in.  Sweet!

---

### Post by Ensnared on 2006-04-16
If you deleted the /home directory, that's probably what causes the error. The directory needs to exist for the drive to be mounted on it, but it has to be empty.

EDIT: Exactly right ;)

---

