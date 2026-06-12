---
title: "desktop drapes"
date: 2010-01-08
forum: General Help
---

### Post by gokul10 on 2010-01-08
i cannot install desktop drapes from ubuntu software center it says not available for the current data i hav attached a screen shot of the program pls help thnks

---

### Post by gsmanners on 2010-01-09
Go to System / Administration / Synaptic Package Manager and click on "Reload". That should fix it.

---

### Post by rabdoel on 2010-01-09
and once you have installed it ... you might find that it does not autostart ..

if that is the case you will need to edit the following file 

home/username/.config/autostart/drapes.desktop

and add the following line to the bottom of the page 

"Type=Application"

taken from - [https://bugs.launchpad.net/drapes/+bug/292051](https://bugs.launchpad.net/drapes/+bug/292051)

I had this problem in karmic koala 9.10

so press alt+F2 .. in the box that appears type "gnome-terminal" and press run

now in the terminal screen type
sude gedit  home/username/.config/autostart/drapes.desktop  ( where username is your own username) 

desktop.drapes file will come up and add the following on the last line 
"Type=Application"

press save and now logout and log back in again .. that should fix it

---

