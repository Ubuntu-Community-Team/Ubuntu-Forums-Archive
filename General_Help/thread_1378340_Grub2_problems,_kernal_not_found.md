---
title: "Grub2 problems, kernal not found"
date: 2010-01-11
forum: General Help
---

### Post by eyeteeth on 2010-01-11
I have (or had) Ubuntu 9.10 residing on my Dell laptop within Windows Vista. (shudder) Not a true dual boot.

Several days ago, the laptop froze, and Grub.cfg was damaged, lost, deleted... something.  I was able to manually load the kernal and boot back into Linux.

From previous searches for solutions to rebuilding grub.cfg, I ran ubuntu update, which didn't solve the problem, then later ran sudo update-grub in an attempt to fix grub.  It said I needed to reboot to complete, which I have done.

But now I can no longer even manually boot in Grub.  I get the error message kernal not found.  So... I am becoming a bit more desperate as I seem to dig myself deeper, and as a semi-geek but linux newbie, I figure its better to reach out for suggestions.  I am hoping the current Ubuntu installation can be saved without starting over.  At the very least... if there is a means of accessing the files from Vista (..ubuntu/disks/root.disk) so I can get to the docs before starting from scratch.  The 9.10 installation CD won't try to repair this installation saying I need to delete and reinstall.

Thank-you

---

### Post by Sylslay on 2010-01-11
update-grub2
apt-get install os-prober
os-prober

But how You boot linux now?

---

### Post by eyeteeth on 2010-01-11
That's the big part of the problem at this point, I can't get to linux with my limited knowledge.  I'm sure running it from 'within' windows isn't adding ANY complications to trouble shooting this either. lol.  It would be much easier if i could at least access the file system.

---

### Post by meierfra. on 2010-01-11
You might be hit by a bug in Grub2's ntfs module. If yes, this should  fix your problem:

Boot into Windows and follows these instruction from the author of Wubi:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by eyeteeth on 2010-01-12
meierfra.

Excellent, your recommended link solved it perfectly. 

I was certain the freeze had something to do with my problems thinking it corrupted something.  (Old windows ways die hard)  Thank-you for seeing past that and being able to relate the remaining symptoms to a simple correction.  Highly appreciated and impressed.

Being new to the community, is there a process/utility I should report the issue and correction to to help with any development or fixes?

---

