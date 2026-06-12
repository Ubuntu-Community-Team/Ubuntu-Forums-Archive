---
title: "How to preserve GRUB when reloading XP partition"
date: 2009-12-15
forum: General Help
---

### Post by hovercraft on 2009-12-15
Hi

I'm new here so excuse me if I am posting in the wrong place.

My machine is running Ubuntu 8.1 and Win XP in separate partitions.
(Unfortunately I need windows for certain applications.)
I need to reload Windows after being hit an avalanche of malware but am worried about losing GRUB and not being able to access Ubuntu.

Any advice?

---

### Post by moffa on 2009-12-15
I don't know of any way to perserve grub as Windows will most definately overwrite it. Just use the Ubuntu boot-cd after to reinstall grub.

---

### Post by lidex on 2009-12-15
Have a look at this guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

### Post by hovercraft on 2009-12-15
Thanks people for the quick replies!
The link is just what I was looking for

---

### Post by john newbuntu on 2009-12-15
If you are just repairing windows and not partitioning, you should be able to just backup your current MBR (say using a 'dd' command to a USB drive), repair windows and restore the MBR from the backup.

---

