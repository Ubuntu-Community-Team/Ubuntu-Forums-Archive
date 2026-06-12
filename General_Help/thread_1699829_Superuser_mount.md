---
title: "Superuser mount"
date: 2011-03-04
forum: General Help
---

### Post by pluMmet on 2011-03-04
I'm having trouble getting Wine to see the Hardware ID of my USB so I'm trying to mount it as a Superuser.

When I use 'sudo umount /dev/sbd1 /media/88E5-98BA' the drive unmounts.

then I use 'sudo mount /dev/sbd1 /media/88E5-98BA' and it says "mount point /media/88E5-98BA does not exist"

how do I mount this USB as a super user?

---

### Post by pluMmet on 2011-03-04
I've taken further steps that I thought would work but did not.

I went to gconf-editor and turned off media_automount then I used Thunar to mount the USB as root.

Still Wine does not see the Hardware ID of the USB :confused:

---

