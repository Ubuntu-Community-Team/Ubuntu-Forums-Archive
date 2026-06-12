---
title: "Help me make some startup files/scripts/something"
date: 2010-05-09
forum: General Help
---

### Post by jordan Alexander Hartley on 2010-05-09
Hi everyone,
First off, Im new to linux, well not new new, but new to playing around with it.

Ive currently got a HTPC setup, and I want to run something once my system starts.

Now when i startup, which boots into xbmc, I need to start a continous ping in the background.

So to acheive this I go to tty1 by pressing CTRL+ALT+F1, from here i enter my user details to login and then simple type my command and then switch back to xbmc to carry on.

So, is there away I can automate this, so the console automatically starts the ping without me.

Ive come accross the ttyX.conf files in the /ect/.conf/ directory (I think thats there file names, Im not there to double check atm), are these files there to allow autorun commands?

I know it may be a strange request, the reason for the ping is just so a NAS box i have doesnt fall alseep, I know i shouldnt have to do this, but its easier and cheaper than buying a better NAS box.

just as a note, it needs to run at System startup, as the season which auto logsin is not Gnome, its the xbmc session type.

Hope someone can help, I really do need to start getting better at the linux stuff, Im a Windows technician and kinda neglect linux, even though i always enjoy it when i play with it.

O Im using the current 10.04 Lucid build of Ubuntu.

---

### Post by dino99 on 2010-05-09
into "synaptic" search for "ping", you will have listed a lot of packages, maybe one can be added to a cron job for your needs

---

