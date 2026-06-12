---
title: "Lost HardDrive Space"
date: 2009-11-15
forum: General Help
---

### Post by oversky on 2009-11-15
My harddrive was running low and only 106 MB was left.
I decided to uninstall evolution in Synaptic Package Manager,
and it said 56.7 MB of extra space will be freed.
But after uninstall, the free space only increased to 119 MB,
which should be 162.7 MB by math.

The same thing happened to install new software.
I installed gcin and Synaptic said 28 MB of extra space will be used,
and 9 MB of files have to be downloaded.
So it should be 119 - 28 - 9 = 82 MB.
But the result is only 54 MB left.
After a apt-get clean, I gained 9 MB back.

I am using Ubuntu 9.10. Is this a bug, or just a bad config?

---

### Post by scragar on 2009-11-15
The space needed is based on the files to be installed, there are two configuration scripts, one for preparing the install, one for finishing the install, depending on what these do the total isntalled size could be very different.

---

### Post by ajgreeny on 2009-11-15
Uninstalling evolution will not remove all the personal files etc in your home partition.  If you have used evolution in the past for email etc etc, there could be a lot of disk space used by the ~/.evolution folder.

---

