---
title: "Can't Log In! 11.10 - GNOME"
date: 2011-10-17
forum: General Help
---

### Post by HandyAndyShortStack on 2011-10-17
Hey!
I haven't used ubuntu for a couple of years now, but I recently installed 11.10, and I LOVE IT!!!
Problem is, after a week of (nearly) bug-free operation, I can no longer log in!  My password is correct.  When I type it in in the login screen under the correct username, I get a purple screen, a little glimpse of the terminal, then I'm back at the login screen.

More info:  
I can log in just fine to terminals 1-6, but I can only do so much without my precious GUI.  Also, I can log in as a guest, but the interface is all messed up -no dock and windows cannot be moved, closed, or resized.  I have to use another terminal to shut down guest sessions.  Also the last session I was able to log into had some buggy behavior with the alt-tab menu.  I am using GNOME.  The only thing I really changed in my last session was to set the MySQL to start automatically on startup.

Anybody want to save the day?  I'm pretty much resigned to setting up a fresh install, but some insight would be nice.  Also, if I'm posting this in the wrong place just let me know :)

---

### Post by dhysk on 2011-10-17
I had much the same issue but it was from upgrading from 11.04 to 11.10.  You could try to delete the ~/.Xauthority file.  that fixed it for me.

The best thing to do would be rename it to something like Xauthority.bak or something.  Than try again.

---

### Post by HandyAndyShortStack on 2011-10-17
K I'll try that right now.  thx.

---

### Post by HandyAndyShortStack on 2011-10-18
Ok, it worked!
For any newbies that stumble onto this thread, here's what to do:
At the login screen, press CTRL+ALT+F1.
Login to the terminal with your username and password.
enter the following lines, where {{ username }} == your username:
```
cd /home/{{ username }}
mv .Xauthority Xauthority.bak
```
Now press CTRL+ALT+F7.
You should be able to login normally :)

---

### Post by Bones80 on 2012-01-30
Does not work for me. I installed 11.10 on a blank HD. Everything works except wireless. It asks for password but will not accept the correct one that works on all my other computers, windows 7 and my iPad.
I can't get into sudo.

---

