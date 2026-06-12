---
title: "cant boot 11.04 graphics card driver issue i think"
date: 2011-04-30
forum: General Help
---

### Post by tetsu7 on 2011-04-30
i was trying to uninstall old nvidia driver and install new driver via terminal. i used these commands (sudo dpkg -p nvidia -173; sudo apt-get --purge autoremove) and then this is the one that froze up on me (sudo apt-get install nvidia-current)computer froze while installing the new driver. now i cant boot up ubuntu 11.04. i get the grub menu but cant boot OS. i cant get recovery mode to boot either. it stops after it reads my dvd drive. i dont remember exactly what i did to get this message but i got a message that says alloc magic is broken at 0xb7ce5c80. im assuming that i have no graphics card driver installed and this is why i cant boot. is there anyway to boot from a live cd and manually install the graphics card driver? im on a dual boot with win7 and upgraded from ubuntu 10.10 so i dont really want to do a clean install and have to install tons of software etc. thank you in advance to anyone that can offer me any adviced.

---

### Post by Frogs Hair on 2011-04-30
A couple questions , was the driver removed prior to upgrade and was there some reason you could not remove the 173 driver with the driver jockey ? Any residual configuration could have been removed with the Synaptic Package Manager.

---

### Post by tetsu7 on 2011-04-30
i removed the driver after the upgrade. i was having problems getting compiz to work and my wallpaper would not change. im not sure what a driver jockey is. im new to linux im in my last 2 weeks of an intermediate linux class. my linux exposure hass been almost 4 months and 98% of it has been in the terminal. the gui is very new to me. anyway by jockey if you mean additional drivers i went there but it wouldnt let me remove the old driver. i had the old one and the new one installed at the same time. the new one i installed yesterday. anyway ive been having issues so i was hoping if i could uninstall the old one i may have better luck. i know alot of people have been having issues with the new nvidia driver. anyway i ran from the terminal the command to uninstall the old one and then the command to make sure my driver was the correct one, or so i thought.thats when my computer locked up. i ran these same commands on another machine yesterday with no problems.

---

### Post by tetsu7 on 2011-04-30
ok after trying to boot more times than i can count it all of a sudden booted up. im at the login splash screen. before i can login a message popped up that says "a program is still running" in the window it says "unknown not responding" under that it says "waiting for the program to finish. interuppting the program may cause you to lose work." it gives me three options: lock screen, cancel, log out anyway. what should i do? im afraid to do the wrong thing and not be able to get back to this blessed login screen.

---

### Post by tetsu7 on 2011-05-01
i chose logout and i was logged back into ubuntu where i ran the driver commands again and problem solved. still cant use compiz but thats another matter.

---

