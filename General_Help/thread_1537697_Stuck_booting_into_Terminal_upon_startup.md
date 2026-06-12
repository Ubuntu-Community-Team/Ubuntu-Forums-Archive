---
title: "Stuck booting into Terminal upon startup"
date: 2010-07-23
forum: General Help
---

### Post by kristapus on 2010-07-23
I have a computer that normally boots into XBMC player in my living room for movies and what not. I tried to boot into the desktop to add some movies and i must have accidentally booted into the terminal. Well now i am stuck. It just boots into the terminal every time with no other menue options to stop it before. It just boots to a blue ubuntu screen with a terminal window in the top left corner. I included a picture. I just need to get back to the desktop. Please help. I am very new to ubuntu. Thank you for any help given.

---

### Post by Bertus_Nel on 2010-07-24
Take from [http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode](http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode) : Oh, there is some discussions on this topic in the forum....

{



I'm assuming you are getting to a login prompt.


 1. Login
2. sudo dpkg-reconfigure xserver-xorg
3. type your password
4. Follow the prompts....the defaults should get you up and running  
 }


Hope this does it for you..

---

### Post by kristapus on 2010-08-01
> **Bertus_Nel said:**
> Take from [http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode](http://www.ubuntux.org/cant-start-ubuntu-in-grphical-mode) : Oh, there is some discussions on this topic in the forum....

{



I'm assuming you are getting to a login prompt.


 1. Login
2. sudo dpkg-reconfigure xserver-xorg
3. type your password
4. Follow the prompts....the defaults should get you up and running  
 }


Hope this does it for you..
I never see a login screen, it goes right to that screen with the terminal on it, in picture on original post message.

---

### Post by jerenept on 2010-08-01
You can just enter that into the terminal you see there.

---

### Post by Smart Viking on 2010-08-01
What you see there is called xterm, so what you can basically do is this(i'm presuming u are using xubuntu because of the background):

```
xfce4-terminal
```that will open another terminal, then do this:

```
metacity
```after that, you press "ctrl+t" which will open another tab in the terminal, and there you enter this:

```
xfce4-panel
```and then you will basically have everything you need and can see of you can perform more from there, btw try the other guy's suggestion, that might work. And if it does not you could try mine(it should work, but it takes time since you must do it everytime you start up). :)

---

### Post by kristapus on 2010-08-01
Thanks guys, got it working. I have been stuck there for over a week. Thanks a bunch again. I truly appreciate it.
Kris

---

