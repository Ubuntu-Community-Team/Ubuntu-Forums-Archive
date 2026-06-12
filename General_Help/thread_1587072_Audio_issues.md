---
title: "Audio issues"
date: 2010-10-02
forum: General Help
---

### Post by Granddadof10 on 2010-10-02
Now, off to try to find out why my sound is not working
under ANY program?   Am running Realtek ACL662 and
no issues show up during setup or check for driver  :confused:

Have a great day,   John

---

### Post by lidex on 2010-10-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

