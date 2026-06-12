---
title: "Firefox 3.5 / Shiretoko doesn't open Startup page when opened"
date: 2009-07-01
forum: General Help
---

### Post by zonky on 2009-07-01
I'm using Firefox 3.5 / Shiretoko, installed from the Ubuntu Mozilla Security Team PPA, with one problem: When i Launch the app by running firefox-3.5, the startup page doesn't load, as set in Edit-> Preferences, i just get a blank tab.

Is anyone else having this problem?

(I imported my existing profile from Firefox 3.0.11 where this startup page works fine).

---

### Post by lovinglinux on 2009-07-01
Delete the file *places.sqlite* from the Shiretoko profile folder, somewhere under ~/.mozilla/firefox-3.5/******/

This should fix your problem. Additional info in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by zonky on 2009-07-01
Hi, thanks for the suggestion. I've deleted places.sqlite from inside the mozilla profile folder for firefox-3.5, however this does not seem to have fixed this problem.

---

### Post by lovinglinux on 2009-07-01
> **zonky said:**
> Hi, thanks for the suggestion. I've deleted places.sqlite from inside the mozilla profile folder for firefox-3.5, however this does not seem to have fixed this problem.

Close Firefox and delete ~/.mozilla/firefox-3.5

It will import your profile from ~/.mozilla/firefox again. This could solve the problem.

---

### Post by zonky on 2009-07-01
> **lovinglinux said:**
> 
It will import your profile from ~/.mozilla/firefox again. This could solve the problem.

Thanks. A bit more work on my part identified the problem as caused by an incompatible add-on, specifically Ubuntu Firefox Modifications.

---

