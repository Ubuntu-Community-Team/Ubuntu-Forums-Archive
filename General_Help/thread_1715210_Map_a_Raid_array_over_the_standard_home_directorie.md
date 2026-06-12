---
title: "Map a Raid array over the standard home directories"
date: 2011-03-26
forum: General Help
---

### Post by txtiger on 2011-03-26
I recently installed a new Raid 5 array in my machine.  The current install uses a separate partition for /home and has the usual Documents, Downloads, Music, etc. on it.

This /home drive is a fast SSD with about 60 GB in the partition.  The new raid array has 3 TB and includes other directories that are not in /home (like backup, podcasts, themes, etc.).  Also the Raid actually holds its files in a Logical Volume.

What is the cleanest way to have Ubuntu map certain /home directories to the Raid array instead of the SSD?

I would like for this to not affect the system if I decide to install another distro (say Kubuntu) or if I upgrade.

My initial thought was to mount the individual Raid directories "into" the existing home directories.  I do that on a box that uses NFS shares, but I don't know how to do that with a directory and not a block device.

I have tried using a symlink link

ln -s /home/[user]/Raid/Videos /home/[user]/

but it won't do it.  The error is: ln: creating symbolic link `/home/[user]/Videos': File exists


I could get around that by removing the Videos directory first, but that would be dangerous if automated. For example, if the link were broken and some material got dropped on the SSD.

Any suggestions?

Thanks in advance for your help.

---

