---
title: "Strange large file eating disk space?"
date: 2009-09-08
forum: General Help
---

### Post by Compintuit on 2009-09-08
I was routinely checking for large files on my system (20GB HD) and I found this file:/home/caleb/.local/share/gvfs-metadata/home.EPGVZU taking up 623.6 MB! I know gvfs is gnome virtual file system, so I'm wondering if it has to do with my recent switch to mount my /home on a seperate partition. Here what I added to fstab:
UUID="a6958e59-b1d4-4245-a336-76b52a8276af"	/home		ext4	relatime	0 2
Does that have something to do with it? And how can I get rid of that extraordinarily large file! 
Thanks.

---

### Post by Compintuit on 2009-09-22
Bump?

---

### Post by akakingess on 2009-09-22
Maybe the fact that it is ext4 could be the problem, I think if it were ext3 then you wouldn't have the same issue, it's one of those 'do I want the space or the availability and options' that come with ext4. I could very well be incorrect, but remember hearing that ext4, while providing some more options and features, could use more space for maybe indexing or something of that nature (I know that doesn't help much) but at least we could bump this question again and see if we get any more input.

---

### Post by Compintuit on 2009-09-23
I was moving my / partition to the outside of the disk for speed, which meant changing my /home partition, so I was like what the hell... and I deleted it. It made a new one. My boot time dropped 6 secs (wtf?) and so yeah... I've got new files, but nothing bigger than 32kb. So how's that for careful problem solving :)

---

