---
title: "problem with desktop panels"
date: 2009-11-09
forum: General Help
---

### Post by zaydius1729 on 2009-11-09
hello everyone. i need some help. i upgraded ubuntu a few days back to 9.10 and i was just playing around with my desktop and moved the top panel down on the bottom and it was also set at "hiding" when i moved it down. there was the normal panel on the bottom too where it shows the two desktops on the bottom right corner and whatever programs ur running as well... 

but once i did that... all the panels just vanished and theres just a gray bar on the bottom. i cannot access anything including the administration, and all those things. so i was wondering if there is anyway to reset the desktop settings without being able to go to the terminal or any of it. i would really appretiate any help.

---

### Post by wojox on 2009-11-09
Open your home directory. 
Press Ctrl+H
Go to /.gconf/apps/panel
Rename panel panel.old
Logout and back in.

---

### Post by zaydius1729 on 2009-11-09
i could not access the home directory.. when i get to the desktop i cannot do anything.i tried the ctrl h. i couldnt even get anything when i pressed ctrl+alt+del. so i dont know whats wrong. is there any way to fix this from like the recovery mode or anything??

---

### Post by zaydius1729 on 2009-11-09
i really need some help with this guys. i dont know if theres like a MS-DOS thing. also is there anyway i can just reset all of ubuntu.

---

### Post by hossdozero on 2009-11-09
try moving it from one of the tty terminals before you login

at the login screen press ctrl+alt+F1-F6

type

```
sudo mv /home/username/.gconf/apps/panel /home/username/.gconf/apps/panel.old
```

then log back in

---

### Post by zaydius1729 on 2009-11-09
didnt work. 

it said that there was no such directory for "/home/username/.gconf/apps/panel" wondering if im typing it wrong if there are any spaces in there that i dont know.

---

### Post by hossdozero on 2009-11-09
Just to be clear, when you typed it, did you replace the /username portion with your username?

---

