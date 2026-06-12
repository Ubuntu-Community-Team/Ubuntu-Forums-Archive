---
title: "Connect to Ubuntu home folder with Samba in Windows 7"
date: 2009-09-26
forum: General Help
---

### Post by wesg on 2009-09-26
I'm testing the waters of Windows 7, and I'd like to connect to my home folder on my Ubuntu server. I can connect to any standard SAMBA share, but I can't figure out how to connect to the 'homes' share.

How can I authenticate into my home folder? I think it should be the same among all windows OSs.

---

### Post by swerdna on 2009-09-28
Use the address \\ubuntu_net_name\your_username

But first you must add the credentials for your_username into the samba user database using smbpasswd.

FFI see the segments titled [COLOR="Blue"]**[homes] Users' Roaming Shares**[/COLOR] and [COLOR="Blue"]**Permission to Access Ubuntu Shares**[/COLOR] in this tutorial: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

