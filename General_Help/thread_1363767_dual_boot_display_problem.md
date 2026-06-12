---
title: "dual boot display problem"
date: 2009-12-24
forum: General Help
---

### Post by ramgopal on 2009-12-24
Hi all,

After installing ubuntu in aDesktop with windows 7 (dual boot) something strange happened. After the instalation and everytime it starts a small square box  appears and display not coming and blank desktop

please help me slove that problem

---

### Post by Sef on 2009-12-24
What are your system specs?

---

### Post by efflandt on 2009-12-24
What brand/model video and how is it connected (laptop display, vga, dvi, hdmi)?

Post the output of **sudo lspci -v** related to your video, which you should be able to get if you can boot in a (recovery) menu entry.  Also have you installed anything additional for your specific video, or are you using default modules?

Sometimes switching video cable type can mess up usplash during boot, but if that is the case you should still be able to boot a recovery kernel and run **startx** after you login.  To fix a splash issue either edit /etc/usplash.conf to your native monitor resolution, or remove "splash" option in /etc/default/grub, and then **sudo update-grub**.

---

