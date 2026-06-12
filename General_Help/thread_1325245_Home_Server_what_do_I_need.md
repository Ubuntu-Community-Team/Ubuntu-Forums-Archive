---
title: "Home Server what do I need"
date: 2009-11-13
forum: General Help
---

### Post by Entropie on 2009-11-13
This is my first post and I am a complete noob to Ubuntu so please forgive any faux pas. 
 
I am looking into building a home server for the house and I was looking into using Ubuntu. 
 
HARDWARE
I have a mini-itx M11 10000 with 1GB RAM. I plan to install a SATA raid controller with 2 500GB disks in a mirrored config. 
 
I will be using a Windows PC to connect to it but plan to expand to an Acer Revo LINUX (Upgraded to Ubuntu) and possibly a work Mac laptop.
 
LAN
It will initially connect via WLAN 11G until I can get a network wired into the house. I currently connect to my ISP via a WLAN modem router. I am aware of WLAN limitations hence the planned wiring project.
 
USAGE
I want to use the server as a central storage repositry for Pics (Win and Mac compatible formats) , Docs, music , video (most formats) and Iplayer HD downlads. In addition I want the server to pull mail from my ISPs POP3 server and store them centrally plus I want run Torrents from it as well. Finally I would like some sort of family calendar.
 
Based upon my requirements is it possible and what do I need. Is there anything that I have missed that I should consider?
 
Thanks

---

### Post by Kelvin Gardiner on 2009-11-13
The full Ubuntu server guide can be found here:

[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

Have a look at section 17 for Windows networking.

Also, the is a step by step setup guide here:

[http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2)

Both these pages have 8.04 (the long term support release) if your using that version on Ubuntu.

You may want to have a separate partition for storing files, as is normal with /home directory. So if you need to reinstall Ubuntu in case of some disaster you don't need to touch the stored files.

---

