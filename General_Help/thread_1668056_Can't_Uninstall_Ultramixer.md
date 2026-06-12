---
title: "Can't Uninstall Ultramixer"
date: 2011-01-15
forum: General Help
---

### Post by rf.bennett1 on 2011-01-15
Dear Ubuntu,

I downloaded Ultramixer just to test it out and see if it's any better than Mixxx and i decided that Mixxx is miles better so...i thought to myself i might aswell uninstall Ultramixer. So i when to the uninstaller folder and right clicked the jar file and asked java to uninstall the program. Unfortunatly it does nothing apart for making my desktop blink once....so i checked to see if i can just delete the file which it won't let you (it install the files in usr/local. So since i'm still on the learning curve is the a command i can put into terminal and delete this software? Also after the last update of my system and i was asked to restart in order to complete the update which was dated "Fri Jan 23.43pm" while my system was restarting just before i got the the logon screen everything froze screen went black and i had to cut the mains power to turn off my machine and reboot again so was wondering what happend? is there a way to find all my system logs?

Thanx for reading and any info or help regarding Ultramixer or recent update i had will be extremly greatfull

P.S. Yesterday i managed to convert all my friends to Ubuntu except one who is already using Linux Mint.

So i'm off for a smoke and i await to repies :D

Rob ;)

---

### Post by Pollox on 2011-01-16
> **rf.bennett1 said:**
> 
So i when to the uninstaller folder and right clicked the jar file and asked java to uninstall the program. Unfortunatly it does nothing apart for making my desktop blink once....so i checked to see if i can just delete the file which it won't let you (it install the files in usr/local. So since i'm still on the learning curve is the a command i can put into terminal and delete this software?


Try running the uninstaller from terminal with "sudo", i.e. "sudo java -jar pathtouninstaller. Or if you just want to delete files from /usr/local, press "Alt+F2" to start the gnome application launcher, and type "gksudo nautilus" to start the file browser with sudo permissions.

> 
Also after the last update of my system and i was asked to restart in order to complete the update which was dated "Fri Jan 23.43pm" while my system was restarting just before i got the the logon screen everything froze screen went black and i had to cut the mains power to turn off my machine and reboot again so was wondering what happend? is there a way to find all my system logs?


System > Administration > Log file viewer will show you system logs. This is a separate issue so it would be best in a separate post if you need more help with that (I have nothing more to offer on it, sorry).

---

### Post by rf.bennett1 on 2011-01-16
Thanx for your reply :)

The only way it would let me uninstall ultramixer was to hit ALT + F2 and it work a treat.

I will look through my system logs and make a seperate post.

Thanx again :)

---

