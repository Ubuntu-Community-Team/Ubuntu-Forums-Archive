---
title: "few questions."
date: 2009-08-05
forum: General Help
---

### Post by Kd40 on 2009-08-05
hey i got a few things i'd like to do with my linux so i'll ask them all at once.

i'd like to know how to change my mouse cursor.

how to install a splash screen.

how to install the cairo dock.

and how to make a reflection on the bottom of my cube when i go into 3d mode you know the old ctrl+alt+mouse 1 trick in compiz. thanks.

---

### Post by philcamlin on 2009-08-05
> **Kd40 said:**
> hey i got a few things i'd like to do with my linux so i'll ask them all at once.

i'd like to know how to change my mouse cursor.

how to install a splash screen.

how to install the cairo dock.

and how to make a reflection on the bottom of my cube when i go into 3d mode you know the old ctrl+alt+mouse 1 trick in compiz. thanks.

heres for the dock [http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/](http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/)

and for the splash look at point 6 [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by 3rdalbum on 2009-08-05
1. System > Preferences > Appearance. Click Customise. Go to the Pointer tab and choose a different one.

3. System > Administration > Synaptic Package Manager. Do a search for "cairo-dock". Right-click, choose Mark For Installation. Click Apply.

---

### Post by Kd40 on 2009-08-05
ok, i just tried the cairo dock vier synaptic packet manager but it seems it wont let me tick one of the files...i was messing round trying to install earlier so maybe i have 1 or 2 files installed that shouldnt be. how would i uninstall those little files?

---

### Post by Kd40 on 2009-08-05
and also the pointers that our in the pointers tab, are they the only ones you can use? because i saw some i wanted to download and use.
*edit* worked out how to do the pointers thanks.

---

### Post by Kd40 on 2009-08-06
'3. System > Administration > Synaptic Package Manager. Do a search for "cairo-dock". Right-click, choose Mark For Installation. Click Apply.'

done that and it came up iwth this error message...
"cairo-dock-data: Depends: cairo-dock but it is not going to be installed"

---

### Post by Kd40 on 2009-08-06
also, splashscreen seems to not work anymore, and when i start up no imagery just lots of code.

---

### Post by fabounet on 2009-08-06
```
apt-get remove --purge cairo-dock cairo-dock-plug-ins
```
then, activate the Cairo-Dock's repository if not already done (see [here]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")), and ```
apt-get install cairo-dock cairo-dock-plug-ins
```

---

### Post by Kd40 on 2009-08-06
ok did all that then put in the last code.

this error message came up
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

as far as i know i am root. i dont get it?

---

### Post by nbtrap on 2009-08-06
To run a command as root, type the word "sudo" before the command. So:

```

sudo apt-get remove --purge cairo-dock cairo-dock-plug-ins

```

It should then prompt you for your password.

---

### Post by Kd40 on 2009-08-06
ok i done all those install methods and such, and i see no dock :confused:, just the normal display.

---

### Post by nbtrap on 2009-08-06
Check your menus.

---

### Post by Kd40 on 2009-08-06
well just gone through apps and all that and everything looks the same as before.

is there some terminal code that will tell me if i have it installed or something? i did install it but it may gave a little bit more info.

---

### Post by nbtrap on 2009-08-06
Open up a terminal. Type:
```

sudo synaptic

```

Once synaptic launches, type "cairo-dock" into the search box. If you have it installed, its box will be filled-in. Otherwise, right click on it, select "Mark for Installation" then hit "Apply". It will probably prompt you for confirmation.

When I installed it, it appeared under "utilities" in my menu, but I'm running KDE. Can someone with gnome please verify that cairo-dock is installed to the gnome menu by default?

Anyway, once it's installed (or if it's already installed and still not in your menus), open up a terminal and type:

```

cairo-dock

```

to launch it from the terminal. You'll then want to create a menu launcher so you don't have to run it from a terminal window every time, but I'm pretty sure it should appear somewhere in your menus.

---

### Post by Kd40 on 2009-08-07
k went to it and it came up with the last error, seems it is something to do with the repositaries, not really sure how the repositaries work so tell me if im wrong, but i did have a little dig around and found some of the files (that i think i installed vier terminal) in the third party software section there is a url to cairo docks ```
http://repository.cairo-dock.org/ubuntu
```

and then in the aunthentication section there is something saying...
```
Cairo-Dock Team (cairo-official repositary)
``` with like a email kind've thing to finish it off.

are these the right files?...also i can film it and put on youtube and add a link here so you can see what i meen.

---

### Post by fabounet on 2009-08-07
make your life easier :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

### Post by Kd40 on 2009-08-11
ok found it and all, decided i did'nt like it and want to uninstall. what would be terminal code? lol

---

