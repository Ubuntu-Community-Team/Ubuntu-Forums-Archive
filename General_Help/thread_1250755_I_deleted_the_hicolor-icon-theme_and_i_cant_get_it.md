---
title: "I deleted the hicolor-icon-theme and i cant get it back"
date: 2009-08-26
forum: General Help
---

### Post by natholas on 2009-08-26
I was trying to clear up some space on my hard drive so i deleted /usr/share/icons/hicolor now i realize that was stupid but i was wondering how i can get the icons that are normally in there.. 

i cant run the ubuntu cd and copy the files cos im using a netbook and i tried sudo gtk-update-icon-cache -f /usr/share/icons/hicolor but it gave this error: gtk-update-icon-cache: No theme index file.natholas@Leopluradon:~$    now this is where my knolege of ubuntu stops and ive been looking around on the forums and on google but i havent managed to find anything that has worked.. any help would be much appriciated :)
thanks

---

### Post by yabbadabbadont on 2009-08-26
```
sudo apt-get --reinstall install hicolor-icon-theme
```
That should reinstall it for you.

---

### Post by natholas on 2009-08-27
ye that kinda worked.. except it only installed the folders but with no icons :(

i am going to try to copy the folder from a friends laptop with the same version of ubuntu.. that should work.. i hope..

---

### Post by natholas on 2009-08-27
yey :) that fixed it :) 
if anyone else wants those files just pm me

---

