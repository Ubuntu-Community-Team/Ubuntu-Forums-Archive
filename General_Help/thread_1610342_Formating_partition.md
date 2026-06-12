---
title: "Formating partition"
date: 2010-10-31
forum: General Help
---

### Post by banquo on 2010-10-31
Hello everyone!
Something went wrong during my upgrade, and i was unable to boot.
What I did to save the day was to install Lucid parallel (on an other partition).
Now I just want to double-check before I mess up again -
I've backup-ed all the stuff i wanna keep and want to **format the old partition**. preferably I'd like to extend my current partition to the whole drive (or just make an empty partition for media if that works).

**So how do I do this the easiest way, and what would be the best option (i.e. 1 or 2 partts.)?**

thanks in advance!

// Oskar

---

### Post by sanderd17 on 2010-10-31
extending your partition is always a little danger. If you want that, you need to boot a live CD and run gparted.

If you want to have a separate media partiton, you need to format it via gparted (no need for a live CD since you won't change the partitions of your installation). Then, you can edit your fstab file to have the partition mounted under /home/user/media or something like that. To change your fstab file: look [here]("http://ubuntuforums.org/showpost.php?p=8631122&postcount=7").

Oh, and if you don't really need that space, you can leave it that way for the next release. I always have 2 ubuntu installs: one current and one old. That way, if the current breaks (or the installation failed), I can go back to the old.

---

