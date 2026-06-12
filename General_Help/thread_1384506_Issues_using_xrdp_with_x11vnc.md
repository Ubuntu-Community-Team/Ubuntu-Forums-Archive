---
title: "Issues using xrdp with x11vnc"
date: 2010-01-18
forum: General Help
---

### Post by chitresh4u on 2010-01-18
I have successfully installed xrdp and x11vnc and I can login to my ubuntu from other windows system using rdp without any problem. But I am facing some issues. I have configured x11vnc so that I can login at GDM screen. Instructions are [here]("http://flukylogs.blogspot.com/2009/11/setting-up-vnc-for-gdm-login.html"). 

1) I can view my GDM screen using rdp from windows. But when I press enter after typing in my password (in order to login to ubuntu), the rdp session is disconnected and also GDM screen reloads (this may be the reason for disconnecting rdp session). Note that when I type in incorrect password it shows authentication error and rdp session is NOT disconnected. Also, I can successfully login when I use directly vnc to my view my GDM screen.

2) rdp shows some strange color depth when bitmap-compression is turned off.

3) What is the exact purpose of startwm.sh. Is it supposed to be executed automatically when rdp connection is successful. Can I to put some script like "vncviewer localhost -fullscreen" in it, so that I have to just enter my vnc password when I login using rdp.

---

### Post by chitresh4u on 2010-01-19
Anyone :(

Any help, suggestions, recommendations are most welcome.

---

### Post by krunge on 2010-01-19
I've never used xrdp, but there are some bugs in Xorg and/or GDM that cause the Xorg server to crash if you have x11vnc running on the GDM login window:

[INDENT][http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)
[http://ubuntuforums.org/showthread.php?t=965695](http://ubuntuforums.org/showthread.php?t=965695)[/INDENT]

those and other threads in these forums suggest some workarounds.

---

