---
title: "Web servers, mysql and php broke unexpectedly"
date: 2010-07-13
forum: General Help
---

### Post by crazyness003 on 2010-07-13
Hello everyone. 

Short story: web servers, mysql and whatnot are broken. Should I reinstall Ubuntu altogether, or try and salvage what I have?

Long story: I was recently experimenting with web servers and decided to install the LAMP stack. It worked great, i had a nice little web interface, my configurations seemed to be okay, i had all sorts of fun services running, etc.

But then i get the need to dump apache for 'Lighty', so i decided to uninstall apache via synaptic and install lighttpd. Of course there were a bunch of things that depended on apache...so I uninstalled all of them too. But then when i go to test my lighty server, it wasnt acting right. even though it was running, the only way to get to the lightly placeholder was to actually navigate to it, for some reason the index.html file wasnt automatically being read.

Long story short, i tried reinstalling everything to try and get it back to a working state, but now apache, lightly, mysql and php seem to not be working, at all.

Mysql even gives me errors
```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
``` 

Ultimately, i tried completely removing them all and their associated files from /etc and reinstalling, but that didnt work. all it did was make their folders with nothing inside. So, im wondering if I should just reinstall Ubuntu, or is there a way to salvage my epic failure?

ANY input is appreciated, even if you feel the need to yell at tme for "trying to fix something that aint broke".

PS: If it helps, Im running a Desktop version of Ubuntu 10.04 (since this is currently my only working computer).
And i have Webmin working like a charm (I think).

Ultimately, i want to pseudostream my data across the internet via a web interface. Thats why I felt the need for Lighty.

---

