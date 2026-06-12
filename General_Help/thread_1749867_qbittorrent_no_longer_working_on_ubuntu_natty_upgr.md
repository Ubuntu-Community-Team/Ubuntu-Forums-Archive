---
title: "qbittorrent no longer working on ubuntu natty upgrade"
date: 2011-05-04
forum: General Help
---

### Post by jewfromdahood on 2011-05-04
upgraded to natty, Unity is interesting but I would still rather have the old GUI. but my main issue is that qbittorent no longer works splash screen starts but program never loads. it shows it as running but I can't pull it up... I launch it from terminal and I get this:

alon@kosher-dragon-laptop:~$ qbittorrent 
/usr/share/themes/Divinorum-Blue-Green/gtk-2.0/gtkrc:1391: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Divinorum-Blue-Green/gtk-2.0/gtkrc:1391: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
alon@kosher-dragon-laptop:~$

---

### Post by jewfromdahood on 2011-05-05
now I get this 

alon@kosher-dragon-laptop:~$ qbittorrent 
/usr/share/themes/Divinorum-Blue-Green/gtk-2.0/gtkrc:1391: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Divinorum-Blue-Green/gtk-2.0/gtkrc:1391: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
qbittorrent: symbol lookup error: qbittorrent: undefined symbol: _ZN10libtorrent7sessionC1ERKNS_11fingerprintEii

---

### Post by jewfromdahood on 2011-05-05
bump...

---

### Post by jewfromdahood on 2011-05-06
bump

---

### Post by PratterFak on 2011-05-06
I would just uninstall it, then reinstall it from the software center. I currently use qbittorrent on my 11.04 and it works great, but I installed it once I was on 11.04- after I found that the Transmission I was using on 10.10 no longer worked.

---

### Post by jewfromdahood on 2011-05-07
tried that already before I even posted... And still to no avail got it to work for a few minutes upgrading to the beta... then it still would not work so I uninstalled it and downgraded to 2.7.3 again. Still to no avail

---

### Post by jewfromdahood on 2011-05-07
fixed it... I completely uninstalled then reinstalled qbittorent, still wouldn't work so on a hunch I found libtorrentrasterbar and saw it was using v0.16 so i downgraded to 0.15.6 and all is good again

---

### Post by mattymonkey on 2011-05-09
I had this problem too. I upgraded and I believe that is what led to the problem. The issue stems from qBittorrent starting minimized. I opened terminal and edited the file in ~/.config/qBittorrent and changed StartMinimized from true to false. Worked fine after that. I reinstalled as well and that didn't help because, I assume, when I reinstalled the config file stayed.

Hope this helps!

Peace

---

