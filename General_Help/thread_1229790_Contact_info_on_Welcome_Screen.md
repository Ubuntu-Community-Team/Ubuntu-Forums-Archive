---
title: "Contact info on Welcome Screen"
date: 2009-08-02
forum: General Help
---

### Post by Upkeep on 2009-08-02
Hi! I'm running Ubuntu 8.10 on an HP2133 Mini-Note netbook, Via C7M 1.2 GHz processor, 2Gb RAM. It's my first experience with Linux (I don't count the couple of weeks fighting with the SLED10 o/s originally installed), so far, so good.
 
This netbook is small and could easily be left behind somewhere, so I wondered if it was possible to modify the welcome/login screen to include a phone number or other suitable contact details - just in case it gets found by a kind person.
 
Any ideas?
 
Thanks
Upkeep

---

### Post by smile-its-smiley on 2009-08-02
if you go to system > administration > login window > local

at the bottem there is a welcome just write your contact details in there.

---

### Post by Upkeep on 2009-08-03
That's what I thought, but it doesn't seem to take effect for me. I checked etc/gdm/gdm.conf-custom and my welcome information is there. It just doesn't seem to get read at the appropriate time. There seems to have been a similar bug in Hardy (see link). I'll do a bit more research and see if I can work something out.
 
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg851896.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg851896.html)
 
regards
Upkeep

---

### Post by Upkeep on 2009-08-04
In the end I opened a terminal, typed **sudo gimp** to open Gimp as root and opened usr/share/gdm/themes/human/background.png (I think it was .png).  I stuck a textbox with my contact details in it onto the background image and saved it.
 
Re-started to check it out and it worked a treat.
 
Upkeep:D

Update: I tried a few of the other greeters on offer, like circles and happy gnome and lo and behold the welcome message was displayed!  It seems that human.xml lacks the coding to display the message!

---

