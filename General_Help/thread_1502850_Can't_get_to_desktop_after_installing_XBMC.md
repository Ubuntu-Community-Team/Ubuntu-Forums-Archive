---
title: "Can't get to desktop after installing XBMC"
date: 2010-06-06
forum: General Help
---

### Post by cloudone on 2010-06-06
after I boot the system, it would get to XBMC automatically, and when I tried to exit XBMC, it returns to login screen with two choices for Sessions, XBMC and xterm. xterm just gets me a terminal.

So I tried to remove xbmc by using command line.

Now, whenever I start the system, it takes me to the login screen, and after entering my credentials, the screen will go black for 1 or 2 seconds, then return to the login screen again, in an infinite loops.

How do I get my Gnome desktop back?

I'm using Ubuntu 10.04 64 bit

---

### Post by gerowen on 2010-06-06
I'm guessing XBMC is a desktop environment?  First thing hits my mind is XBox Media Center, but I don't see how that would affect your Gnome desktop environment.  Either way, try dropping into a terminal (at boot you can go to failsafe mode and enter a root terminal) and in your home folder delete the .gnome and .gnome2 related folders.  Depending on "what" XBMC you're talking about there may be a folder there for that as well (a hidden .xbmc or something like that is what you're looking for), if there is delete that, then reboot and try to get into Gnome.  Basically what this does is delete all your custom configs for Gnome so it forces Ubuntu to reload a default UI for you.  Your /home folder will be fine, you'll just have to redo your UI customizations.

---

### Post by cloudone on 2010-06-06
> **marcusdean.adams said:**
> I'm guessing XBMC is a desktop environment?  First thing hits my mind is XBox Media Center, but I don't see how that would affect your Gnome desktop environment.  Either way, try dropping into a terminal (at boot you can go to failsafe mode and enter a root terminal) and in your home folder delete the .gnome and .gnome2 related folders.  Depending on "what" XBMC you're talking about there may be a folder there for that as well (a hidden .xbmc or something like that is what you're looking for), if there is delete that, then reboot and try to get into Gnome.  Basically what this does is delete all your custom configs for Gnome so it forces Ubuntu to reload a default UI for you.  Your /home folder will be fine, you'll just have to redo your UI customizations.
I was talking about this [http://xbmc.org/](http://xbmc.org/)

I'll try those, and post results in a minute.

---

### Post by cloudone on 2010-06-06
Deleted those folders, but same thing. Can't get past the login screen.

Is there any way that I can restore my desktop environment?

I tried to sudo apt-get install gdm

but it just told me that the currently installed version is the newest version.

---

### Post by wojox on 2010-06-06
You would need:

```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```


Did you add anything to start up applications to get it to boot directly into XMBC?

---

### Post by cloudone on 2010-06-06
> **wojox said:**
> You would need:

```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```


Did you add anything to start up applications to get it to boot directly into XMBC?
nothing. I just installed xbmc and it went crazy.

---

### Post by wojox on 2010-06-06
> **cloudone said:**
> nothing. I just installed xbmc and it went crazy.

Went crazy. Well that explains it. I've used that app before and not had any troubles, knock on wood.

How much stuff do you have on there? It may be easier and faster to reinstall Ubuntu for you if that's an option. :)

---

### Post by cloudone on 2010-06-06
> **wojox said:**
> You would need:

```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```


Did you add anything to start up applications to get it to boot directly into XMBC?
thanks a lot.:popcorn::KS that worked.

---

