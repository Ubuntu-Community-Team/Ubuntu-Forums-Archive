---
title: "Many Insane 9.10 Issues. Need Help."
date: 2010-02-21
forum: General Help
---

### Post by LiteDrive on 2010-02-21
It's 4:00am, and I've been having a HUGE runaround of issues going on lately - more so than I can remember. 

First off, I'm new to Linux. I know a little, but hardly anything really. I've been having problems with Compiz and Emerald every time I restart, basically to the point now to where they don't even work. 

Anytime I punch ```
emerald --replace
``` in the terminal to activate the theme, it stays dormant. This makes it so that I can't close the terminal if I want to do something else with it; I can't continue writing commands in the same tab.

On top of that, I installed an Azenis theme .deb package, and I haven't been able to figure out how to uninstall everything it came with. Because it appears to be permanent, I can't even change it so I'm basically stuck.

Other issues are apparent, as not being able to mount my WD Passport (500gb) external drive which I had no problem with before. This time my PC doesn't even acknowledge the fact that it's there. However, I had used it for Windows (to no avail) a few days back before I tried it again with Linux. 

To solve an iPod showing up with Banshee issue, I was told to type ```
killall -9 nautilus
``` as part of the process, or something along those lines. I hardly know what the true meaning of nautilus is, except for that it has a huge deal to do with root and window management. 

Ever since then I started having mass issues with this thing, however the Azenis problem popped up long before that. It's gotten so bad that I can't even load my most recent boot via GRUB anymore (the Azenis splash screen freezes on startup); I've had to revert to a day back. I don't understand how this works though, as Azenis is still running on my screen, albeit in a more stable version. I also deleted a bunch of Azenis files in my /usr/share/themes/ directory - it didn't do a damn thing. In fact, the theme stayed on my desktop without the ability to be changed!

This is insanely frustrating. I'd like to just do a clean install, but I have way too many important things on my hard disk that I can't just do away with. 

Please, any help here would be great. I honestly haven't had problems like this with Linux for a while; last time was months ago - when I had 64 bit. I'm on 32 bit Karmic now, but even then I'm having trouble. I'd try different, such as Jaunty or something, but I know that those are meant for more advanced users.

---

### Post by mikewhatever on 2010-02-21
> **LiteDrive said:**
> 
....

This is insanely frustrating. I'd like to just do a clean install, but I have way too many important things on my hard disk that I can't just do away with. 
......

If I was you, I'd go to sleep right now and deal with it after having a good rest. Reinstalling would be the easiest, and you can copy all important files from the live cd before reinstalling.

---

### Post by SecretCode on 2010-02-21
> **LiteDrive said:**
> It's 4:00am, and I've been having a HUGE runaround of issues going on lately - more so than I can remember. 
One at a time... :)

> **LiteDrive said:**
> Anytime I punch ```
emerald --replace
``` in the terminal to activate the theme, it stays dormant. This makes it so that I can't close the terminal if I want to do something else with it; I can't continue writing commands in the same tab.
You could type 
```
emerald --replace &
```
to return the command line in the terminal window immediately. Or better, press Alt-F2 and enter 
```
emerald --replace
```
in the 'Run application' window. (This is better because emerald will not then be a child process of your terminal window.)


I am not sure about the theme issue.

> **LiteDrive said:**
> Other issues are apparent, as not being able to mount my WD Passport (500gb) external drive which I had no problem with before. This time my PC doesn't even acknowledge the fact that it's there. However, I had used it for Windows (to no avail) a few days back before I tried it again with Linux.This might require some investigation. Can I suggest you open a new thread to focus on this specific issue?

> **LiteDrive said:**
> To solve an iPod showing up with Banshee issue, I was told to type ```
killall -9 nautilus
``` as part of the process, or something along those lines. I hardly know what the true meaning of nautilus is, except for that it has a huge deal to do with root and window management. 
Nautilus is the file manager - like Explorer in Windows.

---

