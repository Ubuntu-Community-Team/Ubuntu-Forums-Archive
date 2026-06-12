---
title: "Removed /var/lib/dpkg"
date: 2011-06-05
forum: General Help
---

### Post by AndyBoy_LV on 2011-06-05
Hi!

I did an unsuccessful update and got a lock un apt. But instead of removing /var/lib/dpkg/lock, i by accident removed /var/lib/dpkg. 


Yes, i don`t have backups, and i regret it very much now.


I created a new /var/lib/dpkg folder but now if i do a apt-get upgrade, it tries to install all applications, because apt thinks i dont have any. Any chance to rebuild the database?

Also, if i hit "yes" and try to reinstall them all, i get this error message: 

```
"E: Could not perform immediate configuration on 'multiarch-support'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)"
```

Any help is appreciated.

---

### Post by TeoBigusGeekus on 2011-06-05
Try
```
sudo dpkg-reconfigure -a
```

---

### Post by AndyBoy_LV on 2011-06-05
> **TeoBigusGeekus said:**
> Try
```
sudo dpkg-reconfigure -a
```

tried it, still same result. I cannot install/upgrade anything because of this error:

```
E: Could not perform immediate configuration on 'multiarch-support'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

---

### Post by ajgreeny on 2011-06-05
All I can suggest is that you run a live CD/USB of the same version of ubuntu and see if copying **/var/lib/dpkg** from there to your installed version helps.

I am pretty sure some of the data in those files and folders may be different, but it may at least mean you can use **apt-get** again

---

### Post by gmargo on 2011-06-05
Short answer:  You're toast.  Reinstall needed.

Longer answer: There's a tremendous amount of valuable, yet difficult to recreate, information stored under /var/lib/dpkg/.

A small amount of the information is backed up under /var/backups/.

Hopefully you have a separate /home partition.  
If you have enough room on the /home partition, make a copy of the root filesystem
or at least /etc/ and /var/backups/ and /var/www/.  This will help you get the same packages installed.

Then reinstall.

Believe me, it will take no time at all to reinstall, compared to time spent trying to recreate all that info.  Plus you'll never be sure it's correct.

---

### Post by AndyBoy_LV on 2011-06-28
Ok, fixed it by installing Xubuntu lol :)

---

