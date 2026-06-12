---
title: "graphics type problem in 10.10"
date: 2011-03-05
forum: General Help
---

### Post by harecanada on 2011-03-05
When I open Open Office or some website and even Ubuntu forums, some words show up in a dotted pink box. I've attached a sample here. I know it has to be a setting  that is screwed up but I don't know which setting. Also, I don't know why it affects only some pages and why offline (Open Office) and online too.
Any ideas?
harecanada

---

### Post by rosencrantz on 2011-03-05
Could you be missing Microsoft's core TrueType fonts?
Enable Ubuntu Universe ([https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)) and try
sudo apt-get install msttcorefonts

---

### Post by harecanada on 2011-03-06
Thanks rosencrantz. This is what I get when I put in sudo apt-get install msttcorefonts:


harecanada@harecanada-Inspiron-531:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harecanada@harecanada-Inspiron-531:~$ 

Any other ideas?
I'm stumped
harecanada

---

### Post by rosencrantz on 2011-03-10
Search me ... can  you pin it down to specific fonts (i.e. check that weather site's CSS sheet and look it up in affected OpenOffice documents)?
Have you tried a different browser like Chrome?
It could also be that your problem is GTK related, but off the top of my head I couldn't name a single Gnome app that's based on anything else. I suppose you don't have any KDE components like Konqueror/rekonq to rule out GTK involvement?

---

### Post by harecanada on 2011-03-20
Sorry I have not gotten back to you rosencrantz. That was not polite of me. I tried using Chromium and the problem disappears. So I guess the problem is Firefox which really is a drag because I have been using it for so long and you know how you get use to using one thing and I don't really want to change. However, it still doesn't answer why it happens with Open Office. I'll keep working on solving it and let you know how I do. Thanks again for your input. Much appreciated.
harecanada

---

