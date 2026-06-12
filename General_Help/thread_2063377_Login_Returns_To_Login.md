---
title: "Login Returns To Login"
date: 2012-09-26
forum: General Help
---

### Post by Xaotique on 2012-09-26
I removed ecryptfs with the instructions from ecryptfs-setup-private --undo and now when I try to log in, in graphical mode, it returns to the login screen.  When I login to command mode, I get no errors, and I log into the home folder.  I can see all files and whatnot with ls -al.

Also, when I'm in graphical mode at the login screen, it shows my background .. if that's meaningful at all.  The permissions of /home/tom are 755.  I tried chown to tom instead of root, but it didn't help.  It's 755 permission, then tom owner, then root, then the folder tom when looking at ls -al /home.

Any ideas?

---

### Post by Xaotique on 2012-09-26
Ok, changed owner to tom:tom, though it didn't help at all.  I tried adding a user with /home/tom as the home folder, and changed ownership over to tom, and it wouldn't work either.

I have no idea what's wrong. :(

---

### Post by Xaotique on 2012-09-27
In hopes it may help anyone .. the problem was the Xauthority file permissions needed chown from root to my user.  I just did a recursive chown tom:tom to the home foler, and we're back in business.

I don't know if this has to do with the home folder issues, but lightdm froze during boot up, so I installed gdm and set it as default and I was able to log in.  Purged lightdm, autoremove + clean, then installed again.  Set it to default, reboot, and everything is working correctly now.

Bye (:

---

### Post by Rexilion on 2012-09-27
Best not to do 755 on your home folder. You don't want the world readable bit + exec bit set on your home folder. More sensible would be:

770 for home folders
660 for home files
770 for home files that should be executed (not recommended)

So that makes

```
find /home/tom -print0 | xargs -0 chown -h tom:tom
find /home/tom -type f ! -type l -print0 | xargs -0 chmod 660
find /home/tom -type d -print0 | xargs -0 chmod 770
```

---

### Post by Xaotique on 2012-09-28
Thanks for that Rex.

---

