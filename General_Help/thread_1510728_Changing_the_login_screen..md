---
title: "Changing the login screen."
date: 2010-06-15
forum: General Help
---

### Post by Mike808 on 2010-06-15
How do you change the login screen?  I was wondering and cannot find it.

The file name is "login.tar.bz2"

Do I have to extract it?  Install it?  How?

Side-Note - Sorry haha, I ask alot of questions.

---

### Post by jarmore on 2010-06-15
Menu ... System/Administration/Login Screen ... then click 'unlock'

---

### Post by cuberts on 2010-06-15
I was having the exact same problem. Easy solution, put this in your  terminal :

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

That will bring you to your typical background selection but don't be  alarmed, select the new login background and close it as normal and  enjoy your new login screen background :). 

If you want to add a custom picture to this you may add them just as you  would add your typical gnome backgrounds through the menu that opens  with the above command. If it rejects it, make sure you format and size  the picture like the others in the menu. You can do this with GIMP. Good  luck!

---

### Post by Mike808 on 2010-06-15
Well, I tried that but all it did was bring me to "Appearance Preferences".  Is that right...?

---

### Post by cap10Ibraim on 2010-06-15
Install Ubuntu Tweak a lot of easy customizations
[http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html](http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html)

---

