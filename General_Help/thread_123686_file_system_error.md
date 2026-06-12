---
title: "file system error"
date: 2006-01-30
forum: General Help
---

### Post by emerick7 on 2006-01-30
I just got my computer back up and running after a file system error. I was wondering what would cause this, so here's how it happened: I had my computer on after school to check email, everything working fine.  Then about an hour later I came back and went to open up firefox and got an error about a problem with the file system.  I tried a few other apps but had no luck, so I rebooted. During the system file check, it hung on that for a while then did some other check on it.  I then got something like this:

> /data contains a file system with errors, check forced.
Error reading block 77000497(Attempt to read block from
file system resulted in short read) while doing inode scan.

/data: UNEXPECTED INCONSISTENCY; RUN fsck manually.

[FAILED]
***An error occured during the file system check.
*** Dropping you to a shell; the system will reboot
***When you leave the shell.
Give root password for maintenance
(or type Control-D for normal startup):

I tried Ctrl-D but that didn't help, so I tried my root and then fsck. That didn't seem to work, but after restarting a few more times it was up back and running. So, my question is what did I do wrong and is there anyway to prevent this from happening again??  I have no explanation for it - it was working fine when I left, then an hour later I had this problem.  I'd appreciate any input.

---

### Post by kaamos on 2006-01-30
Your friend -> [http://ubuntuforums.org/showthread.php?t=118260](http://ubuntuforums.org/showthread.php?t=118260)

---

### Post by emerick7 on 2006-01-30
Thanks... that's just what I was looking for - I was searching for "file system errors" instead of "filesystem errors."

---

