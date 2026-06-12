---
title: "Install Ubuntu only and keep Windows partition"
date: 2011-03-27
forum: General Help
---

### Post by beah11 on 2011-03-27
Hi, I have a DELL 500 with a most probably fake "Windows" XP or 7 on it. I had my computer reinstalled by a friend in Indonesia, and now I am having too many problems. I want to use rather Ubuntu. I have too partitions in Windows, C: and D:, D: has all my personal data. How could I install Ubuntu and keep the data D: has, or keep the same partition without making a copy of it or keeping the Windows?

Thanks in advance for your time and help :)

---

### Post by mikewhatever on 2011-03-27
The installer will, automagically, offer to make space for Ubuntu by resizing one of the existing partitions.

---

### Post by Krytarik on 2011-03-27
If I got you right, you want to
- format the first partition, C: and use it for Ubuntu
- keep the second partition, D:

That's fairly easy:
- choose "Specify partitions manually" in the installer
- delete the first partition
- create a swap partition, at least of the size of the installed RAM
- create the root partition
- maybe create a dedicated home partition (useful for later re-installs)
- specify the mount point for the second partition

For details/screenshots see this guide:
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Greetings.

---

### Post by beah11 on 2011-03-28
Thank you very much for the quick response guys! I will try and see how it goes, I might come back with more questions :)

---

