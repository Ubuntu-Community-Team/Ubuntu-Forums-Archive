---
title: "Name of mount point instaead of n GB Filesystem in Places menu &amp; Nautilus."
date: 2012-04-05
forum: General Help
---

### Post by New00Folder on 2012-04-05
Hi

I'm running ubuntu 10.10 and today I came across a USB pen drive which was unusual in the sense that the nautilus browser didn't open up automatically which is its default setting. I opened disk utility and mounted the pen drive from there. Then I saw that the entries in the Places menu and in the left panel of the nautilus browser had changed form "n GB Filesystem" to the name of mount points. The entries reverted back after restart.

I tried to change these entries to mount points from dumb n GB filesystem a long time ago but couldn't. I have two equally sized partitions, and they appear in a different order in KDE and GNOME. There's no way I can tell them apart by just looking at them. Now this incident leads me to believe that it's possible to change the entries.

If you know how it can be done, please let me know.

Thanks.

---

### Post by sudodus on 2012-04-05
I suggest that you set labels to the partitions on those external drives. You can use the ***disk utility*** or ***gparted*** to set labels.

Disk Utility alias ```
palimpsest
```

Then the partitions on these drives will be displayed with their labels by the file browser.

---

### Post by New00Folder on 2012-04-05
I'm sorry I was wasn't very specific in my initial post, but the partitions I'm talking about are NTFS and disk utility isn't allowing to set labels to them.

EDIT: OK I got it. Running as root did it. Thanks a lot sudodus.

---

