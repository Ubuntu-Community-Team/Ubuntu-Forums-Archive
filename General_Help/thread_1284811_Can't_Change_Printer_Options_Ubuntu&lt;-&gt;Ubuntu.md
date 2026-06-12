---
title: "Can't Change Printer Options Ubuntu&lt;-&gt;Ubuntu Shared Printer"
date: 2009-10-07
forum: General Help
---

### Post by PacShady on 2009-10-07
Hey all

I have a Samsung CLP-300 set up on my desktop computer (runing Jaunty), prints fine, no problems, however when I set up my laptop (also running Jaunty) to print over the network to this printer, it refuses to let me change any printer options within system-config-printer.

Printing itself is fine, and if I log into the CUPS webpage, I can change the settings there no worries. I just can't change them from within system-config-printer, for the life of me I can't work out why. Hours of Googling and forum searching suggests, once again, I'm the only damn person on the planet with this problem. Anyone got any ideas, any ideas at all, as to why this is happening?

---

### Post by PacShady on 2009-10-07
Here's a screenshot of what I mean by not being able to change the options, and an error log from CUPS from opening system-config-printer, and trying to access the settings.

EDIT: Added strace log

---

### Post by plucky on 2009-10-07
This is a longshot,but have you allowed "remote administration" on the computer the printer is attached to?

Good Luck

---

### Post by PacShady on 2009-10-07
I have, and I even tried turning it off and back on again. No luck.

I did manage to get a workaround going, since I also have the printer set up to print when my desktop is running Windows (my girlfriend likes to play WoW on a particularly cheap and nasty private server that destablises her client when running under Wine), and I could change the settings under that, I copied that install and simply changed the output to the ipp address for Ubuntu. Worked like a charm, however when setting up the printer from scratch it still won't let me change anything. I think I'll have to launch a bug report on system-config-printer.

---

