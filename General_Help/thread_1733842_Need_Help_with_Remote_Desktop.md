---
title: "Need Help with Remote Desktop"
date: 2011-04-19
forum: General Help
---

### Post by _Aninemity on 2011-04-19
I am as lost as can be. I have a brand new server running Ubuntu. A lot of the GUIs were setup for me. I am now trying to remote desktop into the system from my Windows 7 machine. I've setup the remote desktop preferences to allow others to control it and to require a password.

I've tried accessing the IP adress that setup gave me through the windows 7 remote desktop connection. It's saying that the remote machine doesn't exist.

I figured it wouldn't be that simple, but as I'm so new to servers, all the links I could find on google were over my head on how to get this working.

Any help would be greatly appreciated! Thanks in advance!!

---

### Post by mikewhatever on 2011-04-19
Are you referring to the Ubuntu Desktop Edition (Gnome Desktop) as your server? If so, what is used remote connection on Ubuntu and W7?

If you do run a server (not desktop), Webmin is a nice browser based GUI, and you can also use ssh to get access to the server.

---

### Post by ttshivers on 2011-04-19
You might want to use VNC to remotely access your computer. Here is a tutorial on how to set up VNC:[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

---

### Post by ttshivers on 2011-04-19
TeamViewer might do the trick for you also: [http://ubuntuforums.org/showthread.php?t=896283]("http://ubuntuforums.org/showthread.php?t=896283")

---

### Post by capla on 2011-04-19
I use UltraVNC on windows7 since it free and straight forward.  You can then use the software that comes with Ubuntu for VNC client and server (vinagre and tsclient).  I regularly remote desktop to windows7 and xp machines from by Ubuntu desktop.  Similarly it should be straight forward the other way round :)

---

