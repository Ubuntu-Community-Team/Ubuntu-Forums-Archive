---
title: "nautilus goes to 100% cpu when ntfs in fstab"
date: 2010-10-11
forum: General Help
---

### Post by TeutonJon78 on 2010-10-11
I've just been installing Maverick on my computers, and one of them seems to be having a problem.  I am dual-booting WinXP and Ubuntu.

If I just mount my NTFS partitions manually, there is no problem.  However, when I put them in the fstab file, nautilus takes up 100% cpu on the next boot.  It will share the cpu with other tasks still, but it eats up an available cpu.  The whole system is running sluggish.

options=defaults,uid=1000,gid=46 -- but I also just tried "defaults")

I tried installing the new ntfs-3g driver (ntfs-3g-2010.10.2 with the same result.  If then remove it from the fstab and reboot, everything works again.  I've tried reinstalling the whole system -- no change.  I also tried a "sudo apt-get purge nautilus && sudo apt-get install nautilus" to no avail.

Some something is happening different between the way the volumes get mounted in fstab and in gnome that is freaking nautilus out.  Any ideas?

---

### Post by |{urse on 2010-10-11
Perhaps your ntfs partition is fragmented or there is a bad sector that is being worked out differently when mounted manually?

---

### Post by TeutonJon78 on 2010-10-11
> **|{urse said:**
> Perhaps your ntfs partition is fragmented or there is a bad sector that is being worked out differently when mounted manually?

Hmmm, well it happens with two separate drives.  I've tried mounting them separately and it still happened.  I also defragged the drives and did a chkdsk on them between the two install attempts.

I could do a check for bad sectors though, I haven't explicitly done that yet.

---

### Post by |{urse on 2010-10-11
Might want to wait on that, seems unlikely now that I think about it. Back to google, I'll let you know if anything looks similar.

---

### Post by TeutonJon78 on 2010-10-13
Any ideas out there forumites?  Or perhaps better, yet, any debugging info on nautilus so I can determine where/why it's looping?

---

### Post by TeutonJon78 on 2010-10-13
Huzzah!!!  I dusted off my debugging skills and traced it down myself.

I had one mistake -- I was able to mount the first drive no problem.  It was the second drive that was causing the loop.  Did a bad sector test, and no problems there at all.

I did a little gdb magic on nautilus and saw that it was getting stuck in the add_templates_to_templates_menu function.

The culprit -  had generated a symbolic link in the user Templates directory that linked to that drives root.  Hence, it was trying to add the contents of the whole drive to the templates.

I removed the symlink and everything is working now.

---

