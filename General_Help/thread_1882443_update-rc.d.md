---
title: "update-rc.d"
date: 2011-11-17
forum: General Help
---

### Post by orrymr on 2011-11-17
Just looking at this program, and from what I understand I can use it to add/remove symlinks in my init.d directory. Which runlevel does it add/remove the symlink for - is it the current runlevel I'm using?

---

### Post by raja.genupula on 2011-11-17
basically what i know is update-rc.d is going to use for managing services 

look at this

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

[http://manpages.ubuntu.com/manpages/hardy/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/update-rc.d.8.html)

---

### Post by hg088 on 2011-11-17
u could try this one "sysv-rc-conf". it in the repos

---

### Post by Lars Noodén on 2011-11-17
> **orrymr said:**
> Just looking at this program, and from what I understand I can use it to add/remove symlinks in my init.d directory. Which runlevel does it add/remove the symlink for - is it the current runlevel I'm using?

It does it for all run levels.  The main copy of the script is in /etc/init.d and a symlink will be made in the directories rc0.d - rc6.d and rcS.d.  The number after 'rc' corresponds to the run level.  Generally only runlevel 2 is used.  [telinit](http://manpages.ubuntu.com/manpages/precise/en/man8/telinit.8.html) is the program that can change runlevels for you.

---

### Post by orrymr on 2011-11-17
Thanks raja, that first link was great

> **Lars Noodén said:**
> It does it for all run levels.  The main copy of the script is in /etc/init.d and a symlink will be made in the directories rc0.d - rc6.d and rcS.d.  The number after 'rc' corresponds to the run level.  Generally only runlevel 2 is used.  [telinit]("http://manpages.ubuntu.com/manpages/precise/en/man8/telinit.8.html") is the program that can change runlevels for you.

so, if I understand correctly, the command 'telinit 2' for example, will close gnome (or whichever window manager) and take me to command line?

---

### Post by Lars Noodén on 2011-11-17
> **orrymr said:**
> so, if I understand correctly, the command 'telinit 2' for example, will close gnome (or whichever window manager) and take me to command line?

'telinit 2' will take you to runlevel 2.  That is it run all the scripts in /etc/rc2.d/ in numeric order.  It will kill all services linked with K in the name and start all services with S in the name.  

An increasing number of services can use upstart also.

---

