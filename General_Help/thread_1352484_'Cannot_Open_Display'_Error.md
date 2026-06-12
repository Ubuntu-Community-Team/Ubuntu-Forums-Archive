---
title: "'Cannot Open Display' Error"
date: 2009-12-11
forum: General Help
---

### Post by AJH101 on 2009-12-11
Hi - I am attempting to edit my xorg.conf.new that I had to generate to try to fix some screen resolution issues. Whenever I try however I get a 'Gtk-WARNING **: cannot open display:' error. 
 
Any ideas how I can get around this? I am running 9.10. Thanks!

---

### Post by AJH101 on 2009-12-12
OK I have access to my /root/xorg.conf.new file.
 
Section "Monitor" refers to "Monitor0".
Sectiion "Screen" refers to "Screen0", "Card0" and "Monitor0" but each subsection refers to "Viewport 0 0" and then depths 1, 4, 8, 15, 16 and 24.
 
I am really out of my depth here. Can anyone help? I have one very dead computer otherwise!!
 
Thank you

---

