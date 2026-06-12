---
title: "read only"
date: 2009-11-18
forum: General Help
---

### Post by carcar1 on 2009-11-18
My Ubuntu locked me out of all files in my entire "/" drive so where Ubuntu is installed.  Its all locked out after using :gksudo natilus: and changing all folders and sub folders to go to my user name instead of root where it was.  And still no luck I need a fix please.  Its an acer aspire 5100 laptop and this just happened today. In ubuntu 9.10

---

### Post by emigrant on 2009-11-18
ghhhhrrrrrrr
why did you do that man?
i think you got to backup your data and reinstall. not sure though lets wait for a geek.

---

### Post by carcar1 on 2009-11-18
Might I say that its a server on top of a desktop and reinstalling is not fun.

---

### Post by 3rdalbum on 2009-11-18
Did you change the permissions of your drive, and that caused the problem? Or did you get the problem and decide to try and fix it by changing all the permissions? Your post is unclear.

I'm not so good at reading permissions, but someone else might be able to help if you can post the output of:

```
ls -la /
```

---

### Post by Cheesemill on 2009-11-18
+1 for reinstallation and restoring your files from backup.

It will be so much quicker than fixing your current install (if it's even possible).

---

### Post by unamanic on 2009-11-18
If you did what I think you are saying, you are in bad shape, hope you have a backup.  

You said its a server on top of a desktop, what services are you running?  If it's just a standard LAMP server, you'll want to fire up a live cd and copy off /var/www /var/lib/mysql and /etc as well as your /home directory to external media.  /var/www and /var/lib/mysql can be droped back in place after a reinstall, but /var/lib/mysql MUST have mysql:mysql (user and group for it's files and sub files)

---

### Post by fluffman86 on 2009-11-18
Try booting into recovery mode, and booting into a Root Shell.  You can use the command

chown -R root:root /

To make everything belong to root.

Then use:

chown -R carcar:carcar /home/carcar/

To reclaim your home directory and do the same for any other home directories as well.

edit: Wow, I take a long time to type. :P  I can't believe everyone wants a reinstall.  As long as he didn't mess up his sudoers file or something, he'll be fine.  It'll just take some finagling at the shell to get things back.

---

### Post by unamanic on 2009-11-18
> **fluffman86 said:**
> Try booting into recovery mode, and booting into a Root Shell.  You can use the command

chown -R root:root /

To make everything belong to root.

Then use:

chown -R carcar:carcar /home/carcar/

To reclaim your home directory and do the same for any other home directories as well.

This may get the system to boot, but the real kicker is /var It can take forever to get it back correctly.

---

### Post by carcar1 on 2009-11-19
Thanks fluffman86 you saved my life a good 4 hours of configuring a fresh install thanks.  It work except for proc which I never go into.  And the orignial problem was writing to folders except home.

---

