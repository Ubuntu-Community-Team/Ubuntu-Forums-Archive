---
title: "Getting rid of Ubuntu Studio splash screen"
date: 2010-04-19
forum: General Help
---

### Post by ProDigit on 2010-04-19
Hi,
I installed the beta version of Ubuntu 10.4, and on top of that Ubuntu Studio (for the programs it brings with it); but don't like the splash screen.

How do I disable it? (I tried uninstalling the Ubuntu studio desktop, but it did not remove the splash screen).

*Edit, following Ubuntu studio apps are still installed on my system:
```
ubuntustudio-default-settings  ubuntustudio-screensaver
ubuntustudio-icon-theme        ubuntustudio-sounds
ubuntustudio-look              ubuntustudio-theme
ubuntustudio-menu              ubuntustudio-wallpapers
```

---

### Post by ProDigit on 2010-04-21
bump!

---

### Post by ProDigit on 2010-04-22
bump 2

---

### Post by lucasta on 2010-04-27
if i remember correctly there's a usplash tool in the repositories somewhere. or search synaptic for the ubuntu studio usplash and remove it

---

### Post by Cherry Cotton on 2010-05-01
I think I have the same problem. And the thing is—and I suspect the situation is similar for ProDigit—I don’t even have Usplash installed, and haven’t for some time. I did have the “libusplash0” package installed, so I removed that, and just to be safe I purged residual config files for that package, the “usplash” package, and the packages for the Ubuntu and Ubuntu Studio Usplash themes (packages which were removed some time ago), and I reinstalled the “xsplash” and the Ubuntu Xsplash theme packages. So, according to the package manager, I do not have anything even remotely related to Usplash residing on my system (and “sudo xsplash” confirms that my current Xsplash theme is the default Ubuntu one), and yet, if I start up the computer, there’s the Ubuntu Studio Usplash theme in all its unwanted glory.

Does anyone have any ideas? This is annoying....

---

### Post by border on 2010-05-03
My splash screens are also ****ed up. At the moment I don't even see any.
I tried to manage them with startupmanager (might be the reason it got ****ed up) and gnome-splashscreen-manager. But those do not seem to be the right tools for that.
There is a package ubuntustudio-plymouth-theme (also a plymouth-theme-ubuntustudio) and that got me to the point that there is plymouth which seems to generate the splash screen at startup.

So I guess (x)splash is still hanging around from previous ubuntu version, but is superseded (or maybe even uses?) by plymouth.

Anyway
investigating further

---

### Post by border on 2010-05-03
Normally removing plymouth-theme-ubuntustudio should do the trick
But I don't really like the new ubuntu plymouth theme...

Wonder if there are others to install...

suggestions are welcome ;)

---

### Post by ProDigit on 2010-05-03
I also only had plymouth-theme-ubuntustudio installed which was not removed after the removal of Ubuntu Studio desktop.
I'll remove it now, and see what'll happen.

---

### Post by ProDigit on 2010-05-13
Nothing happened.
Still stuck with the splash screen...

---

### Post by Tivis on 2010-05-18
Hi everyone,
I had the same problem as well after installing some stuff to create-edit the linux themes. By chance, I installed something related to the Ubuntu Studio and I had a different splash screen which I didn't like.
I have removed all the Ubuntu Studio related voices from Ubuntu Software  Centre but it was not enough.
I searched for a file called "splash" with any image extension in linux but found none relevant to solve the issue.

I found another post somewhere, suggesting to execute these commands to resolve the issue:
- sudo update-alternatives --auto default.plymouth
- sudo update-initramfs -u
but unfortunately it was not yet solved.

Only when I opened Synaptic Package Manager and I marked as "remove completely" the package "plymouth-theme-ubuntustudio", the default 10.04 splash screen returned.
Hope this can help who still has the problem.

Cheers! :D

---

### Post by angry_johnnie on 2010-05-18
this

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

almost the same as the last post, except for one word :p

when the first command is executed, use numbers to choose the appropriate theme.

by the way, you could also run

```
aptitude search plymouth-theme
```

there's a couple of them you could install that are decent enough.

by the way, editing plymouth themes is not that hard.

just go to /lib/plymouth/themes and start changing stuff, like the background, logo, throbber, etc.

just keep in mind it won't support a lot of colors, so try to keep things simple.

---

