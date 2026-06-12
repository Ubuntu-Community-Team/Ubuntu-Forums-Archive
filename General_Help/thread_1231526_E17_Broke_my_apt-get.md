---
title: "E17 Broke my apt-get"
date: 2009-08-04
forum: General Help
---

### Post by j.e.schroder on 2009-08-04
A couple of days ago I attempted to install Enlightenment. Being a novice Linux user, I did a quick Google search for the easiest, quickest tutorial. Well, it failed. And now when i try to install anything new, or even try to use apt-get or aptitude commands, I get:

> Unable to get Exclusive Lock
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.Update Manager gives me this error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```So I did:
```
john@LinuxBox:~$ sudo dpkg --configure -a
```Which gives me this:
```
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' doesn't exist
FAILED! Next attempt 7 in 100 seconds
```While the above is shown the title of my terminal becomes "Easy_e17.sh - FAILED"

I also tried this before dpkg configure command:
```
sudo apt-get clean all
```I have since given up on E17, this much trouble for a little bit of eye candy? 

If anyone can help, in any way... 

Thank you in advance,
John

---

### Post by paul_in_london on 2009-08-04
First look for the file **/var/lib/dpkg/lock**.

If this file exists and no package management tool is running, it is safe to remove it:

```
sudo rm -f /var/lib/dpkg/lock 
```

Then try again:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

If it still doesn't work, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=916690&page=42](http://ubuntuforums.org/showthread.php?t=916690&page=42)

---

