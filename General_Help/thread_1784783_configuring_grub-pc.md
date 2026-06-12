---
title: "configuring grub-pc"
date: 2011-06-17
forum: General Help
---

### Post by benpack101 on 2011-06-17
I am running Ubuntu 10.10 (64bit) and I went to update my computer this morning and I ran across this:

 Configuring grub-pc
 A new version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified.

What do you want to do about modified configuration file grub?
                                                         install the package maintainer's version                              keep the local version currently installed                         show the differences between the versions                                 show a side-by-side difference between the versions                        show a 3-way difference between available versions                         do a 3-way merge between available versions (experimental)                 
start a new shell to examine the situation 

I am not sure what I should do here.

---

### Post by oldfred on 2011-06-17
Having been burned by not installing package maintainer's version, and having to leap thru hoops to get it to work (not just grub but other systems also), I always choose the maintainer's version. But if I manually maintain something, I try to remember to copy it into a folder in my /home so I have a copy that gets backed up as part of my normal backups of /home.

If you know what changes you made or can easily reproduce them choose package maintainer's version. Otherwise you may have issues as sometimes they change a lot and old version does not work at all.

---

### Post by benpack101 on 2011-06-17
I believe all I might have changed was the default OS - so I am going to go with package maintainer's version. Thanks!

---

