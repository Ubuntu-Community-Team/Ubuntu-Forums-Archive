---
title: "the 5% question"
date: 2009-10-23
forum: General Help
---

### Post by tiras_dude on 2009-10-23
For the longest time I could not figure out why my free space in Ubuntu never matched available space.

Eventually I discovered that 5% of any file system except for swap is reserved for root. 

A bit later I also discovered that the 5% could be increased or reduced with a command like this:  sudo tune2fs -m Y /dev/sdxX 
where:
Y is your reserve percentage expressed as a number (eg  1 if you want 1%)
x is your a,b,c or whatever drive it is
X is your partition number (1, 2, or whatever)

Here are the questions:

a. What is a real optimal reserve for /home partition if I have separate /boot, /, and /home partitions and there are no other users besides myself on the laptop, and why?

b. What would be the optimal reserve for an external 1 TB back up drive with ext4? 5% for root which amounts to 50 gigs sounds like an overkill.

c. Why is that reserve there in the first place?

---

### Post by scragar on 2009-10-23
a. For /home I'd say 0%, root has /root which you won't touch if you need root, so ignore it all together.

b. Backups shouldn't need any extra space either, go for 0%.

c. Right, you as a user use up all your space, but now you have trouble doing anything, to open anything GNOME records the file name, so you can't open anything with errors, attempting to run commands throws more errors from bash_history... That is why root has the allowance, root may log in and reduce the space used without having to worry about the limit itself.

As long as you are aware of the limit yourself and make sure to give yourself a bit of free space it's fine to remove the limit all together, but the tiny amount of reserved space is essential in shared enviroments where most users don't care about free space.

---

### Post by tiras_dude on 2009-10-23
Thank you!

---

