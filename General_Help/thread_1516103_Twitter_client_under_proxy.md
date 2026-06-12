---
title: "Twitter client under proxy"
date: 2010-06-23
forum: General Help
---

### Post by Brown_ on 2010-06-23
Hi fellows, 
I've been searching for a nice and lightweight twitter client that runs under a proxy, but couldn't find any. What would you guys suggest to me?
ty

---

### Post by rusty0101 on 2013-02-02
"Nice and light weight" will always be questions of course, but Hotot seems to work as a twitter client behind a proxy. It's a 1.0.1 release, but their web site indicates it's still to be considered Alpha software.

It is a Python app, so there are a few required packages, but I already had all of those installed from what I can see.


Remember if this solves your problem to tag your question as solved.

the hotot package is in the repositories for 12.04, and presumably 12.10. I have not checked earlier releases.

To verify it is available, do:

[INDENT]$ apt-cache search hotot[/INDENT]

One of the results should be:

[INDENT]hotot - lightweight microblogging client[/INDENT]

Install with the command:

[INDENT]$ sudo apt-get install hotot[/INDENT]

From my perspective the app looks nice, supports both twitter and identi.ca and very possibly is extensible for other services should they be built. I gather the app developer would appreciate feedback.

~Rusty

---

### Post by howefield on 2013-02-02
Old thread closed.

---

