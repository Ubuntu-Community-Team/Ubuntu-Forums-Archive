---
title: "HDD Musical Chairs- /dev Labels Changing"
date: 2010-06-07
forum: General Help
---

### Post by Ralob on 2010-06-07
Every 3 or so times I reboot, I need to manually bypass the failed to mount message. This is because my HDD's seem to play musical chairs in their labels. sdb, sda, and sdc all get swapped between the HDD's. So I need to run the fdisk -l  and tweak my fstab. Is there a way to keep them consistent? Editing my fstab each time is getting tedious.

---

### Post by BoneKracker on 2010-06-07
Instead of "/dev/sdX" entries in fstab, use "UUID=" or "LABEL=" entries.              

From MOUNT(1):> 
The recommended setup is to use LABEL=<label> or UUID=<uuid> tags rather than /dev/disk/by-{label,uuid} udev symlinks in the /etc/fstab file. The tags are  more  readable,  robust  and  portable.  The mount(8) command internally uses udev symlinks, so use the symlinks in /etc/fstab is not advantage over LABEL=/UUID=.  For more details see libblkid(3).

You can look up UUID and/or LABEL for devices using blkid command.  You can assign a LABEL (or a UUID for that matter) to a filesystem using filesystem-specific tools such as e2fstune.

---

### Post by Ralob on 2010-06-07
Thanks for the reply. I decided to go the UUID route. Borked the first attempt, but the ever-handy LiveCD let me re-edit the fstab and now it works great.

Thanks for the tip about labels, too. It will come in handy when I get new HDD's.

---

