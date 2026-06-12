---
title: "Are ntfs partitions removable devices?"
date: 2011-11-01
forum: General Help
---

### Post by glaubersm on 2011-11-01
Hello

My two ntfs partitions are detected as removable devices and appear in bottom right corner from gnome-shell. Why?

I use Oneiric x32.

---

### Post by 2F4U on 2011-11-01
They can be unmounted and therefore removed. Maybe thats why they are detected as removable.

---

### Post by glaubersm on 2011-11-01
> **2F4U said:**
> They can be unmounted and therefore removed. Maybe thats why they are detected as removable.

Good explanation, but is strange for me partitions from internal hard disks detected as removables.

---

### Post by Gatemaze on 2011-11-01
My guess, they are dynamically mounted under /media and this is why they appear on your desktop. Add them on your fstab and on a directory under /mnt (or anywhere else other than under /media) and they will stop appearing on your desktop.

Forgot, if you don't want them mounted then this is also done through fstab.

---

### Post by dave0109 on 2011-11-01
As far as I understand it, the dynamic device manager (udev) will have probed your system and found your other partitions which are made available for mounting in Ubuntu.

Think of them as removable from the Operating System's point of view, rather than a physical perspective.  They are not required by Ubuntu for the system to run correctly.

---

### Post by glaubersm on 2011-11-01
> **Gatemaze said:**
> My guess, they are dynamically mounted under /media and this is why they appear on your desktop. Add them on your fstab and on a directory under /mnt (or anywhere else other than under /media) and they will stop appearing on your desktop.

Forgot, if you don't want them mounted then this is also done through fstab.
My two ntfs partitions are mounted on boot.
After I change mount point to /mnt folder my ntfs partitions does not appear in nautilus. I already reverted fstab to previous configuration.

---

### Post by Gatemaze on 2011-11-03
> **glaubersm said:**
> My two ntfs partitions are mounted on boot.
After I change mount point to /mnt folder my ntfs partitions does not appear in nautilus. I already reverted fstab to previous configuration.

In order for them to appear in the nautilus side panel create bookmarks.

---

### Post by glaubersm on 2011-11-03
> **Gatemaze said:**
> In order for them to appear in the nautilus side panel create bookmarks.

thanks for your tip, friend. :D

---

### Post by Gatemaze on 2011-11-04
> **glaubersm said:**
> thanks for your tip, friend. :D

You are welcome. :)
If you think the issue is resolved you can mark it as such as it helps other to find reliable solutions.

---

### Post by glaubersm on 2011-11-04
> **Gatemaze said:**
> You are welcome. :)
If you think the issue is resolved you can mark it as such as it helps other to find reliable solutions.

Solved! :D

---

