---
title: "Broadband Help"
date: 2010-03-25
forum: General Help
---

### Post by Skip Williams on 2010-03-25
Just installed Ubuntu 9.04 on my laptop.  I have a verison Broadband connection. The software seemed to recognize the Vz Connection but didn't start automatically.  I have manually installed the VZ phone number but still can't get connected to the net.  I assume I am doing something wrong.  Any suggestions??

---

### Post by 2hot6ft2 on 2010-03-26
Maybe this will help
> **fheinsen said:**
> I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install gnome-ppp -- this is the application you will use to connect, and do the following:

**Step 1.** Plug the modem in on a freshly restarted computer.
**Step 2.** Launch gnome-ppp as superuser (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))

---

