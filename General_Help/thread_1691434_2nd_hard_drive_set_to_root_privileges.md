---
title: "2nd hard drive set to root privileges"
date: 2011-02-19
forum: General Help
---

### Post by cswenson on 2011-02-19
I have a dual-boot system Vista/Ubuntu 10.10 with both OSes on a single drive and then a 2nd shared drive for storing files (formatted as NTFS).

Ever since I upgraded to 10.10 from 10.04, the the owner of the 2nd drive has been set to 'root'.  I'm not sure how it happened, but it is annoying as heck.  I can still interact with the drive through nautilus, but I can't write using the terminal or any program (i.e. 'File'->'Save' doesn't work, I get a permissions error).  I've tried a 'chown', but that doesn't work.

Anyone know how this happened?  What do I need to do to take back my hard drive?

Thanks.

---

### Post by TheHackOps on 2011-02-19
chmod 777 /dev/sda1

---

