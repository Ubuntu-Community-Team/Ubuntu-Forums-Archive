---
title: "Display problem - vertical lines"
date: 2009-12-18
forum: General Help
---

### Post by pikmen on 2009-12-18
Hi guys!

Yesterday I installed Ubuntu for the first time, and though I'm finding it very interesting, I've also run across an annoying problem.

I get narrow vertical lines, separated by around 1cm, from which smaller horizontal lines flicker from the bottom of the monitor upwards. They're worst at 1280x1024, and become barely noticeable at 1024x768, both at 60Hz. They also increase when I move things like windows around the monitor.

Here's a picture I took of the monitor (I left it unusually large so the lines are better seen):
[http://img20.imageshack.us/img20/5434/dsc04193r.jpg](http://img20.imageshack.us/img20/5434/dsc04193r.jpg)

I'm posting this here in the General Help forum hoping you guys will be able to tell me what the problem is, so I can look up more specific help. Obviously, I won't say no to a solution though :).

---

### Post by dcstar on 2009-12-18
> **pikmen said:**
> 
........
I get narrow vertical lines, separated by around 1cm, from which smaller horizontal lines flicker from the bottom of the monitor upwards. They're worst at 1280x1024, and become barely noticeable at 1024x768, both at 60Hz. They also increase when I move things like windows around the monitor.
........

It is probably a video driver issue, do a search for your particular video hardware.

---

### Post by pikmen on 2009-12-19
Thanks :), I'll look into it better.

---

### Post by pikmen on 2009-12-21
Apparently this computer has a SiS integrated graphics card... or something.

I eventually stumbled on this thread:

[http://ubuntuforums.org/showthread.php?t=345492](http://ubuntuforums.org/showthread.php?t=345492)

I followed the instructions on the page they referred us to ([http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml)), and after installing the suggested driver the problem was fixed.

---

### Post by barinov2000 on 2011-01-07
great latest drivers (source and binaries) here (including Lucid 10.04 and Maverick 10.10):
[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

Thank you Antonio J. de Oliveira, awesome job!

---

