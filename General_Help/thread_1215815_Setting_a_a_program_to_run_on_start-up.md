---
title: "Setting a a program to run on start-up?"
date: 2009-07-17
forum: General Help
---

### Post by Dylan Bartlett on 2009-07-17
Hey. I'd like to make an RSS aggregator called Yarssr to run on startup. I get to sessions preferences but i dont know the program command to put in the command box. Does anybody know the Yarssr command? And can anbody tell me how to determine the command for future reference.

Thanks

---

### Post by lukeiamyourfather on 2009-07-17
If the program is in the applications menu then right click it and add it to the panel, from there you can see what command it uses. There might be others but that's how I do it.

For launching an application at startup I'd use ~/.profile which is run each time you login. A system wide alternative would be /etc/rc.local but that's run for every user. Cheers!

---

### Post by Dylan Bartlett on 2009-07-17
Thanks. I used your suggestion on using the panel to find the command.

Just so you know an easier way to add a program on start-up is to to to system>preferences>sessions and then add the program to the list.

Thanks again :D

---

### Post by MaddMatt on 2009-07-18
Hey vader- know of any other places that login apps are kept? I can't seem to find where two phantom programs are launching at login - I checked .profile, and the startup applications dialog, but they are no where to be found. I've browsed through many of the hidden folders in ~/, but no dice. Any ideas?

---

### Post by wojox on 2009-07-18
Check System > Preferences > Sessions
What are the apps?

---

### Post by lukeiamyourfather on 2009-07-18
Also check the /etc/rc.local and the other /etc/rc.d/* files. Cheers!

---

### Post by MaddMatt on 2009-07-19
rc.local is blank, and rc*.d are non applicable since this A. this only happens on my profile, and B. when I upgraded I overwrote the / directory, just kept /home. 

I do not have a system > preferences > sessions menu. Am I supposed to in Jaunty? Thanks for the tips!

---

### Post by 3rdalbum on 2009-07-19
> **MaddMatt said:**
> rc.local is blank, and rc*.d are non applicable since this A. this only happens on my profile, and B. when I upgraded I overwrote the / directory, just kept /home. 

I do not have a system > preferences > sessions menu. Am I supposed to in Jaunty? Thanks for the tips!

In Jaunty it is now Startup Applications.

You use Startup Applications for graphical programs that you want to run when you log in; and use rc.local (it should not be blank) for terminal programs that you want to run when the computer itself starts.

---

### Post by MaddMatt on 2009-07-19
Well both of the offending programs were disabled and removed from Startup applications a while ago and the problem persists. Does anyone know where exactly startup applications puts the links / commands in the home directory? Maybe they weren't *actually* removed...

---

### Post by MaddMatt on 2009-07-22
I solved the problem. 

After much searching, I found old sessions from pre-Jaunty which apparently were triggering xpad and others to start at login, despite the fact that "save sessions" was disabled. 

I just removed the saved sessions I found here:
~/.config/gnome-session/saved-session

Hope this helps someone

---

