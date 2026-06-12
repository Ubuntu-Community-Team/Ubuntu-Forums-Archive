---
title: "Help with remote desktop"
date: 2011-03-24
forum: General Help
---

### Post by emilward on 2011-03-24
I am completely new to Linux in general but I want to remotely access my mom's computer which has XP on it using my laptop which has Ubuntu 10.10 Desktop edition. I already enabled "remote desktop" on her machine as well as set up "port forwarding" on her router. This is where I get stuck. I have tried remote desktop viewer in applications but when I input her IP address all I get is a black screen. I tried Terminal Server Client (saw a tutorial on youtube about it) and that does nothing. Next I tried the terminal using the command "rdesktop 192.168.x.xx" (where x is her address) and all I get is a message saying "autoselected keyboard map en-us" and thats it. nothing else happens. Again i am new to linux so I am assuming I am screwing up the process somewhere. Can anyone help me?

---

### Post by Old *ix Geek on 2011-03-24
Do you have desktop effects enabled? (The eye candy stuff, like desktop cube.) I had similar problems using remote desktop (to other Linux computers, not windows) until I shut off desktop effects.

---

### Post by flyingsliverfin on 2011-03-24
are you trying to access her computer from an internal network or from ouside the router?

if from outside, you can't use the 192.168...

---

### Post by lmarmisa on 2011-03-24
Welcome to the forums.

I believe your main problem is related to you mom's IP Address. 192.168.x.xx is not the remote IP address you have to use. This is only a [private IP address]("http://en.wikipedia.org/wiki/Private_network") and it is not valid out of the scope of your mom's [local area network]("http://en.wikipedia.org/wiki/Local_area_network") (LAN). You should know her public IP address. This link can help you for knowing that public IP address:

 [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

A better alternative is to use a Dynamic DNS service like [http://www.dyndns.com/](http://www.dyndns.com/) or [http://www.no-ip.com/index.php](http://www.no-ip.com/index.php) .  This service allows to use a label for connecting to your mom's computer. A basic DDNS service is free.

If you know the correct public IP addres or you use a DDNS service and if the configuration of the remote desktop function is correct (do not forget to allow the access from anywhere) and if you set up the ports correctly, you should be able to connect to the remote computer from Ubuntu using the Terminal Server Client (protocol RDP).

Another alternative that I recommend is to use TeamViewer:

[http://www.teamviewer.com](http://www.teamviewer.com)

The installation of this progarm both in XP and Ubuntu is very simple. TeamViever is a free program for personal use.

Best regards,

Luis

---

### Post by Zzl1xndd on 2011-03-24
+1 for teamviewer. Great software and works on Linux, Mac and Windows :D.

---

### Post by sml156 on 2011-03-25
You may also want to Google search for    enable concurrent user sessions on Windows   allow multiple user logon to windows    or this site tells you how to do it   [http://www.golod.com/2005/10/enabling-multiple-remote-desktop-sessions-in-windows-xp-professional-and-media-center-edition-2005/](http://www.golod.com/2005/10/enabling-multiple-remote-desktop-sessions-in-windows-xp-professional-and-media-center-edition-2005/)    Windows only lets 1 user log on to the computer this may also be giving you problems

---

### Post by sj1410 on 2011-03-25
i recommend teamviewer

---

### Post by Mathias1 on 2011-03-25
I'm using Gnome-RDP and it works great IMO.
Just make sure to set up your XP correctly ;)

---

### Post by emilward on 2011-03-25
Thanks for everyone's help. I didn't even realize I was not using the public IP address (duh!). Unfortunately that still did not work. When I use the public IP I still cannot get through, all I get is an error message. Either way, I'm just going to use Team Viewer. App installs easy and it works great. Thanks again for everyone's help.

---

