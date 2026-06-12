---
title: "ATI Graphics Card controller not working properly"
date: 2011-03-31
forum: General Help
---

### Post by carega on 2011-03-31
Hello! I'm having a problem here with my graphics card. Until not very long ago I was using the controller Ubuntu downloaded for me. However I recently downloaded another one from the ATI page, called ati-driver-installer-11-3-x86.x86_64.run and installed it.
So far, I've encountered two new problems:

1. The ATI Catalyst Control Center would not open after I setup the Tear Free Desktop.
1. The computer is running slow. Files take longer to open, minimizing and maximizing windows takes longer. Wi-fi connection takes longer to connect, etcetera. Overall, everything is going slow.

Are these problems related? I would like to uninstall the driver as the computer was working just fine before.

In addition to this, I  have firefox 4.0 and the colors on most of the images are darker than they should. The images look fine on other browsers except firefox. I read I had to do type "about:config" in the address bar, find "gfx.color_management.mode" and change the value from 2 to 0. What did I exactly do there? I took the advice from this thread: [http://ubuntuforums.org/showthread.php?t=1237366&highlight=radeon+hd+3200](http://ubuntuforums.org/showthread.php?t=1237366&highlight=radeon+hd+3200)

This is the graphic card I have:

```
 01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
``` Can anyone tell me how can I uninstall the driver or solve the problem? Thank you!

---

### Post by wolfen69 on 2011-03-31
Did you install **libqtgui4** also? It is recommended to do so.

---

### Post by carega on 2011-03-31
ok, before I read your reply I uninstalled the driver. I rebooted my computer and all I see now is a terminal. What can I do? I have no idea what's going on.

EDIT: I'm gonna go step by step, writing as much detail as possible, so you can tell me what happened and what's going on.

1. I downloaded ati-driver-installer-11-3-x86.x86_64.run and installed it.
2. Rebooted computer. After reboot I experienced the problems I wrote on my first post.
3. Uninstalled the driver through ```
 sudo sh /usr/share/ati/fglrx-uninstall.sh 
```4. Rebooted again. After reboot all I could see was a terminal opening, asking me to log in. After I logged in it even greeted me and all. I got my friend's computer and tried "sudo gnome-panel" but got this message: 
```
(gnome-panel:1434): Gtk-WARNING **: cannot open display:
```
I tried installing the ati driver again but still got no luck.
5. Tried "startx" but got no luck as well. I found this thread ( [http://ubuntuforums.org/showthread.php?t=1659017](http://ubuntuforums.org/showthread.php?t=1659017) ) and recovered my gnome desktop doing this:
```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
startx 
```I don't know if I still have the ATI controller or the one I had before that. I pretty much have no idea what I did with the last "mv", I just know the computer is working fine right now and I'm scared of turning it off. If I turn it off will I get the terminal again? Help!!

---

