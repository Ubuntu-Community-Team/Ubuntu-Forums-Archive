---
title: "How do you automount a removeable drive"
date: 2010-12-12
forum: General Help
---

### Post by bt101 on 2010-12-12
I am running Ubuntu Server Lucid.
I want to have USB drives and network drives mount at boot, however the drives *may* not be there (after all these are USB drives and also the network may be down making network drives inaccessible).

I tried putting entries in the fstab using the UUID, however the boot just hangs if the a drive is not connected (that ureadahead headache).

What is the proper way to automatically mount these drives so they mount in the same spot each time?

Thanks.

---

### Post by dcstar on 2010-12-13
> **bt101 said:**
> I am running Ubuntu Server Lucid.
I want to have USB drives and network drives mount at boot, however the drives *may* not be there (after all these are USB drives and also the network may be down making network drives inaccessible).

I tried putting entries in the fstab using the UUID, however the boot just hangs if the a drive is not connected (that ureadahead headache).


Use the fstab **noauto** option.

---

### Post by bt101 on 2010-12-13
> **dcstar said:**
> Use the fstab **noauto** option.

Yes, but (correct me if I'm wrong) doesn't that option prevent mounting at boot? (the opposite of what I need).

---

### Post by dabl on 2010-12-13
You really can't have it both ways -- auto mounting, but also with drives missing in action, AFAIK.  The "auto" mount option will produce an error and usually a hung boot, if the stated device is not present.

The USB bus was designed for hot-plugging. You're kinda going against nature to try to use as if it were an internal drive controller.  If you knew for sure that a given external USB drive will always be present, then you could mount it by its UUID number, with the "auto" option, and it will work fine.

---

### Post by efflandt on 2010-12-13
Set a label on partitions.  Then partitions on a USB drive auto mount under /media/label instead of /media/UUID, as long as they are not mentioned in /etc/fstab.

I just tried that.  With no partition label USB flash auto-mounted in /media by its UUID.  It is Kubuntu natty live iso, so I used gparted to set the label of its partition as "knatty".  When I removed it and plugged it in again, it shows in **mount** as:

/dev/sdg1 on /media/KNATTY type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

Although, it is possible that if it is a file system with no concept of permissions for directories (like vfat), it might only be writable by the person running X when it was auto-mounted.

---

### Post by bt101 on 2010-12-14
> **efflandt said:**
> Set a label on partitions.  Then partitions on a USB drive auto mount under /media/label instead of /media/UUID, as long as they are not mentioned in /etc/fstab.

Thanks,only problem is that Ubuntu server doesn't automount.
I'll have to figure out a way of making automount work on Ubuntu server, or maybe it's just easier to make my own scripting.

Funny, the fstab worked fine in previous versions.  If the drive was not there, I would get a helpful error message.  With Lucid, it "helps" me by hanging the server.

---

### Post by dcstar on 2010-12-15
> **bt101 said:**
> Thanks,only problem is that Ubuntu server doesn't automount.
I'll have to figure out a way of making automount work on Ubuntu server, or maybe it's just easier to make my own scripting.

Funny, the fstab worked fine in previous versions.  If the drive was not there, I would get a helpful error message.  With Lucid, it "helps" me by hanging the server.

Servers should not really "automount" USB devices. USB automounting when plugging in is a graphical desktop function. If it worked previously then that may have been a situation that was changed for the very reasons you are complaining about now.

Simply put a manual mount command in the /etc/rc.local file for each USB device that you want mounted (and exists in the fstab file with the noauto option).

---

### Post by bt101 on 2010-12-19
> **dcstar said:**
> 

Simply put a manual mount command in the /etc/rc.local file for each USB device that you want mounted (and exists in the fstab file with the noauto option).

Worked great, thanks.

---

