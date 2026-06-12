---
title: "Unity is gone"
date: 2011-08-25
forum: General Help
---

### Post by KatieMetzger on 2011-08-25
Hello, I am running Ubuntu 11.04. Recently, I attempting to change some basic settings for compiz. I don't remember exactly what I changed. When things started going wrong, I tried to put everything back the way it was. After restarting and logging in, no desktop environment shows up. It shows my desktop background, but nothing else. No unity hot keys run and the computer is otherwise unresponsive. I can run other virtual consoles but nothing I've tried there has made any effect. I would really appreciate it if someone could help me make my computer usable again. Thank you.

---

### Post by roman5x3 on 2011-08-26
I am in a similar boat. I just got my opengl working and installed unity desktop on top of my kubuntu system. I get nothing but what you described as well as a couple of icons on my desktop. I will say that my ubuntu one accounts prompts for login and my wifi logs in automatically. So the desktop core script is working up until the point of the initialization of unity.

I am going to continue to do research and see what I can come up with.

Roman

---

### Post by christopher.wortman on 2011-08-26
Kubuntu +1

Seriously it is amazing, give it a go.

---

### Post by IWantFroyo on 2011-08-26
Using CompizConfig with Unity is a really bad idea.
Last time I tried it, I ended up with a Unity in my Ubuntu Classic, not being able to log into the normal Ubuntu session.

I never figured out a fix. You may have to reinstall.

---

### Post by christopher.wortman on 2011-08-26
> **IWantFroyo said:**
> Using CompizConfig with Unity is a really bad idea.
Last time I tried it, I ended up with a Unity in my Ubuntu Classic, not being able to log into the normal Ubuntu session.

I never figured out a fix. You may have to reinstall.

Hit alt+f2 type: terminal then hit enter
then type the following
sudo apt-get purge Unity
sudo apt-get install Unity

Should fix it. If it does not and you are forced to reinstall, seriously try Kubuntu, it is worlds better...

---

### Post by IWantFroyo on 2011-08-26
> **christopher.wortman said:**
> Hit alt+f2 type: terminal then hit enter
then type the following
sudo apt-get purge Unity
sudo apt-get install Unity

Should fix it. If it does not and you are forced to reinstall, seriously try Kubuntu, it is worlds better...

KDE's okay, but if you want solid panels, just use the Ubuntu Classic login and delete Unity like christopher.wortman said.

I personally prefer Gnome2 to KDE, simply for performance and battery reasons. And, KDE just has too much transparency for me.//opinion

---

### Post by IWantFroyo on 2011-08-26
Edit- Double post. I knew I shouldn't have switched to Chrome... FF doesn't do this!

---

### Post by KatieMetzger on 2011-08-26
Thank you for your replies, everyone.

I tried the things recommended but the problem continues.

I don't have icons on my desktop but I didn't originally. I can, however, right click and create things on the desktop as well as open Appearance Preferences. The window borders and title bars appear to be working for that application.

It seems to be that the only things missing are the unity sidebar, the top panel, and my hotkeys.

I am trying to avoid re-installing the entire OS since I really want to actually know how to solve the problem. It just seems like the easy way out.

I would definitely appreciate any more help with this problem. Google is being very unyielding (not very Google-like).

---

### Post by raja.genupula on 2011-08-26
open your terminal & type 

```
ccsm
```

in the menu look for ubuntu unity , check  is ubuntu-unity  enabled or not . if not enable it . i am sure its gonna help you 


.

---

### Post by KatieMetzger on 2011-08-26
Alright, I went into classic mode and opened the terminal and typed it. It opened up the configuration. I selected the Ubuntu Unity Plugin, which was the only option that resembled "Ubuntu Unity." I logged out and back in with the typical Ubuntu interface selected. I thank you for trying to help, but it didn't make any effect. Everything is still broken.


EDIT:
Still following your suggestion, I went back into CCSM and I deselected everything and then selected the Unity plugin and other things that I figured wouldn't mess things up and that I vaguely remember being set. It works now. Thank you for telling me how to solve my big mistake. I appreciate it very much. Thank you to everyone else who tried to help as well. And sorry I posted this in general help, I just now realized that there is a desktop environment section.

---

