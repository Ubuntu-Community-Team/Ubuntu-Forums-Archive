---
title: "shrinking my Ubuntu / partition"
date: 2010-01-04
forum: General Help
---

### Post by linuxhippy on 2010-01-04
I just bought a netbook that's installed with the Ubuntu 9.10 remix for netbooks.  It has a 160 GB harddrive and I'd like to have a couple more partitions on there for fresh installs of Ubuntu.  I used gparted from a live cd before and repartitioned a drive with WinXP by defragmenting XP first and then shrinking the partition to 15 GB.  Do I need to do a defrag before I shrink my Ubuntu / partition?  If so, how?

---

### Post by J V on 2010-01-04
No, the linux filesystems make sure a file is put somewhere it won't get fragmented before they write, this means there is little to no fragmentation on a linux box.

Just resize... (but backup first!)

You might want to mount /home in its own partition later...

---

### Post by linuxhippy on 2010-01-04
I thought I had read that Linux files aren't sloppy like Win files!  But that was years ago.  So if I make a /home partition can Ubuntu upgrades and other Linux distros all share this?

---

### Post by jamesisin on 2010-01-04
It's a challenge to fragment the ext file systems in a meaningful way.  Typically if you keep your drive not full (say around 70-90%) you won't see any fragmentation worth discussing.

Be sure to back up your data (I like using image based backups especially).  I did once have a partition go renegade after a resize and had to recover files through some damned wonky file recovery application.

---

