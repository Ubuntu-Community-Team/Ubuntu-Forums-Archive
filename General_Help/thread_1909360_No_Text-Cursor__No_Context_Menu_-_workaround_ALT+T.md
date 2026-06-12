---
title: "No Text-Cursor / No Context Menu - workaround: ALT+TAB"
date: 2012-01-15
forum: General Help
---

### Post by blueSpirit on 2012-01-15
Hello,

I have a crazy bug, which shows up in two topics:

[LIST]
[*]From time to time the context menu of Firefox (right mouse click) disappears when I move the mouse - thus I cannot select anything. The regular menu of the Firefox is still working. After I switch the workspace, switch a window (ALT+TAB) or minimize/un-minimize the Firefox it's working fine again.
[/LIST]
  
[LIST]
[*]From time to time the text cursor disappears. This means, I can still select text (CTRL+C has no effect) but I cannot set the text cursor (the blinking line) - thus I cannot enter text. I noticed this bug in the QtCreator.
Workaround is the same as for the Firefox, so pressing ALT+TAB twice, the cursor shows up again and I can continue working.

See also this video: [http://www.youtube.com/watch?v=_BnrHB0tJU4](http://www.youtube.com/watch?v=_BnrHB0tJU4)
[/LIST]
Any ideas where this comes from and how to fix it?


Thanks, Charly

PS: Ubuntu 11.10 - x86_64

---

### Post by dino99 on 2012-01-15
Might be due to a graphic driver issue: check it via sudo jockey-gtk

Your logs can help you to know about warnings/errors:
~/home/.xsession-errors
/var/log/

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient & wait for self ending)

---

### Post by blueSpirit on 2012-01-15
> **dino99 said:**
> sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient & wait for self ending)
I ran these commands and rebooted the computer, but at least the "text-cursor problem" still exists. It appears when changing from QtCreator to another workspace. Switching to another workspace and back again does only sometimes fix the problem.
> **dino99 said:**
> Your logs can help you to know about warnings/errors:
~/home/.xsession-errors
/var/log/
I watched the following log files while reproducing the text-cursor problem - without any result:
```
tail -f ~/.xsession_errors
tail -f  /var/log/dmesg
tail -f /var/log/xorg.0.log
```Further more, I checked the whole folder by time - without any useable result:```
sudo grep -r "Jan 15 11:35:" /var/log/*
```> **dino99 said:**
> Might be due to a graphic driver issue: check it via sudo jockey-gtk
The NVIDIA version does not fix this problem. I tried version 96, version 173, 'version-current' and 'post-release updates/version current-updates'. In none of them the bug is fixed.

---

### Post by blueSpirit on 2012-01-15
I switched from a 19" to a 27" monitor some time ago - maybe this could be the source for the problem. But maybe it also appears before... what I'm sure is that it started at least with 11.10...

---

### Post by blueSpirit on 2012-01-15
I ve posted a video which shows this problem: [http://www.youtube.com/watch?v=_BnrHB0tJU4](http://www.youtube.com/watch?v=_BnrHB0tJU4)

---

### Post by blueSpirit on 2012-01-18
No one else with an idea...?

---

### Post by sigi64 on 2012-01-25
I have the same problem with QtCreator (2.3.1, 2.3.2, 2.4.0) on Ubuntu 11.04 and 11.10

---

