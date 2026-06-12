---
title: "help - please changed the wrong file"
date: 2006-06-16
forum: General Help
---

### Post by waldorf on 2006-06-16
I started this thread [http://www.ubuntuforums.org/showthread.php?t=197997&highlight=kdm+gdm](http://www.ubuntuforums.org/showthread.php?t=197997&highlight=kdm+gdm)

and made a mistake when I edited etc/X11/default-display-manager

I was supposed to change the line /usr/sbin/gdm to /usr/bin/kdm

BUT

changed it to /usr/sbin/kdm (i.e. I left it as sbin instead of changing to bin)

Now I can't boot up.

How do I use a live cd to go in and fix etc/X11/default-display-manager

It won't let me mount the partition that ubuntu lives on.

Please help!

---

### Post by ayoli on 2006-06-16
you have just screwed up your display manager launching, but your machine must boot (even if kdm cant launch) then hit ctrl+ alt + F1 log in with your user / pass and:  sudo nano /etc/X11/default-display-manager 
might do the job.

---

### Post by waldorf on 2006-06-16
okay I'll give it a try.

quick question. how do I save a change to a file with nano?

Thank you thank you

---

### Post by waldorf on 2006-06-16
Yeah Ayoli!!!!!

Many many thanks!!!!!

It worked!

---

### Post by bruce89 on 2006-06-16
[QUOTE=waldorf]quick question. how do I save a change to a file with nano?[/QUOTE]Contol+X quits nano.

---

