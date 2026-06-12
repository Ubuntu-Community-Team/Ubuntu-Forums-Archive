---
title: "lib arts-devel in Ubuntu 9.10 (half-solved)"
date: 2010-03-04
forum: General Help
---

### Post by eucloid on 2010-03-04
Hi,

We have a project at work that requires a couple of library headers. One of them that I could not find in Ubuntu is arts-devel.

I read somewhere that it was not available anymore in Ubuntu (or KDE 4). Is this correct? 

Also the way I (temporary?) resolves this is to copy artsc.h and artsc_export.h (from another machine's /usr/include/kde/artsc/) to Ubuntu /usr/include/KDE/artsc directory then create a link: 
sudo ln -s /usr/include/KDE /usr/include/kde

I say it's half-solved because it allows to compile the software (for other linux installation that have this library), but not to run it on my development machine.

Thanks!
Francois

---

