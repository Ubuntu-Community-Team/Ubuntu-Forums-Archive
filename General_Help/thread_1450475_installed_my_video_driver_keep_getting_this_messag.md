---
title: "installed my video driver keep getting this message"
date: 2010-04-09
forum: General Help
---

### Post by imtacovato on 2010-04-09
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

i have no idea how to do this any help would be appreciated

---

### Post by imtacovato on 2010-04-09
bump

---

### Post by lisati on 2010-04-09
Please be patient - we're all volunteers here, the person who has the best nugget of information to help you figure this out might not have seen your thread yet. The usual rule of thumb for bumping threads here is to not do it more than once in 24 hours.

If you are able to, go to Applications->Terminal, and type in: ```
sudo nvidia-xconfig
```
You will be asked for your password. It won't show as you type but will still be accepted.

Let us know how you get on.

---

### Post by imtacovato on 2010-04-09
okay thank you, sorry about that i should have read the forum rules before i bumped it

---

### Post by imtacovato on 2010-04-09
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

this is what i got no idea if it worked

---

