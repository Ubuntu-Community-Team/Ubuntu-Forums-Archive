---
title: "Desktop crashes and other seemingly related problems"
date: 2010-07-28
forum: General Help
---

### Post by SchizmWolf on 2010-07-28
Hey all, I'm having some trouble with my desktop and a few other issues that seem related. I'm running Kubuntu Jaunty 9.04 and have been since December without issues until now.  I've been noticing the last couple of days that my desktop, KDE4, is starting to crash randomly, and I get various messages saying that a variety of different things "aren't writable" despite the fact that I'm not actively trying to write anything. 
When I last brought up my terminal and typed in "sudo apt-get -f install" it returned an unusual result that I haven't encountered before:
```
schizm@schizm-laptop:~$ sudo apt-get -f install
[sudo] password for schizm:
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```I don't know where to start to fix the problem, and it's starting to worry me a bit. Any fixes, advice, tips, etc would be greatly appreciated. Thanks, hope to get some responses before my computer decides not to work or something :(

---

### Post by hornetster on 2010-07-28
Stab in the dark.....
Disk problems? do a full check....

---

### Post by SchizmWolf on 2010-07-29
> **hornetster said:**
> Stab in the dark.....
Disk problems? do a full check....

Never had to do it before, so I'm a little rusty... any specific commands I should know about?

---

### Post by SchizmWolf on 2010-07-30
Alright, problem solved. Turns out there were some broken paths on the hard drive that I fixed with a simple fsck. Works just fine again. Thanks for the idea though! :D

---

