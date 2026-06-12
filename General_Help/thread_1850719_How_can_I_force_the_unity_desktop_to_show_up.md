---
title: "How can I force the unity desktop to show up?"
date: 2011-09-27
forum: General Help
---

### Post by olegsomphane on 2011-09-27
So I installed Heroes of Newerth on Ubuntu 11.04 and let it update on the first run. Without starting a game, I attempted to quit the game. However, the screen appeared to freeze on the game quit screen and I could not see the desktop. Moving the mouse around, it appeared that it was scanning the desktop - mouse cursor changed so that it would expand/contract my open terminal windows or to highlight text, etc. I tried Super+D x2, Super+1/2/3, and some other shortcuts but could not get the Desktop environment to show up. Finally, I press ctrl+alt+del and waited a minute for the computer to shut down, but it appeared frozen on the ubuntu shutdown screen (ubuntu with the five or so dots below it) and I was forced to use the hardware reset button. This did not reproduce the next time I ran Heroes of Newerth. I am running an AMD/ATI setup with proprietary drivers.

I was wondering, when something like this happens, is there a way I can safely restart the computer instead of using the hardware switch? Is there a way to force unity to restart or redraw itself?

---

### Post by mastablasta on 2011-09-27
control+alt+ F1...F7 i believe. this should get you into console. there oyu sign up with your user name and password and execute the shutdown command
 
```
man shutdown
```--- for info on command or have a look here as well: [http://www.computerhope.com/unix/ushutdow.htm](http://www.computerhope.com/unix/ushutdow.htm)
 
```
 
sudo shutdown -r now

```
 
will restart the computer. -h switch should shut it down.

---

### Post by olegsomphane on 2011-09-28
Thanks, will keep that in mind :)

---

