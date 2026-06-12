---
title: "Netbeans crashes when I use SVN, sometimes"
date: 2010-04-29
forum: General Help
---

### Post by thale on 2010-04-29
I've been using Netbeans for a while now but all of a sudden (as of 9.10 for me) it totally locks up when I execute svn commands. I've tried a few fixes I found, such as changing the bin dir, but nothing seems to have helped so far. Has anyone else come across this? The issue isn't consistent, sometimes it lets me execute commands and others it just freezes and I have to kill -9.

Any suggestions? I am using an i7 proc, not sure if that matters at all.

---

### Post by themullet on 2010-06-01
Ran into the same problem, solved it by adding:

-J-DsvnClientAdapterFactory=commandline

to netbeans_default_options in /etc/netbeans.conf 

Found the solution: [http://wiki.netbeans.org/FaqSvnCli](http://wiki.netbeans.org/FaqSvnCli)

Hopefully is of help

---

