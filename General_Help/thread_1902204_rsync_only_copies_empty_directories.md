---
title: "rsync only copies empty directories"
date: 2011-12-30
forum: General Help
---

### Post by mahohmei on 2011-12-30
Ubuntu 10.04

I have a NAS device: a USB hard drive connected to a Linksys E4200 router/wifi/NAS device.

I want to back up my home directory with:

rsync -av /home/matt /home/matt/.gvfs/matt\ on\ cisco31545/

This command copies over the folder structure perfectly, with all folders empty, yet the verbose output shows each individual file being copied.

Any thoughts?

Thanks!

---

### Post by papibe on 2011-12-30
Hi mahohmei

A couple of ideas:

First, I would avoid syncing when the destination is contained into the the source. You'll have a recursive problem. Instead, I would mount the Cisco share into a different directory, for example /media/cisco31545 or /network/cisco31545

My guess is that the share is NTFS, so I would recommend playing with the option --modify-window in order to manage better modification times.

I hope it helps.
Regards.

---

