---
title: "can't man or tar anything- too many levels of symbolic links"
date: 2010-04-14
forum: General Help
---

### Post by daweefolk on 2010-04-14
I'm trying to build LFS (linux from scratch) and when i try untarring a file it tells me "too many levels of symbolic links". i thought it was my tar command so i tried man tar. "can't exedcute pager: too many levels of symbolic links".
What's going on? how do i fix it?
I'm running ubuntu 9.10 right now

---

### Post by Brandon Williams on 2010-04-14
It sounds like you probably have a circular symbolic link somewhere. To fix it, you'll have to find it, and running commands to do so might not be very helpful. It's probably an issue with either /usr/bin or /bin (since it impacts pager), so look there first. Once you find the circular link (if that's really what it is), we can give better advice about the specific fix.

---

### Post by daweefolk on 2010-04-15
well after doing a reinstall using wubi, i restarted and while scanning the book during all the wgets i found where i screwed up. last time i was just in the habit of entering any code i saw. i didn't realize i made an extra symlink for 64 bit only systems. whoops. Learned my lesson, lol

---

