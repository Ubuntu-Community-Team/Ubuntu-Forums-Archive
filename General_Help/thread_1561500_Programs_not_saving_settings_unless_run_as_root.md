---
title: "Programs not saving settings unless run as root"
date: 2010-08-26
forum: General Help
---

### Post by gibber1sh on 2010-08-26
I'm using Ubuntu 10.04 64-bit and I'm having the following issue: a lot of the programs I use seem not to be able to save their settings on shutdown (Visual Paradigm for UML, for example. Kile is another one). This happens only for some of my programs. What is causing this? Have I installed them in an inappropriate location? (e.g. VP is in /opt). I also have this problem sometimes with system settings (screensaver reverted to old value upon reboot once, but after that it worked...). 
Any idea what's going on?

Edit: Just noticed running as root doesn't work either, I rebooted and it's back to square one

---

### Post by mikewhatever on 2010-08-26
Generally speaking, programs will not allow you to save configuration changes if their config files are owned by root. The ownership often becomes root, when you run the program as root or as admin. Try checking the ownership of the cofig files that give you trouble and chown if needed.

---

