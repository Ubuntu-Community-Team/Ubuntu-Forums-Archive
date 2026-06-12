---
title: "Just installed 10.10 but I have no panels :/"
date: 2010-11-17
forum: General Help
---

### Post by timr92 on 2010-11-17
Hey guys and thanks in advance for any help provided. I just performed a clean install of Ubuntu 10.10, and all goes well until I log in to find no panels; just a mouse pointer and the pretty wallpaper :/ can't right click on anything or do anything, all I can do is entertain my cat with the cursor :( Wouldn't mind being a little more productive with my computer, any help is greatly appreciated thanks guys :)

---

### Post by plucky on 2010-11-17
> **timr92 said:**
> Hey guys and thanks in advance for any help provided. I just performed a clean install of Ubuntu 10.10, and all goes well until I log in to find no panels; just a mouse pointer and the pretty wallpaper :/ can't right click on anything or do anything, all I can do is entertain my cat with the cursor :( Wouldn't mind being a little more productive with my computer, any help is greatly appreciated thanks guys :)

On your keyboard,type **ALT+F2** and a window should open,so type in ```
gnome-panel &
``` and see if that brings back the panels.


Good luck

---

### Post by timr92 on 2010-11-17
> **plucky said:**
> On your keyboard,type **ALT+F2** and a window should open,so type in ```
gnome-panel &
``` and see if that brings back the panels.


Good luck

No window opens when I do **ALT+F2** :(

---

### Post by wojox on 2010-11-17
Open a terminal and try these three commands

```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```

You may have to log out and back in.

---

### Post by timr92 on 2010-11-17
> **wojox said:**
> Open a terminal and try these three commands

```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```

You may have to log out and back in.

How do I open a terminal with no menus and no ALT+F2 :/

---

### Post by Crazedpsyc on 2010-11-17
Try Ctrl+Alt+F6 to get a virtual console (like a terminal except you log in) and run from there ```
sudo apt-get install gnome-panel
``` and see what it gives you. If it installs the panel you should be good, if it says it is already installed, bad, if it says it can't install, worse. 
An idea to inspire others here: what about making sure the right configuration keys are set in the configuration editor? I don't know how to access the keys from the command line. but it sounds like maybe some vital bits of gnome failed to install.
If this doesn't work try rebooting if you haven't already and then install something like avant-window-navigator or docky instead if it still isn't there.

EDIT: Oh, thats how you do it. thanks wojox
Try what he said from the console first :)

---

### Post by timr92 on 2010-11-17
> **Crazedpsyc said:**
> Try Ctrl+Alt+F6 to get a virtual console (like a terminal except you log in) and run from there ```
sudo apt-get install gnome-panel
``` and see what it gives you. If it installs the panel you should be good, if it says it is already installed, bad, if it says it can't install, worse. 
An idea to inspire others here: what about making sure the right configuration keys are set in the configuration editor? I don't know how to access the keys from the command line. but it sounds like maybe some vital bits of gnome failed to install.
If this doesn't work try rebooting if you haven't already and then install something like avant-window-navigator or docky instead if it still isn't there.

EDIT: Oh, thats how you do it. thanks wojox
Try what he said from the console first :)

Tried what wojox said using Ctrl+Alt+F6 without success :/ ```
sudo apt-get install gnome-panel
``` says it's already the newest version *sigh*

---

### Post by io5cml4z on 2010-11-17
Try:
> sudo rm -rf ~/.gnome2
That should reset gnome. Try restarting after that. :)

---

### Post by Crazedpsyc on 2010-11-17
Hmm.
What do you think about reinstalling ubuntu? it sounds like more of gnome is missing than you can replace with a dockbar...

---

### Post by Crazedpsyc on 2010-11-17
you may also want to do this
> 
**rm -rf .gnome .gnome2 .gconf .gconfd**(recommended by wordpress.com)

Best Of Luck! There's always the possibility that your copy of the ubuntu iso/disk is corrupt, and you may have to get a new one

---

### Post by timr92 on 2010-11-17
> **Crazedpsyc said:**
> Hmm.
What do you think about reinstalling ubuntu? it sounds like more of gnome is missing than you can replace with a dockbar...

Already tried reinstalling ubuntu :( ```
sudo rm -rf ~/.gnome2
``` didn't work, nor did ```
rm -rf .gnome .gnome2 .gconf .gconfd
``` I checked the md5 sums of everything in md5sums.txt on my installation media and it's all good, and the md5 of the iso itself is fine too :(

---

### Post by gofrommicrosoft on 2010-11-19
Hi,

I have just found the same problem, installing 10.10 on a Dell Optiplex GX150 that worked fine with 9.10.

Running "Try Ubuntu" from the CD the desktop works fine. Actually install and everything seems fine untill the installed version fires up, I get the logon screen, enter password, then all I get on the monitor is the background graphic, no panels top or bottom, no real way to use the system. I've tried switching through the different screen resolutions and the only thing that changes is the mouse pointer size.

If it works from the CD, why does it not work when actually installed to the hard drive? Seems the "see if it works" is very misleading with this version.

I would appreciate ideas from anyone.

---

### Post by Crazedpsyc on 2010-11-20
Well, the LTS version (10.04) is usually better anyway...
Maybe consider switching back to 10.04. If you want you *could* try upgrading from 10.04, but I don't recommended that if you are having this much trouble. I wouldn't upgrade to 11.04 when it comes out either because with everything being new (unity, lightdm, etc.), I assume it will be rather unstable until at least 11.10.

--I hope this doesn't turn you off ubuntu; it is definitely the best distro ever for human beings!

---

