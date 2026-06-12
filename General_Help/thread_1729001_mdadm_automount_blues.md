---
title: "mdadm automount blues"
date: 2011-04-14
forum: General Help
---

### Post by donarntz on 2011-04-14
I'm posted before about this, and whatever magical thing I did last time doesn't work now.  Let us talk about mdadm and 11.04.

Is there an easy way to automount a raid10?  I'm still getting the wait/skip screen at boot.  I suspect mdadm isn't assembling the disks before the fstab is scanned, but I don't know how to fix this? It mounts fine manually once I'm booted.  This raid is not for the OS, it has all my music and other media on it.  It's a bloody pain to manually mount the raid every time I want to open banshee. 

Any help is appriciated.  I can't post the config files at the moment, as i'm at work.  I'm fairly positive they are correct, and I haven't monkeyed around with them.  And I have deleted the old mdadm/mdadm.conf file and re-ran the configuration.  [FONT=monospace]A couple of things I've noticed that are different from my previous raid10:  The disk utility has the raid named "0" instead of array as before, and mdadm calls the raid dev/md/0 instead of dev/md0 as before.  Sorry I'm still a little bit of a noob, so I don't know how this affects things.

-Don
[/FONT]

---

