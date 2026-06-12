---
title: "Problems with keyboard"
date: 2006-04-07
forum: General Help
---

### Post by njumen on 2006-04-07
Hi, I have a strange problem with keyboard. After login the key **p** dos not work. (It works properly in windows XP) When I tried to find out how to solve this, I changed the *Keyboard model* in Keyboard *preferences* to **acer travelmate 800**   because I have an Acer notebook (not Travelmate 800 but it's only Travelmate which was in selection) and I supposed it shall work. Then I checked the **p** and it worked. But how was I badly surprised when after next login the **p** didn't worked again!! Now only I know about this is that, the **p** start to work *anytime* I change *anything* in *keyboard preferences*, but it does not work right after login. Can anybody help me, please? :-|

---

### Post by trent dillman on 2006-04-07
Is it just in X, or in a console as well? Maybe it's trouble with your xorg?

---

### Post by vruum on 2006-04-07
it sounds like the settings are not being stored. change the keyboard settings, and next time you log out, make sure to tick the box that says something like "save settings for next login" if that doesn't work. you might have to change it in the systemwide xorg settings. but try the other thing first

---

### Post by njumen on 2006-04-07
it does only in Xwindow, in console the key works...
I don't think it has something to do with unsaved settings, because the key starts to work after i ***change* *anything*** and it doesn't deppend what or how is set. Anyway all settings in Gnome seems to save automaticaly...but nevermind.
So please could you tell me more about the *xorg* I have no idea what it is...thanks.

---

### Post by vruum on 2006-04-07
for this purpose, xorg is xwindows. It is configured in the textfile /etc/X11/xorg.conf, so to edit it you would type "sudo gedit /etc/X11/xorg.conf" and then look at the inputdevice section. but if any change makes the keyboard work then I'm not sure that it's a xorg problem. for a quick test, see if the P key works at the login screen, or if you log in to a different session (failsafe gnome for example)

---

