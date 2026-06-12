---
title: "Netbook windows too big"
date: 2011-05-25
forum: General Help
---

### Post by Condor Cluster on 2011-05-25
Hi,
 
just reinstalled Lucid on my netbook, everything is running fine.
 
The question I have is when I open certain windows (like disk utility or file properties for example), the bottom does not fit onto the screen, so I have no way to see or click the buttons at the bottom.
 
Is there a workaround this? (even some way to 'scroll' down a window box would be handy!)
 
Thanks.

---

### Post by 5149.5 on 2011-05-25
In a terminal, enter:

```
sudo xrandr --output LVDS1 --fb 1024x768 --panning 1024x768
```If you like the effect, you can put the same thing in startup applications so it runs at each boot.

---

### Post by tredegar on 2011-05-25
Or you can hold down ALT L-click anywhere on the window and drag it until you can see the buttons.

---

### Post by Condor Cluster on 2011-05-26
Thanks all.

Holding down the Alt key seems like a good workaroung for netbooks :D

---

