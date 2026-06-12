---
title: "urgent! Lost all panel access! (Gnome)"
date: 2009-10-27
forum: General Help
---

### Post by karimruan on 2009-10-27
Okay, I used the command

apt-get install ubuntu-netbook-remix

then I didn't like it, so I used apt-get remove ubuntu-netbook-remix, and now I lost my panels. I right click on where the panel was, and get no option to add a panel.

What do I do? I cant access anything without the command line, I tried using sudo apt-get install kde, and when that was configured, it did the same thing as gnome, no kde menu bar, just a desktop with icons. Anyone else have this problem?

I am running an hp dv6700 series laptop
Ubuntu 9.04 Gnome


Everything worked fine prior to installing ubuntu-netbook-remix.

---

### Post by XDevHald on 2009-10-27
You do have access to a terminal just log out and choose your login session as Xterm and it will give you a chance to reinstall the gnome-panel by ```
sudo apt-get autoremove gnome-panel && apt-get install gnome-panel
```

Hope this helps.

---

### Post by karimruan on 2009-10-27
Okay, I tried to apt-get autoremove gnome-panel and apt-get install gnome-panel. Didn't work. I get no panels in any Desktop environment, so I uninstalled KDE, and it boots straight into gnome, but panel-less. I tried to reinstall ubuntu-netbook-remix so I at least have easier access to a terminal, but it wont work, still boot right into gnome, without panels. I can access a terminal from within gnome, I have to wait till gnome boots and then press control-alt-f1 to get to a console. 

Is there any hope without reinstalling?

EDIT: Even though I am in gnome, I still have the feel of the netbook remix window manager, no close, minimize, or maximize buttons on the top panel of a window, I have to go to file> quit to exit an app. Weird, I think I am using some messed up hybrid of the two DE's!

---

### Post by XDevHald on 2009-10-27
Here's a useful resource: [http://www.ubuntugeek.com/ubuntu-tip-howto-recover-gnome-panel.html](http://www.ubuntugeek.com/ubuntu-tip-howto-recover-gnome-panel.html)

P.S remember to use the Xterm login session :-)

---

### Post by karimruan on 2009-10-28
Okay, I tried rm -rf .gnome2 .gconf .gconfd in xterm and switched to gui login (ctrl+alt+f7) and nothing. Even rebooted. The how to suggested doing this from login window though, I have none. To make using Linux easier on my wife I decided to bypass a login screen and boot directly into ubuntu. I know, I know, bad idea, not secure, but ubuntu IS linux, and I really don't have too much to worry about with unwanted users.

Anyway, I really want to avoid a new install. Not with ubuntu anyways. If we can't get this fixed I might try something else, ubuntu based, easy for my family. 

Listen to me, giving up already. I stayed up for four hours playing in the terminal, nothing. No more ideas. You have more I hope!:D

UPDATE:

Did some searching in the forums (yes, I am doing my part too :) and tried this with no luck:

1. login gnome
2. ctrl-alt-f2
3. sudo apt-get remove gnome-panel
4. sudo apt-get install gnome-panel
5. sudo apt-get install ubuntu-desktop

Kinda knew it wasn't going to work, but I am desperate! Anyway, just wanted to share what wasn't working so for!

---

### Post by P4man on 2009-10-28
press alt+f2 (or in a terminal) run
```
gnome-panel
```

Does that start them?

Another thing to try is starting

```
gconf-editor
```

browse to app > panel. The main panels ought to be in toplevels Check their settings
.

---

### Post by karimruan on 2009-10-28
Is there a way to open terminal besides with alt-f2, i lost that functionality. I saw a post in the forums somewhere where the person was in the same situation as me, I just have to find it again, I saw it like 10 minutes ago but I started trying things on my own. Should have bookmarked it.

My lastest try was (all of my commands are done by alt-f2) what you said to do, but without using a terminal in gnome, I get Cannot Open Display.

Is there a way to access the terminal in gnome beside f2 or Applications>Accessories>Terminal?

---

### Post by P4man on 2009-10-28
try control alt F1

To go back to the gui control alt F7

edit; that wont work for gconf-editor...

---

### Post by P4man on 2009-10-28
I think this is your problem (and solution):
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

Short version:

```
gconftool-2 --recursive-unset /apps/panel
```

reboot. Then update your system so it wont happen again.

---

### Post by karimruan on 2009-10-28
Nope, sorry, still didn't work. I am going to install pclinux os and install gnome (i have a kde version) and then dual boot with a fresh install of ubuntu jaunty. That way I finally get my full linux dual boot and and working gnome configuration.

---

### Post by karimruan on 2009-10-28
Reinstalled Jaunty. Works fine. Just gotta get my mic working now! But that is another story... Thanks for all the help guys!

---

