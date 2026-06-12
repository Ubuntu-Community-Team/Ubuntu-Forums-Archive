---
title: "Changing font size"
date: 2006-04-01
forum: General Help
---

### Post by Blazeix on 2006-04-01
Hi, I recently installed the nvidia driver for linux and it works very well, the only problem is that it made the font size very large for every font. I used kcontrol to set the system fonts down to a better size, but non system fonts (Anything on the web or in a form) is still huge. I can go to every single application and set the font size manually, but there must be an easier way. Can anyone help?

---

### Post by Sutekh on 2006-04-01
When you installed the NVIDIA driver, did your screen resolution change?

---

### Post by Blazeix on 2006-04-01
No, I had it set at 1920x1200, and it stayed at 1920x1200

---

### Post by duffydack on 2006-04-02
it must of changed the dpi
find ServerArgsLocal  in kdmrc (cant remember where it is exactly) and make sure its got -dpi 75(or whatever u want) after the = 
MUST be directly after the =

---

### Post by Blazeix on 2006-04-02
Thanks! Your reply helped. I couldn't find kdmrc, but a google search gave me this site with an in depth tutorial:
[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

---

