---
title: "Distorted boot splash"
date: 2010-09-03
forum: General Help
---

### Post by megabyte1234 on 2010-09-03
):P
Im using ubuntu lucid lynx and when i boot it it gives me (where the splash should be) some strange colored pixels on top of my screen (kind of orange dots repeated in the top 2 cm of screen), then login screen pops up. Anybody got this problem? or hints to solve?

---

### Post by t0m on 2010-09-03
I got the same problem on my server. 
Thought maybe it's because my old graphics card wasn't supported anymore.. it's a Matrox Mystique. Upgraded from 8.04LTS.

---

### Post by megabyte1234 on 2010-09-03
Sorry, will give some more details...

I have a custom-built computer with an ATI Radeon HD 3450 graphics card and an old CRT monitor (Hansol 730E) as screen. I have an print of sysinfo attached to this post.

---

### Post by gandaran on 2010-09-03
> **megabyte1234 said:**
> ):P
Im using ubuntu lucid lynx and when i boot it it gives me (where the splash should be) some strange colored pixels on top of my screen (kind of orange dots repeated in the top 2 cm of screen), then login screen pops up. Anybody got this problem? or hints to solve?
try changing the boot resolution, install and use startup-manager.

---

### Post by megabyte1234 on 2010-09-03
I think i have found it...

I set an splash image for grub, and splash resolution to 1280x1024 and now it works! still not really solved, i get the message "out of range"...

---

