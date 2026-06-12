---
title: "Dial Up on Ubuntu"
date: 2005-02-18
forum: General Help
---

### Post by Rock on 2005-02-18
Is this possible to get dial up working on Ubuntu with the same that came with it? I have a friend who wants to put Ubuntu on his PC but he uses dial up.

---

### Post by somuchfortheafter on 2005-02-18
letss see assuming that you have high speed, let your friend bring his pc over and install it so you can have the latest of everything then you should be able to use ppp configurations, all i can say is google it because i dont remember the exact specifics but there are tools for kde and gnome

---

### Post by friendly_guy on 2005-02-18
I have dial-up working on ubuntu.  You need to use the 'computer =>system configuration =>users' tool to add the user to the 'dip' group and then configure the connection by opening a terminal and typing 'sudo pppconfig' and following instructions.  To dial in type 'pon' and to disconnect type 'poff'.

You can add 'modem lights' to the taskbar afterwards to dial in with the mouse.

Modems can be an issue as many need (windows) software, they are called winmodems.  The easy way if you modem is not supported is to buy a serial modem - thses connect to the pc's serial port & are usually quite cheap.  

You can get many winmodems working under linux - just google 'linmodems' & follow the links.

Hope this helps

Guy

---

### Post by Rock on 2005-02-21
[QUOTE=somuchfortheafter]letss see assuming that you have high speed, let your friend bring his pc over and install it so you can have the latest of everything then you should be able to use ppp configurations, all i can say is google it because i dont remember the exact specifics but there are tools for kde and gnome[/QUOTE]Yeah I have 5Mbps high speed internet and my friend has 56k. We might do that.

---

### Post by piedamaro on 2005-02-21
I use gnome-ppp :)

---

### Post by darkoptix on 2005-02-21
Personally I use gnome-ppp for dialing, i could never get modem lights working...
For setting it up, as long as he has a hardware modem / stupid winmodem that has linux drivers, he should be fine.  However if not, then don't bother. You may want to do some research if the modem works in linux before proceeding.

---

### Post by jllitvay on 2005-04-06
I have the same problem with my USR2976 hardmodem. I got a script that make ubuntu detect it, dial via pppconfig/pon , make the modem noises but do not connect. pppnegociation failed.
Any help?

gnome-ppp is a apt-package? I didnt find it! wat is it package name? it come installed with ubuntu 4?

---

### Post by Alex4R on 2005-04-06
Also, make sure that the ISP doesn't require him to use software as it may not be available for Linux. If he uses Netzero, there is a way around the software.

---

### Post by jimbalaya on 2006-04-20
I am a newbie to Linux. I use a USR serial modem and used the networking tool to connect to my MSN dial up account. I think I have it configured properly I hear the modem dial and still get no connection. Just the operator saying please hangup and try again.

Any answers would be greatly appreciated.:p

---

