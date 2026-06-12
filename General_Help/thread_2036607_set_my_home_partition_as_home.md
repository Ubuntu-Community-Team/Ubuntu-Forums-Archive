---
title: "set my /home partition as home?"
date: 2012-08-02
forum: General Help
---

### Post by ELD on 2012-08-02
Okay guys i somehow did a booboo

I made a partition for /home but when installing didn't set it to be used as /home so now my main partition has /home

Is there a way to move all of /home to the partition i made and have that be used as /home ?

---

### Post by Lars Noodén on 2012-08-02
Yes, it can be done easily.  I've done that lots of times when I do a fresh install of the OS but leave the old /home untouched.  But I wonder if I can explain it coherently.  

Make a backup copy of /etc/fstab first.  

Once the new partition is formatted, log out of the graphical system and log in via the console (e.g. ctrl-alt-f2)  If you need to copy stuff from the old /home, mount the new partition under /mnt and use [tar](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html) to copy things over.  Then unmount /mnt and edit /etc/fstab to reflect the new /home.  Then mount /home

If you need to get the UUID for the device containing the new /home, use [blkid](http://manpages.ubuntu.com/manpages/precise/en/man8/blkid.8.html).

---

### Post by oldfred on 2012-08-02
More details here, but Lars has it correct.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ELD on 2012-08-03
> **oldfred said:**
> More details here, but Lars has it correct.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

That did it cheers.

---

