---
title: "Switching HD Cable and _Not_ Messing Up Kubuntu"
date: 2006-02-18
forum: General Help
---

### Post by Fotinakis on 2006-02-18
I have Kubuntu installed on a hard drive hooked by a primary IDE cable, and so it is mounted as **hda**.  I need to move the hard drive to be a slave drive and so it would be mounted as **hdb**.

What do I have to change in the configuration files so that it can still boot correctly and know that it is now *hdb*?
Do I only have to edit *grub.conf *and* /etc/mtab*?

---

### Post by daller on 2006-02-19
You should probably edit both /etc/fstab, /etc/mtab and /boot/grub/menu.lst

---

