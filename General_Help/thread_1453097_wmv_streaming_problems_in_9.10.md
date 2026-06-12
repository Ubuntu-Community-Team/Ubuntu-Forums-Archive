---
title: "wmv streaming problems in 9.10"
date: 2010-04-12
forum: General Help
---

### Post by seemore on 2010-04-12
Hi guys, I'm sure this is a simple problem, however I am a newly reformed microsoft user (and it feels great).

When I try to watch wmv streams I get the error:

"
**[SIZE=3]No URI handler implemented for "mmsh".[/SIZE]**

thank-you for your time and help.

---

### Post by darolu on 2010-04-12
Try installing these packages from your terminal:

```
$ sudo apt-get install ubuntu-restricted-extras gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
```

You can also install them via Synaptic of course.

---

### Post by seemore on 2010-04-12
I get this message in synaptic:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Then when I type what it asked into the terminal I get:

"seymour@Toshiba:~$ sudo dpkg --configure -a
[sudo] password for seymour: 
Setting up openoffice.org-emailmerge (1:3.1.1-5ubuntu1.1) ...
Segmentation fault
Copying: mailmerge.py
Enabling: mailmerge.py
Segmentation fault"

and then it does nothing for minutes. The above problem began when my system crashed mid-updating.

Thank-you for your help.

---

