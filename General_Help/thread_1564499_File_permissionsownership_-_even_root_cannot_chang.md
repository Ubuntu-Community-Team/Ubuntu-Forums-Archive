---
title: "File permissions/ownership - even root cannot change"
date: 2010-08-30
forum: General Help
---

### Post by Martyn Thompson on 2010-08-30
Dear all,

I have been VERY lucky and managed to restore from a formatted ext3 /home/ partition.  I used testdisk to reset the original partition which had had nothing done to it since formatting(!). 

However some of the file permissions are a altered and I cannot  change them.  I have tried "su chmod" and even temporarily enabled the root account itself and tried to alter the ownership/permissions from root 'proper' without it helping. 

Here is an example of the output of ls -l

drwxr-xr-x 2 martyn martyn 4096 (date) (time) sponsors
?-----S--T 63231  92820383 44090688 4286824785 (date) (time) order.xls



The first line looks like a normally formed output and indeed is readable.  The second line looks corrupted and I don't have a clue how I can reclaim this - or even if it is possible. 

Should I count my blessings most of my files are intact and leave those be?  

Any advice would be welcomed. 


Martyn

---

### Post by ajgreeny on 2010-08-30
Ubuntu does not use "su" as most other distros do, but "sudo" instead, so try ```
sudo chmod etc etc
```I am surprised, however, that the temporarily enabled root account did not do the job; are you sure that it really was a root account?

Please bear in mind that discussions about enabling root are not generally allowed in this forum so any further info about what you did may be a bit difficult.

---

### Post by Old *ix Geek on 2010-08-30
> **Martyn Thompson said:**
> I have tried "su chmod"First of all, another reply said that su doesn't work with Ubuntu--yes it does. It's a *nix command and I've never seen a *nix distro where it didn't work.

However, what you've done:
```
su chmod
```
is saying, "log in as user chmod"--and of course that's not what you're trying to do. Don't confuse the usage of su and sudo. With su, you supply the user's name that you want to log in as; with sudo, you supply the command you want to run as root.

Anyway, I've seen something like this before:
> Here is an example of the output of ls -l

drwxr-xr-x 2 martyn martyn 4096 (date) (time) sponsors
?-----S--T 63231  92820383 44090688 4286824785 (date) (time) order.xls

*scratching my head trying to remember how I fixed it*

Try running chmod again and post any output/errors you get.

---

