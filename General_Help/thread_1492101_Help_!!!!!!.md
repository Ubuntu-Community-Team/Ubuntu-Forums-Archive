---
title: "Help !!!!!!"
date: 2010-05-24
forum: General Help
---

### Post by whitetimer on 2010-05-24
Hi All

OK i have just done something silly.  I have Xubuntu installed and i opened Window Desktop Tweak i think and stupidly i enabled Composting and slid all the sliders the wrong way and now i cant see any of my windows ........

What do i do or how can i correct this as i cant see anything ?????????????????????/

Many Many Thanks

:(

---

### Post by sisco311 on 2010-05-24
Switch to a virtual terminal (Ctrl+Alt+F1), log in and run:
```
DISPLAY=:0.0 xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
```

[noparse]Press Ctrl+Alt+F7 (or Ctrl+Alt+F8) to switch back to the GUI.[/noparse]

---

### Post by whitetimer on 2010-05-24
> **sisco311 said:**
> Switch to a virtual terminal (Ctrl+Alt+F1), log in and run:
```
DISPLAY=:0.0 xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
```[noparse]Press Ctrl+Alt+F7 (or Ctrl+Alt+F8) to switch back to the GUI.[/noparse]

Hi ... Thankyou so very much, got it sorted ... Could you explain to me what that line does please ?

Many Thanks

---

### Post by deathadder on 2010-05-24
```
xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
```

-c: Is the channel you're going to modify, in this case it's xfwm4 the XFCE window manager, you could use xfce4-desktop for example to modify the desktop.

-p: The property to modify, this is what setting you want to modify within the channels settings. Here you're modifying the general/use_compositing setting.

-t: The property value type, the property listed with the -p argument can have different value types depending on the type of setting. The command will set it to a boolean type (true | false) 

-s: The new value to set for the property 

So what the command does is, exports the DISPLAY variable so that the command will modify the :0.0 display (the first X session started) and then run the xfconf-query command which sets the use_compositing setting to false (turning it off)

---

### Post by whitetimer on 2010-05-24
> **deathadder said:**
> ```
xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
```-c: Is the channel you're going to modify, in this case it's xfwm4 the XFCE window manager, you could use xfce4-desktop for example to modify the desktop.

-p: The property to modify, this is what setting you want to modify within the channels settings. Here you're modifying the general/use_compositing setting.

-t: The property value type, the property listed with the -p argument can have different value types depending on the type of setting. The command will set it to a boolean type (true | false) 

-s: The new value to set for the property 

So what the command does is, exports the DISPLAY variable so that the command will modify the :0.0 display (the first X session started) and then run the xfconf-query command which sets the use_compositing setting to false (turning it off)


Thanks for the explanation :guitar:

---

