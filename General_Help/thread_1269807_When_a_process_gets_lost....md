---
title: "When a process gets lost..."
date: 2009-09-18
forum: General Help
---

### Post by hnrkg on 2009-09-18
This is my problem: When my ubuntu-session froze I "killed" it (altgr+prt src+k) and after that at least one process seems to be "lost",  i.e. "xsp2", a webserver started through Monodevelop. So, when I logged on again and started up Monodevelop and tried to run the webserver it gave me an error that said that the particular port (in this case 8080) was "already in use".

The problem is, I think, that the old "xsp2"-process is still running -- "somewhere". I can't find it and therefore I can't not kill it. 

So, my question is really: How do I kill this (lost) process? I can't find it as root with neither "ps -A" nor "top". Where is it? And why?

---

