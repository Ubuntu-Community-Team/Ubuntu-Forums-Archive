---
title: "X won't start after partition resizing"
date: 2012-05-12
forum: General Help
---

### Post by crw4096 on 2012-05-12
Hi,

I decided I didn't want to have a swap partition because I've got an ungodly amount of RAM, so I wanted to reclaim the 16 GB.  I booted from my Ubuntu install disk and ran gparted.  I deleted the swap and resized the root partition to take the rest of the disk.  This seemed to work out ok - all files are still where they should be (my home dir, other stuff).

Then, after reboot, the machine doesn't come up in X.  I can log in to the console, run commands, see that all disks have mounted properly, etc.  Just doesn't seem to start Xconsole.

Any ideas?  I'd be happy to supply whatever information you think would be useful.

Thanks,

Charles

---

### Post by llamabr on 2012-05-12
That old 'twice as much ram as you have' rule no longer makes any sense, but you should still keep a swap partition.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by crw4096 on 2012-05-12
Well, thanks for the link, but the partition's gone now, and I don't think bringing it back will fix my problem.  And anyway, if I do need one, I want it on a different disk.

Really hope I don't have to reinstall everything, but if that's what it takes, I guess I will.  Seems like a simple problem to solve for the person who understands how upstart works...

---

