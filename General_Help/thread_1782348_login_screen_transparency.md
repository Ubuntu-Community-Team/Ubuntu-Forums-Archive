---
title: "login screen transparency"
date: 2011-06-14
forum: General Help
---

### Post by link15 on 2011-06-14
I found out how to change the clorors, themes, fonts,etc by using this command ```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

```and a way to open ccsm (compizconfig settings manager) ```
sudo cp /usr/share/applications/ccsm.desktop /usr/share/gdm/autostart/LoginWindow

``` but how do I make it transparent, I tried to do it with the opacity feature in ccsm, but it didn't do anything, so how do I activate transpareny? is it even possible?

---

### Post by link15 on 2011-06-14
any ideas?

---

### Post by link15 on 2011-06-14
I got it to work with this[http://ubuntuforums.org/showthread.php?t=1333683]("http://ubuntuforums.org/showthread.php?t=1333683"):popcorn:

---

### Post by smithark on 2011-06-15
thanks a lot..

---

### Post by link15 on 2011-06-15
glad I could help:p

---

### Post by Rasa1111 on 2011-06-27
> **link15 said:**
> I got it to work with this[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683):popcorn:
Would you like to elaborate on how exactly you got your login window transparent? 
The link isnt doing me much good. 
giving me 404's on links and what not. 

All I need is to make my login window about 50-60% transparent. 

Thanks for any help you can give.

---

### Post by waveOSBeta on 2011-07-20
I need some help with this as well.

---

### Post by link15 on 2011-07-21
change the window manager to compiz using these commands ```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/wm_use_compiz --type bool true
``` ```
sudo -u gdm gconftool-2 --set /apps/metacity/general/compositing_manager --type bool true
``````
sudo dpkg-divert --local --rename --add /usr/share/gdm/autostart/LoginWindow/metacity.desktop
``` ```
sudo cp /usr/share/app-install/desktop/compiz.desktop /usr/share/gdm/autostart/LoginWindow
```, and then add ccsm (compiz config settings manager) to the gdm startup (to do this. logout and then log in to ubuntu classic go to system: preferences: compizconfig setting manager and right click it and select "add this launcher to desktop" then open a terminal and type in ```
sudo nautilus /usr/share/gdm/autostart/LoginWindow
``` and click and drag the ccsm icon on the desktop into the window that opened) , if its not already installed, search for ccsm in the software center and install it, then logout and click on opacity, brighness and, saturation, then click on the "opacity" tab ,then, click on the "new" button then click the plus button and click the "grab" button and click on the area you want to make transparent and adjust the "window values" to adjust the transparency then close ccsm, and, log back in and delete ccsm from the gdm startup, and, :) your done!

---

### Post by waveOSBeta on 2011-07-21
Thanks! :D

EDIT: Just tried, didn't work.. :(

---

### Post by link15 on 2011-07-22
> **waveOSBeta said:**
> Thanks! :D

EDIT: Just tried, didn't work.. :(

[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683) 
just follow that link and try to set the window manager to compiz using the guide I just linked to above

---

### Post by waveOSBeta on 2011-07-23
> **link15 said:**
> [http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683) 
just follow that link and try to set the window manager to compiz using the guide I just linked to above
No, compiz works fine. The ccsm just appears all weird.

---

### Post by link15 on 2011-07-25
> **waveOSBeta said:**
> No, compiz works fine. The ccsm just appears all weird. does ccsm work normally? if it doesn't then you should try reinstalling ccsm

---

