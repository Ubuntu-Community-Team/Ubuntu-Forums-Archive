---
title: "Upgrade XSANE ?"
date: 2006-06-15
forum: General Help
---

### Post by drfox on 2006-06-15
There is a new version XSANE .991 which allows scanning to pdf. 
I downloaded it to my desktop, but it wouldn't install because of dependency problems. How can I get this upgrade to install?

Thanks

Larry

---

### Post by nanotube on 2006-06-15
[QUOTE=drfox]There is a new version XSANE .991 which allows scanning to pdf. 
I downloaded it to my desktop, but it wouldn't install because of dependency problems. How can I get this upgrade to install?

Thanks

Larry[/QUOTE]
download and install the dependencies, maybe? :)

---

### Post by balloons on 2006-06-16
Enable debian etch repos, and force version install of the new xsane (non-multiverse, non-ubunutu). That will take care of everything.. I just did this, for the multipage support as well

---

### Post by drfox on 2006-06-16
Thanks to both of you. Before I got Guitarra's message, I downloaded and installed xsane-common, tried xsane again, found it necessary to download and install 1 library file, and then installed xsane. I had to restart Gnome before my scanner was detected, but this new version works great.  :D 

Larry

---

### Post by redPirate on 2006-06-29
How do I enable the debian etch repos?

---

### Post by balloons on 2006-07-13
Download and install these two packages, if you don't want to mess with debian repos.

[http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane_0.97-3_i386.deb](http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane_0.97-3_i386.deb)
[http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane-common_0.97-3_all.deb](http://ftp.us.debian.org/debian/pool/main/x/xsane/xsane-common_0.97-3_all.deb)

---

