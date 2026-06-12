---
title: "Printing Help"
date: 2010-07-26
forum: General Help
---

### Post by supradave on 2010-07-26
I've suddenly had to make a change to our network and we are temporarily completely wireless.  To make matters worse, people actually want to print.

So, I have my box with wlan0 on 192.168.253.  If I set a network up on eth0 of 192.168.252 and shared the printers out that way, would just sharing them through Samba work or do they need to have a 253 address?  Which would then lead me to having to bridge a bunch.

Thanks,
Dave

---

### Post by MaxIBoy on 2010-07-26
If all computers are running Linux, it's pretty easy. 

Suppose you are using the GNOME desktop environment (standard with Ubuntu.) On all the computers, run "system->administration->printing," then "server->settings." On the host, check "Publish shared printers connected to this system." On the other computers, check "Show printers shared by other systems." Then wait for a bit and the printers should show up.

If you use a different desktop environment (such as KDE from Kubuntu and XFCE4 from Xubuntu,) the exact steps might be a little different but it's very similar.

Suppose you are hosting a printer on an Ubuntu machine and you want to print from a Windows box? [This tutorial](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html) worked for me for Windows XP at least. Not sure about other Windows versions but it's worth a shot.

---

