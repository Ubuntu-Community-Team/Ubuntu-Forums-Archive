---
title: "Really messed up system"
date: 2006-02-08
forum: General Help
---

### Post by BrejoSacor on 2006-02-08
I hope i can get some support on this... no luck fixing it myself so far.
I have:
Dell Ispiron 9100
Ati radeon 9700
1024mb RAM
Breezy Badger
Windows XP Pro

First off, I am having problems with a few things, i think that the best thing to do is just rollback the kernel, and i have no idea how to.  Or i can always just reinstall Ubuntu, but thought i might be able to get help here first.  I am very new to linux and have not quite yet figured out everything so anything would be great.

Problems:
    Internet is sketchy, some pages will never load, and some will just load randomly.  Google for instance rarely works, or the Firefox Google page/built in google search is sometimes not working.  Gmail rarely loads either.
     Also, my Add Applications does not work at all, it doesn't load after asking for password.  And my C compiler doesn't work either.

Well there it is.  Also, how do i set my priviledges to be like root all the time, such as accessing the file system.

---

### Post by Robor on 2006-02-08
Did everything work fine before the kernel upgrade?  If so, when the system is booting you should see a boot menu (I think it displays for 10 seconds by default).  When it does simply choose (arrow down to and hit enter) the previous kernel instead of the one you updated to.

I don't know how to set everything to run as root/superuser all the time.  When I first started using Ubuntu I asked the same question and was told a) it's not a good idea for system protection/security and b) it would likely cause problems.  After all, it's not that hard to do a 'sudo' before stuff on the command line.

---

