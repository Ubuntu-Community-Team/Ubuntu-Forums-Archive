---
title: "Appearence window pops up at startup"
date: 2011-02-04
forum: General Help
---

### Post by EpicTone on 2011-02-04
Hello.
 
I am fairly used to Ubuntu, and i decided to try and change my login background (10.10) using the code:
 
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/loginwindow,
 
and:
 
sudo unlink /usr/share/gdm/autostart/loginwindow/gdm-simple-greeter.desktop
 
i later relised what i did and i tried to unlink the gnome-appearance-properties.desktop but no luck.
 
is there any way to stop the appearance properties from popping up at login, and to reinstall the gdm-simple-greeter.desktop ????
 
nothing has worked so far. :(
 
Thank you

---

### Post by Frogs Hair on 2011-02-04
I used a similar method to change my greeter , give this a try.```
   sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

```

---

### Post by EpicTone on 2011-02-04
hmmm no luck. it says 'cannot unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop': not a directory.

---

### Post by Frogs Hair on 2011-02-04
Sorry , your method must be different.

---

### Post by EpicTone on 2011-02-04
I solved it!!
i used terminal to check if appearance was present in the /usr/share/gdm/autostart/loginwindow,
then i opened nautilus with root (gksudo nautilus) and i navigated to /usr/share/gdm/autostart/LoginWindow/ and simply deleted "appearance" .

---

### Post by Frogs Hair on 2011-02-04
Good Job ! Welcome to the forums !

---

### Post by EpicTone on 2011-02-04
Thank you!

---

