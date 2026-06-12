---
title: "Disk gone"
date: 2011-10-15
forum: General Help
---

### Post by rugile on 2011-10-15
Hi,

I am completely new to Ubuntu and I have already faced a problem. I installed Ubuntu using Wubi and where I had to choose on which disk I want to install Ubuntu I chose disk H. And now I can't find that disk when I'm on Ubuntu. I mean I can see only three other disks I have (C, D and F) and also Filesystem, but not H disk. Am I right that that H disk is Filesystem? Then how can I access those files I had on H disk (my music, for example)? 

Thanks in advance. :)

---

### Post by 3rdalbum on 2011-10-15
Your Wubi installation is sitting in a file on the "H" disk (note: drive letters only make sense in MS-DOS and Windows, not in any other operating systems).

So, "Filesystem" is the contents of that file on the H disk. To get to the contents of the H disk directly, go to Filesystem and then double-click on the folder called 'host' in there.

/host/

This contains the contents of the host disk. It *is* the host disk.

---

### Post by rugile on 2011-10-16
Thank you. :)

---

