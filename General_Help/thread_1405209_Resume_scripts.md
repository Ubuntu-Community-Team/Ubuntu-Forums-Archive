---
title: "Resume scripts"
date: 2010-02-12
forum: General Help
---

### Post by chaanakya_chiraag on 2010-02-12
I'm using Ubuntu Karmic Koala (9.10) with Fluxbox, so as you can tell, it's a minimalistic setup (without even network-manager!).  I was trying to figure out how to edit the resume scripts, and I was wondering where exactly to put custom resume scripts and how to ensure they are executed.  I tried the following:
Edit a new file (99fixbrightness) (with root permissions) with the following contents:
```
#!/bin/bash
/home/chiraag/scripts/brightness.sh
```and the contents of ~/scripts/brightness.sh
```
#!/bin/bash
yes "password" | sudo -S toshset -inten 7
synclient HorizEdgeScroll=1
gnome-screensaver-command -l
```Thanks in advance!
- Chiraag

---

### Post by chaanakya_chiraag on 2010-02-12
Anyone?

---

