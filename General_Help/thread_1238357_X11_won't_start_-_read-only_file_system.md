---
title: "X11 won't start - read-only file system"
date: 2009-08-12
forum: General Help
---

### Post by gentracer on 2009-08-12
This morning when I came into my office, my computer, Dell Inspiron E1505, appeared to have had a disk problem overnight and I was told to issue the fsck command.  Several errors were apparently fixed during the process.

However, now when I try to restart, I get the following error message:

COULD NOT START THE X SERVER DUE TO SOME INTERNAL ERROR

and it puts me in a regular CLI.  I have looked at several options online for suggestions on fixing the problem, all of which involve editing or removing a file and reconfiguring X.  Unfortunately, the file system is mounted read-only, so I can't make any changes - all file systems appear to be mounted rw based on the output of the mount -l command.

HELP!!

I used to do a lot with Unix, but it has been years and I've forgotten a LOT!  So...feel like a newbie.

I've tried several things from the recovery menu - dpkg, fsck, and restart in normal mode - to no avail.

Thanks for any ideas!!

---

### Post by michy99 on 2009-08-12
Are you sure it's not a permission problem? System file usually have to be edited with root permissions, which you get by using the sudo or gksudo command.

---

### Post by gentracer on 2009-08-12
Yes, not a permission problem.  I have tried it with both a sudo command and by an su directly to the root account - both tell me the file system is mounted read-only.

Since my post, I have done a complete shutdown (again) and booted in recovery mode. I have gone through the various 'fix' options (again) and it now seems to be working.  I'm in the process of checking everything out - so far, so good.

It seems like several people are experiencing a similar problem recently, so I'm wondering if a recent update caused a problem somewhere??

I was having X11 problems that caused the system to crash 2-3 weeks ago and found a solution by editing the x11.conf file, but...

Seems like something in the latest version of ubuntu and X11 are not happy with each other??

Thanks for the post!

---

