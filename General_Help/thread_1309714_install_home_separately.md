---
title: "install /home separately"
date: 2009-11-01
forum: General Help
---

### Post by joey-elijah on 2009-11-01
I've seen many people say they install their /home on a separate partition to make re-installation much easier.

How does one do this?

Do i create two partitions? Or just use one partition and mount my install at /home?

---

### Post by praveenthivari on 2009-11-01
> **joey-elijah said:**
> I've seen many people say they install their /home on a separate partition to make re-installation much easier.

How does one do this?

Do i create two partitions? Or just use one partition and mount my install at /home?

While installing the OS you do choose a drive and make it the mount point as 'root' or   ' / '.
To have /home in separate partition create a separate drive and mount it as /home during installation in addition to root or '/'

---

### Post by donato roque on 2009-11-01
You create 3 partitions.  One for the / (for your os), one for the /home, and one for swap.  When you're using the live cd for installation and you get to partitioning, you can do this and also mount the partition.  The installation process itself will mount the partition for you.  

Use Synaptic to save the markings of your installed software before hand on to a file.  Once you have the basic operating system, open synaptic and have it read the file and hit apply.  Check software sources tabs if its ready.  Just tick the repositories and reload.  Then wait for the download to finish.

---

### Post by DeMus on 2009-11-01
> **joey-elijah said:**
> I've seen many people say they install their /home on a separate partition to make re-installation much easier.

How does one do this?

Do i create two partitions? Or just use one partition and mount my install at /home?

The other two posters describe it very well. I just want to add this:
Yesterday I installed Jaunty after a 2 day adventure with Karmic and I did not even back-up my data on the /home drive. Just when installing I mounted /home to the same drive as before and did NOT format it. Not only data was still there, also settings for several programs which I did not even het to adjust anymore.
That's the real benefit from having a separate /home drive.

---

