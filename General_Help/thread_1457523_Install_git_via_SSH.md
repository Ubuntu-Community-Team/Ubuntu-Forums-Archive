---
title: "Install git via SSH"
date: 2010-04-18
forum: General Help
---

### Post by rickatnight11 on 2010-04-18
I'm running XBMCLive, which is running on top of Ubuntu.  When attempting to install git through the command line, apt-get doesn't seem to have the correct source added/enabled:

```
xbmc@XBMCLive:~$ sudo apt-get install git-core
[sudo] password for xbmc:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package git-core
```

What source do I need to add, and how can I do this from the command line?  Thanks!

---

### Post by Bachstelze on 2010-04-18
Please paste your sources.list. The packae is in main, so if Apt can't find it, you have a problem.

---

### Post by rickatnight11 on 2010-04-18
That's what I thought too.  It's been a while since I've been in Linux land; where is my sources list?

---

