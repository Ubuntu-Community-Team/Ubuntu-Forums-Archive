---
title: "Natty issues &gt; computer imploded"
date: 2011-04-29
forum: General Help
---

### Post by Gakumerasara on 2011-04-29
I performed a distribution upgrade last night.  As a result, I've had nothing but problems, and worse yet, I can't drop to the shell to even attempt to fix anything.  And apparently, according to messages that came up after it rebooted, my /home directories have been encrypted (who was the genius who decided to auto-encrypt /home folders?  so now I can't fix anything using a Live CD?).  :mad:

1) Despite all of my efforts, the Grub menu no longer appears, so I can't go into safe mode.

2) When I reach the login screen, I can't change any of the options at the bottom since none of my mice are being recognized (USB or PS/2).

3) Upon entering my password, 4 errors appear:

a) "Could not update ICEauthority file /home/xxx/.ICEauthority"
b) "There is a problem with the configuration server.  (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
c) "It seems that you do not have the hardware required to run Unity.  Please choose Ubuntu Classic at the login screen and you will be using the traditional environment"  Of course, I can't do this 'cause the f***ing mouse doesn't work!
d) "Nautilus could not create the following required folders: /home/xxx/Desktop, /home/xxx/.nautilus.  Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

4) And then... nothing.  just a blank background with a nonfunctional cursor sitting on it.  Ctrl-Alt-F{1,2,3,4,5,6} just take me to a screen with a bunch of lines across it; no terminal.

Any suggestions?

---

### Post by MnCC on 2011-04-30
Try chown -R on the folder eg:
chown -R admin:admin /home/admin

Hope this helps

---

### Post by Gakumerasara on 2011-05-03
> **MnCC said:**
> Try chown -R on the folder eg:
chown -R admin:admin /home/admin

Hope this helps

Ah yes, thank you.  I wasn't aware that ctrl-alt-T also brings up the terminal.

---

