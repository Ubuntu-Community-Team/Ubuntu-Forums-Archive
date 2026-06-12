---
title: "Local webserver"
date: 2010-11-17
forum: General Help
---

### Post by Tata1955 on 2010-11-17
I have been working a couple of years in Windows of all versions. Working in webdesign area, I used to have installed WAMP as my local webserver. So I could test all PHP based webpages locally without a need to upload them first to my external host.
Now I have install ubuntu as my second OS (so still have fully customized Win7 and ubuntu 10 installed as a dual boot). I have WAMP 2 (Apache,PHP, MySQL) installed under Win7 and a specified partition for my localhost.
Is there a way how I could access webpages stored in this partition from ubuntu?

---

### Post by MrRichard on 2010-11-17
> **Tata1955 said:**
> Is there a way how I could access webpages stored in this partition from ubuntu?

You bet :D

There's a program for Windows, called ext2explorer. It's a .exe file that can be placed and used just about anywhere in Windows. The program simply opens up a file manager of its own. Very easy to use, and so far, bug free.

---

### Post by SeijiSensei on 2010-11-17
Actually it sounds like he or she is interested in the reverse situation, using files from his Windows partition(s) in Linux.

You can just mount the partitions into the directory tree and reference them as, for instance, /windows/Documents and Settings/.  You may need to play around with file permissions, though, as the Apache server in Ubuntu runs as the "www-data" user.  That user needs to be able to read the files on the Windows side.  The simplest, but least secure, method is to give the mount point (e.g, "/windows") 0777 privileges.  I told Ubuntu to mount my NTFS partition during installation of my 10.10 workstation.  It assigned /windows to root with group plugdev and 0770 privileges, and added me to the plugdev group.  That may not be sufficient for Apache to see those files, though you could solve that by adding user www-data to the plugdev group.

---

