---
title: "Grub 2 shouldn't do this"
date: 2011-12-25
forum: General Help
---

### Post by ant2ne on 2011-12-25
It seems that the issue I've outlined [here]("http://blog.computerant.com/2010/03/22/grub-2-bug/") Has gotten worse and the resolution that I've found no longer works with 11.10.

This has got to be one of the most horrible ideas for a server OS particularly a virtualized one. What is the current solution for this problem?

---

### Post by lolpenguin on 2011-12-25
What? GRUB2 skips the list of boot options unless shift is held. Try using StartUp-Manager [apt-get install startupmanager] to lower the countdown time.

---

### Post by ant2ne on 2011-12-26
There is no countdown time. It just hangs until something is selected.

---

### Post by dabl on 2011-12-26
Referring to your article, couple of questions:

1. Are you using a recent/current version of grub-pc?  For 11.10, we have

```
don@ubuntu:~$ sudo apt-cache policy grub-pc
[sudo] password for don: 
grub-pc:
  Installed: 1.99-12ubuntu5
  Candidate: 1.99-12ubuntu5
  Version table:
 *** 1.99-12ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
```

2. Is this still all about the corner case where "... for some reason the computer crashes or is improperly shutdown"?  When that happens, when you attempt to reboot normally a fsck is initiated, and it happens in the background, and you might not necessarily be aware of why you are staring at the boot screen for an extended period of time (I consider failure to give the user any feedback about ongoing processes a poor design, if not a bug ...).

I have not observed the problem, that I can remember, and I don't see lots of complaints about it.  But obviously it is an annoyance for you -- what is your typical system usage?

---

