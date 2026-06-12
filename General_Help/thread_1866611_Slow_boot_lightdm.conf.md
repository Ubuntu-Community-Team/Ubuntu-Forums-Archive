---
title: "Slow boot lightdm.conf"
date: 2011-10-21
forum: General Help
---

### Post by xcution on 2011-10-21
So i've upgraded to ubuntu 11.10 and i've modified my video resolution to expand by using the following article [http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940)
and then modified /etc/lightdm/lightdm.conf 
to add the following lines
xrandr --newmode "1904x1200_60.00" 191.00 1904 2032 2232...
xrandr --addmode DVI-1 1904x1200_60.00
xrandr --output DVI-1 --mode 1904x1200_60.00

which works fine when i type by command line but i wanted it retain the information when it restarts but it will just be at the ubuntu logo and just sits there for hours.  It didn't freeze because i see the four dot animations moving.

any thoughts? thanks in advance.

---

### Post by xcution on 2011-10-21
Another thing to note is when i manually type in the resolution command i cannot see my mouse cursor anymore.  It is still there but I can't visibly see it.

---

