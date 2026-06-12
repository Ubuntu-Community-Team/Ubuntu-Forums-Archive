---
title: "fix permissions"
date: 2011-08-21
forum: General Help
---

### Post by watgrad on 2011-08-21
Hello - I need help with one of the user account on my ubuntu 11.04 install.  I have a separate account for my children to use and somehow the permissions in their home folder are messed up.

I notice this when I use Back In Time to create backup images - it always completes with permissions errors for their account.

In Mac OS X and on android there are programs that can be used to scan and fix file permission settings.  Does such a tool exist in ubuntu?  Or is there a terminal command or script that could be used to check and fix permissions?  I am aware of chown, but don't want to have to do that for each and every error in the log...
Any help would be appreciated.


I've attached the error log from Back In Time if it helps...

---

### Post by Wayne_V on 2011-08-21
If you are not running your back up as root those are not errors.  One user should not be able to necessarily read another users files.

If you must run your backup as a regular user and back up files from another user as well make sure both users are in the same group (id <user>) and then make sure group read permissions are enabled (chmod -R g+r ~<user>)

---

### Post by watgrad on 2011-08-21
Thanks for the reply - running the backups as root and including the home folder as part oft he back up image solved the problem.

---

