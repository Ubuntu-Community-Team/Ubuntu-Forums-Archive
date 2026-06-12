---
title: "Where are start up programs and services?"
date: 2009-12-11
forum: General Help
---

### Post by CONCORAN on 2009-12-11
I remember once seeing an app which displayed and allowed control over what programs/servers (httpd, mysql etc) ran at startup. On net I see that it's supposed to be in System \ Preferences\ Sessions. But I can't seem to find that app anymore or remember its name. Can someone pls help me find it?

Also, is there a place like .profile or other place where the list is maintained?

TIA

---

### Post by howefield on 2009-12-11
System > Preferences > Startup Applications

---

### Post by CONCORAN on 2009-12-12
Thanks. The link appears on one computer, not on the other. How to get it back?

Also, where are apps like apache server etc listed? I don't see those in start up applications. If I do rcconf I can see quite a few servers.

---

### Post by 3rdalbum on 2009-12-12
> **CONCORAN said:**
> Thanks. The link appears on one computer, not on the other. How to get it back?

Also, where are apps like apache server etc listed? I don't see those in start up applications. If I do rcconf I can see quite a few servers.

The program you are thinking of was either Services or Boot Up Manager. Neither of which will do anything meaningful on Ubuntu 9.10 as the startup system is completely different. (it's now Upstart)

Apache is a startup daemon - it runs on bootup as its own user account, not on Gnome login as your user account, so it's not in Startup Applications.

I actually don't know how to manage Upstart; anyone want to take a guess?

---

