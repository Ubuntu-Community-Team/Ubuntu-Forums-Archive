---
title: "gnome not starting!!!"
date: 2006-02-17
forum: General Help
---

### Post by rkakkar on 2006-02-17
the machine is booting up. after the initial boot, i get to the point just before the login screen in ubuntu. all i can see is the default brown screen with my mouse pointer. it does not go ahead. this happened once i set to auto login into my account..i did alt+shift+1 and it took me to the terminal with a login prompt. rebooted and it again froze at that point.

---

### Post by hellraiser_rob on 2006-02-17
after the login prompt can't you just go

startx

?

---

### Post by rkakkar on 2006-02-17
[QUOTE=hellraiser_rob]after the login prompt can't you just go

startx

?[/QUOTE]

after deleting the lock file, i did do startx. but same situation. plus the graphics were inferior (presume it was Xwindows and not gnome) because that plain brown wallpaper became a patterned gray wallpaper

---

### Post by SivArt on 2006-02-17
Yes, [FONT=Arial]I agree with [/FONT]**[FONT=Arial]hellraiser_rob,[/FONT]**[FONT=Arial] try to start the x system manually by issuing the "start  x" command:KS, If that works, you just need to configure some files to make the x-window to run at startup!!!!


[/FONT]

---

### Post by SivArt on 2006-02-17
Did you check the settitngs on X window???
I think you have a missconfiguration:(

---

### Post by hellraiser_rob on 2006-02-17
have you installed some graphics card drivers recently....if so were they nvidia ones or ati ones?

---

### Post by SivArt on 2006-02-20
If you have an nVidia or an ATI card you must review the field nottices that those cards have, this is because this cards have special features and you must download the drivers and install them; you can also set you video card settings manually and verify if you have the correct screen configuration.
Sometimes, that make Xwindow to work a little bit madly :D.

---

### Post by Kagey on 2006-02-20
Are you sure it was frozen? You could have set a high resolution and have a scrolling desktop, in which case you would see the center of the wallpaper and cursor. try moving the mouse up to the top of the screen and see if the desktop scrolls up.

---

### Post by SivArt on 2006-02-21
If the screen is completely frozen, try to issue the ctrl+alt+backspace to restart the Xwindow server
> Are you sure it was frozen? You could have set a high resolution and have a scrolling desktop, in which case you would see the center of the wallpaper and cursor. try moving the mouse up to the top of the screen and see if the desktop scrolls up.

---

