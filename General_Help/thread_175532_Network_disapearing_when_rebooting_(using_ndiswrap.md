---
title: "Network disapearing when rebooting (using ndiswrapper)"
date: 2006-05-13
forum: General Help
---

### Post by Morientes on 2006-05-13
Hi! I used the graphical front-end to ndiswrapper and installed my D-link DWL-610 network card. It seemed to work fine but now I have the problem that it doesnt work every time I reboot! I cant really see any pattern in when its working and when its not.
Whats happening is that when ubuntu is booting it hangs a lot longer where it says "configuring network adapters" (os something like that) and then the network doesnt work.
But sometimes it works...I am really confused. It seems like it forgetting some setting?

---

### Post by Dr. Nick on 2006-05-15
[quote=Morientes]Hi! I used the graphical front-end to ndiswrapper and installed my D-link DWL-610 network card. It seemed to work fine but now I have the problem that it doesnt work every time I reboot! I cant really see any pattern in when its working and when its not.
Whats happening is that when ubuntu is booting it hangs a lot longer where it says "configuring network adapters" (os something like that) and then the network doesnt work.
But sometimes it works...I am really confused. It seems like it forgetting some setting?[/quote]

Run "cat /etc/network/interfaces" and see if you have a ssid setup for your wlan0. If ou always use teh same ssid you may have good luck just hardwiring it in the file instead of making it search all the time

---

### Post by Morientes on 2006-05-26
I do have that...

I think the problem has to do with the PCMCIA device not beeing shut down properly when rebooting?
I believe I have isolated the problem to only occuring when I am rebooting from ubuntu to ubuntu and not when I start the computer after it has been turned off!
Anyone know what I might be able to do to make it shut down the devices better when rebooting? (if that is the problem...)

---

