---
title: "modem settings not remembered"
date: 2006-05-13
forum: General Help
---

### Post by pellgarlic on 2006-05-13
this is quite frustrating...

every so often (about half of the time in fact) when i open "network settings" to establish a dialup connection, the settings i entered previously (i.e.the phone number, user name and password to use) have disappeared. :-? 

am i missing something really obvious? is there a better way to manage my internet connection? i am using this method as it is the one i came across when "exploring" ubuntu after having first installed it.

it would also be cool if there was a way to connect automatically when i open firefox. is this possible? 

i'm in the process of trying to convert my girlfriend to linux (not literally of course, although that would have its benefits...) and when she asked me how to connect to the internet on my new ubuntu installation, she stopped listening after the first couple of sentences of my reply - she wants to just open the browser and have it connect itself, like in windows. 

i can live with the current method, although a simpler method would be nice, and it would make it a lot easier to convince my girlfriend that linux is better than windows! the lost settings is much more annoying though, anyone got any ideas?

---

### Post by pellgarlic on 2006-05-14
ok, i found a solution - first i tried the "modem monitor" applet (right click on top panel, "add to panel"), but for some reason, clicking on "activate" doesn't do anything, even though i entered the exact same information which works successfully with the "networking" option in  the "system > administration" menu, which the "modem monitor" applet appears to be identical to.

next, i downloaded "gnome-ppp" (see: [https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)), which acts in a very similar way to window's dialup connection dialog, and more importantly, works perfectly. :) 

(although wvdial, the program that gnome-ppp acts as a frontend to, gives me problems - it can't detect my modem. as it is a winmodem, i had a bit of hassle installing it in the first place, and i tried every combination of modem port i could think of: /dev/modem, /dev/modem0, /dev/ttyS0, /dev/ttyS1, /dev/536ep, /dev/536ep0 with wvdial, but to no avail. however, when using gnome-ppp, it accepts /dev/536ep0 as the location of the modem, and i am able to dialup successfully.)

---

