---
title: "GParted resizing partition: safe?"
date: 2011-04-13
forum: General Help
---

### Post by Nonno Bassotto on 2011-04-13
I am currently using Ubuntu 10.04, and my partitions are set up as follows:

-Extended partition
--12 Gb Ext3 as /
--4.5 Gb swap as swap
--134 Gb Ext3 as /home
-9.6 Gb NTFS usually unmounted (recovery partition)

I would like to try Ubuntu 11.04 with the Gnome3 repositories, or possibly Fedora 15. If it turns out I can work well with Gnome 3, I would like to delete my current Ubuntu 10.04 install and use the new one instead. At the same time, I would like to decrease the number of dotfiles accumulated in my home through 3 updates.

My plan is the following:

1. Disinstall some stuff to make free space on / (currently only 3.6 Gb are free)
2. Move content of the first partition to the end of the partition - this means losing GRUB
3. Resize the first partition to make free space on the head of it
4. Create a new Ext4 partition in the free space
5. Install Ubuntu 11.04 there, keeping the home on the same small volume. In the process, reinstall Grub. I will have access to files in the old home as a separate partition.
6. Slowly copy only the needed dotfiles from the old home to the new one.

(Assuming I actually like the new Gnome 3)
7. Remove all dotfiles from the old home, and copy back the new dotfiles from the new temporary home
8. Change the home for the new system to the 134 Gb partition, and remove the /home folder from the first partition
9. Remove the old / partition
10. Resize the new / (Ext4) partition to make use of the new free space


It seems a lot of work, and a lot of things could go bad. I am not even sure that GParted can move the contents of a partition (including the MBR!) to the end, so that I get free space at the beginning. So my question is double.

Is my plan actually doable? Is it safe? I will do backups prior to any disruptive operations, but it a pain anyway to lose a functional system for a while.

Is there a simpler way to move to Ubuntu 11.04, keeping in mind that I want to have a fully functional system at any time, that I want to be able to go back to 10.04 should Gnome 3 prove to be not as nice, and that I do not want to mix the home folders for the two systems, as they may have incompatible configuration files?

---

### Post by dragonfly41 on 2011-04-13
I don't understand why you can't just go out and buy an external USB drive to be bootable 11.04?    Cost?

---

### Post by pqwoerituytrueiwoq on 2011-04-13
there is a chance of something going wrong resulting in data loss
i know moving windows results in having to fix it crummy boot loader i *think* Linux is fine if moved 
it is recommended you keep a backup of anything that is not replaceable

---

### Post by coldraven on 2011-04-14
I just used Gparted to resize my main 240GB ext4 partition. (root)
It worked fine even though I made the mistake of shutting the laptop lid which sent the PC into suspend during the resizing. Stupid idea on a live CD to have that as the default option.
Anyway I installed Natty Beta 1 on the free space and it works OK apart from Compiz crashing quite often.
The graphics are very fast and smoother than 10.10 so I might keep it when it becomes more stable.

---

