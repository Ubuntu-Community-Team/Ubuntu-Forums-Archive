---
title: "Flash 10 in Hardy"
date: 2009-07-02
forum: General Help
---

### Post by weissnich on 2009-07-02
Hi,

I wanted to replace the old flash 9.0 r159 and so I removed it and downloaded and installed flash 10 .deb from the Adobe website.
However now in about:plugins I still see "libflashplayer.so Shockwave Flash 9.0 r159", why?
How do I completely remove flash 9, I removed the nonfree-flashplugin but obviously this is not enough.

---

### Post by snek on 2009-07-02
I just had sort of the same problem, however I installed from the repos..
First i had to do a sudo aptitude purge flashplugin-nonfree flashplugin-installer
and then a sudo aptitude install flashplugin-nonfree flashplugin-installer

Somehow the installer is not auto removed if you just purge flashplugin-nonfree.
Hope this helps!

> 
**Shockwave Flash**

 File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r22


---

