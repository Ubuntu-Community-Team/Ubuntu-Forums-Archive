---
title: "Grub error 18 after install of Jaunty alongside Lucid"
date: 2010-04-11
forum: General Help
---

### Post by Duncan J Murray on 2010-04-11
If anyone is able to give any pointers on this one, it would be much appreciated.

I had installed Lucid on a clean install on my laptop - three partitions - ext4 home, ext4 lucid and swap.

I've been using it for around a week, and find it a bit buggy in places, so I thought I would install jaunty (which proved very reliable in the past).  I used the usual installer, and made my /home partition smaller, and created a new ext3 partition for jaunty, assigning the smaller partition to /home.

The install proceded without any problems, but on rebooting I just get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 18


I was hoping that Jaunty would not install grub, but I didn't see any option to prevent this during the installation.  I suspect Grub 1.5 has been installed and now it's all messed up!

Any help MUCH appreciated, as laptop is currently a brick.

Thanks!

Duncan.

---

### Post by Duncan J Murray on 2010-04-11
Looks like Grub 0.97 overwrote Grub 1.96, and it is unable to recognise a partition which isn't the first one (bios woes).  It also didn't seem to recognise Lucid.  I think the only solution is to reinstall Lucid or Jaunty...!  I did try reinstalling Grub 2, but it didn't work.

Duncan.

---

### Post by oldfred on 2010-04-11
Is this an older computer with a newer larger hard drive? Error 18 is trying to boot from beyond the BIOS limits.
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

