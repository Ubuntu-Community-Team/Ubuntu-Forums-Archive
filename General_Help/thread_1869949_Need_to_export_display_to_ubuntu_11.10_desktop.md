---
title: "Need to export display to ubuntu 11.10 desktop"
date: 2011-10-26
forum: General Help
---

### Post by Hitech_Hillbilly01 on 2011-10-26
I am installing oracle rdbms on a server (aix) and need to be able to export display to my desktop so that I can run dbca and various other gui tools.

I can do this with ubuntu 11.04, used xhost to add ip, allowed x11 forward in ssh_config and updated gdm/custom.conf to set disallowtcp to false.

Now, I have replicated the xhost and the ssh settings on 11.10, but since it doesn't use gdm, but lightdm, I'm not sure how to get this to work.

Anyone out there have any suggestions?

---

### Post by Hitech_Hillbilly01 on 2011-10-26
Also updated /etc/lightdm/lightdm.conf with xserver-allow-tcp=true and still didn't work.

---

### Post by Hitech_Hillbilly01 on 2011-11-04
bump.  No one here has found need to export display to 11.10?  No biggie, as I am sticking with 11.04 for now, but seems like this would be something that is quite common (needing to do gui installs on remote servers).

---

### Post by SideTracked on 2011-11-08
Was struggling with this myself. Had a taste of success today.

On a fresh install of ubuntu 11.10 on my laptop I edited /etc/lightdm/lightdm.conf by adding the following as the last line in the file. I used nano as root to edit the file.

xserver-allow-tcp=true

Restarted the laptop after adding the above line, launched a terminal, added the server to the access control list (xhost +) and then ssh'd to the server that has the Sybase tools I needed to launch. The server name is promotion. Did this my normal way and it worked.

xhost +promotion

ssh promotion

Entered login info

At the prompt exported the display to my laptop's IP address

export DISPLAY=X.X.X.X:0.0

Then launched the app I needed. A few seconds later it popped up on my laptop's display.

You're setup may differ from mine but I hope this helps or at least gives you hope that it can be done. :)

---

### Post by gdr4479 on 2011-11-09
vi /etc/X11/xinit/xserverrc
#!/bin/sh

exec /usr/bin/X "$@"
#exec /usr/bin/X -nolisten tcp "$@"

---

### Post by Hitech_Hillbilly01 on 2011-11-09
Thanks for the replies.  I'll try and update with my results.

---

### Post by Hitech_Hillbilly01 on 2011-11-14
ok, adding xserver-allow-tcp=true to /etc/lightdm/lightdm.conf then xhost <servername>  works.  Requires either reboot or restart of lightdm before xhost.

Will try other solution next.

Thanks!!!!

---

