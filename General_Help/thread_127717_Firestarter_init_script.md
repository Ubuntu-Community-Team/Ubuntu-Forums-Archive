---
title: "Firestarter init script"
date: 2006-02-09
forum: General Help
---

### Post by theolster on 2006-02-09
I'm a bit of a newbie, and my only Linux experience is with Fedora.
I'm trying to set up a server with Apache, PHP, MySQL, FTP etc... and all of that is working fine.  So long as I have firestarter running.

But the only way to get firestarter running is to log in.  Since I only occasionally log in remotely (by VNC) i don't really want to have a setup where after every reboot the default user is automatically logged in.  This just messes up the VNC login process (unless the users are different)

I have looked through the forums here, I've tried BUM, and have tried the following non-Ubuntu guides to getting this working:
[http://www.fs-security.com/docs/installation.php#initscript]("http://www.fs-security.com/docs/installation.php#initscript")
and [http://www.linux-tip.net/cms/content/view/157/6/]("http://www.linux-tip.net/cms/content/view/157/6/")
But these rely on chkconfig which Ubuntu does not use.

Has anyone got any ideas?  I'd really like to get firestarter working as a service, but I suspect it was not designed to do that.  Help!

Regards,
Ollie

---

### Post by theolster on 2006-02-10
I have been reading around, and it seems that I just need the following script which should have been installed automatically originally but wasn't:
etc/init.d/firestarter

could someone post the contents of this file so that I can create it myself?
will this work?
help?

---

