---
title: "How to log a user out from ssh"
date: 2006-04-01
forum: General Help
---

### Post by encompass on 2006-04-01
I have users that I need to log out while I am remotely connected.  How do I log them out using ssh and avoiding the reboot.
Scenario:
I have logged in but forgot to log out and I need to vnc in to check some things... But I can't because I am logged in.  I can however ssh in and try to log them out from there.

Solutions anyone?

:-D

---

### Post by hw-tph on 2006-04-01
I answered [a very similar question](http://ubuntuforums.org/showthread.php?p=878411#post878411) yesterday.


Håkan

---

### Post by JaDE_nix_usr on 2008-06-07
I usually do not post to this forum but since it comes the first up on google I thought I would respond with a better answer I found.

skill -KILL -t pts/0

where pts/0 is the terminal gotten from a w

w

---

