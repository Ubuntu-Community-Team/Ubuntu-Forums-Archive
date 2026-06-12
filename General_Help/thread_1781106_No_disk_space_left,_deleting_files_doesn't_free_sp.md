---
title: "No disk space left, deleting files doesn't free space"
date: 2011-06-13
forum: General Help
---

### Post by InkyDinky on 2011-06-13
A process filled the HDD while performing a kernel upgrade. I then couldn't graphically log in although there was a gui login (but not the normal one, the theme was different)
I attempted to delete files but whenever I rm'ed a file it didn't seem to show up as freeing up space when I checked with df.
I even logged in as root on tty1 as well as using the failsafe kernel.
Each time my attempt to free space by deleting files didn't seem to work.
Why couldn't I rm files? Is there a solution?

I "solved" the problem by changing the reserved space for root (tune2fs) to give myself some space to work.  I then was able to graphically log into Gnome and delete some files and free up some space. I then put my reserve space for root back so I have a way out in the future.
However I'm a little concerned as to how I'd have solved this problem had I not had the reserve space trick up my sleeve. 
Thoughts & suggestions appreciated.

-Nick

---

