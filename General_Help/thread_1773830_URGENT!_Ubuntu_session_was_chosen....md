---
title: "URGENT! Ubuntu session was chosen..."
date: 2011-06-02
forum: General Help
---

### Post by pingu1 on 2011-06-02
Hi !
I need help. My Ubuntu-laptop was functioning perfect with Ubuntu 11.04, in the "Ubuntu classic gnome" setup. I logged out and chose "Ubuntu" (which is with unity?) and now there are NO MENUS, the only thing showing is my background and a folder I have had on it. My mouse works fine, likewise the keyboard, but I have no menus og buttons... 

How do I switch back to Ubuntu classic gnome?? Restarting only logs me back in with "Ubuntu"-session and not the "Ubuntu classic"-session...

---

### Post by jamesisin on 2011-06-02
If you know the name of the application which controls the switching, you can enter that name with an ALT-f2 dialog.

---

### Post by snowpine on 2011-06-02
To get a menu, try moving the mouse to the left side of the screen, and/or tapping the "Windows" key.

To get back to Classic Gnome, select it from the menu at the bottom of the Login screen.

---

### Post by jamesisin on 2011-06-02
If snowpine's suggestion doesn't help, you can run a terminal by using the method mentioned above:

```
/usr/bin/gnome-terminal
```

If you know the name but not the location of the application try this in a terminal:

```
which name-of-application
```

And if you just want to poke around you can try this as above:

```
/usr/bin/
```

---

### Post by pingu1 on 2011-06-02
I am unable to get any menus at all... ALT+F2 does nothing. Alt+Ctrl+F3 gives me the terminal, but I don't know how to fix the problem. I have tried the Alt+Ctrl+L and then chosen Switch user to try to switch back to Ubuntu Classic, but when I log in again nothings changed....

I have access to only the folder that I put on my desktop (which gives me nautilus) and all other files, but I can't use any menus or applications. I am also unable to log out normally.

Is there any Alt+Ctrl-option to log out normally?

---

### Post by pingu1 on 2011-06-02
nudge... please help.... desperate :)

---

### Post by pingu1 on 2011-06-02
I was hoping I wouldn't have to reinstall anything and  loose all my data...
crap :(

---

### Post by hawthornso23 on 2011-06-02
The quickest way out is to pull the plug (turn it off). When you turn it back on it should reboot to the login screen. Pick the ubuntu classic desktop this time. 

Your unity is broken. Before you try it again enter

```
unity --repair
```

in a terminal to fix it.

Good luck

---

### Post by pingu1 on 2011-06-02
Thank you for your replies. 
Again - if I reboot, I do not get the login-screen... I automatically log in, and get no menus. The only way I can get the login screen (as far as I know) is through locking the screen and choosing Switch user...

I have not tried the command mentioned above this post, so thanks, I'll try.
:) Hope it solves it... if not - I will reinstall... but this time 10.10....

---

### Post by pingu1 on 2011-06-02
> **hawthornso23 said:**
> The quickest way out is to pull the plug (turn it off). When you turn it back on it should reboot to the login screen. Pick the ubuntu classic desktop this time. 

Your unity is broken. Before you try it again enter

```
unity --repair
```

in a terminal to fix it.

Good luck


Thank you, thank you, hawthornso23 !!!!!!!!!
unity --repair worked !!!!!!

I had already started making backups of what I could... thinking I needed to re-install, but now I don't have to... you stopped me in the final stage....

THANK YOU, WHOEVER YOU ARE!
My hat off for you....

UBUNTU RULES!

---

