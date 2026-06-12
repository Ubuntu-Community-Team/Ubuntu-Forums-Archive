---
title: "Disable save to disk &amp; partitions"
date: 2010-08-17
forum: General Help
---

### Post by komitaltrade on 2010-08-17
If I make one NTFS partition and on other install ubuntu and enable option "disable save to disk", is it worth also for NTFS partition or just for Linux partition(s)?

---

### Post by komitaltrade on 2010-08-18
Anybody???

---

### Post by xenogia on 2010-08-18
Could you re-word your query?  Why do you want to disable write access.  It is easy done by changing permissions on the mounted drives.

---

### Post by komitaltrade on 2010-08-18
In cyber cafe is desirable to have "clean" system, but customers also want all the time to save something in hard disk.

As they like desktop users already cant change the system, that's not the problem, problem is practically home partition (but I have reasons why to keep original ubuntu recommended partitioning - one partition).

So, for me is best solution to format 10GB NTFS and let to ubuntu to install it in free space and after installation to disable save to disk in gconf-editor desktop lock-down.

P.S. If nobody don't know the answer, I should to try it.

---

### Post by xenogia on 2010-08-18
> **komitaltrade said:**
> In cyber cafe is desirable to have "clean" system, but customers also want all the time to save something in hard disk.

As they like desktop users already cant change the system, that's not the problem, problem is practically home partition (but I have reasons why to keep original ubuntu recommended partitioning - one partition).

So, for me is best solution to format 10GB NTFS and let to ubuntu to install it in free space and after installation to disable save to disk in gconf-editor desktop lock-down.

P.S. If nobody don't know the answer, I should to try it.


Why not just go into Root Nautilus and change the permissions on the folders/drives you speak of.  So they can only be written to by the admin.

---

### Post by komitaltrade on 2010-08-18
I tried it before and it create the mess in the system (it is not all files with same permissions and that disable lot of applications).

---

