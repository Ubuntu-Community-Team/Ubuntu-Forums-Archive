---
title: "iBUS des not start automatically"
date: 2009-11-05
forum: General Help
---

### Post by Martin_sensei on 2009-11-05
Hello,

I use iBUS to switch keyboard IMEs (particullary English and Japanese).  I installed Ubuntu 9.10 and when logging in to my user account iBUS starts automatically (keyboard icon appears in the tray)

However, when any other users log on, they do not get the keyboard icon, and have to start the iBUS deamon manually.

Does anyone know how to configure iBUS to start automatically for all users?

Any help would be great!

Cheers

---

### Post by wildweathel on 2009-11-05
All users?  I don't know.  One user?  Preferences -> Administration -> Language Preferences.  Set the IME box to IBus and it will automatically start on login.

---

### Post by Frantic_Earthling on 2009-11-05
Here is your solution:

(from Davescafe [http://ubuntuforums.org/showthread.php?p=8216422#post8216422](http://ubuntuforums.org/showthread.php?p=8216422#post8216422))

PROBLEM: IBus doesn't start automatically when I restart my computer
Here is how I solved the problem:
Go to the menu:
System >> Preferences >> Startup Applications
Click the button: Add
Name: IBus daemon
Command: /usr/bin/ibus-daemon -d
Comment: start IBus daemon when Gnome starts

---

### Post by Martin_sensei on 2009-11-05
Both solutions work!

Thanks!!

---

### Post by vodanhthi on 2009-12-17
> **Frantic_Earthling said:**
> Here is your solution:

(from Davescafe [http://ubuntuforums.org/showthread.php?p=8216422#post8216422](http://ubuntuforums.org/showthread.php?p=8216422#post8216422))

PROBLEM: IBus doesn't start automatically when I restart my computer
Here is how I solved the problem:
Go to the menu:
System >> Preferences >> Startup Applications
Click the button: Add
Name: IBus daemon
Command: /usr/bin/ibus-daemon -d
Comment: start IBus daemon when Gnome starts

Good solution! Thanks.

---

### Post by cmcqueen1975 on 2009-12-19
On Karmic, make that:

System->Administration->Language Support

Then set "Keyboard Input Method System" to ibus.

---

### Post by DomesDKG on 2010-01-13
thanks! works great

---

### Post by k66473 on 2011-08-14
just using your solution.
thank and best regards

---

### Post by binukavumkal on 2012-07-25
Worked for me too:)

---

