---
title: "Few questions (resolution, logging in as root, command line)"
date: 2006-03-09
forum: General Help
---

### Post by j-dawg on 2006-03-09
Total newbie, just to give some perspective.
 
Okay, so I'm having some problems installing video drivers. It's an old computer and not suited to playing games at all, so I'm not too worried about that. What I'm bothered by is that my maximum resolution for some reason is 1024x768, and since I'm used to using two monitors at 1280x1024 each, I like a lot of desk space. Although the Ubuntu machine only has one screen, I still want to be able to run it at that size, or at least something thereabouts. So if there's some alternative to installing new drivers that will allow me to run at higher resolutions, it would be nice to know that. I know it can do it, because a long time ago I installed 4.10 and I was able to run up to 1600x1200.
 
Nonetheless, the problem stands, and it would also be good to figure out how to deal with it. I can't seem to run stuff as root using the program under the Applications menu. In fact, I can't seem to access root in GNOME at all. The only way to log in as root that I can find is to use the terminal (if I try at the login screen it tells me that root may not log in using the login screen), and then I don't know what to do because I don't know the file name of the drivers. So that's not an option, and even if it were I don't want to deal with that every time.
 
I know I have the password right becuase I set it using recovery mode, and I can log in using the terminal. So that's not the problem.
 
 
Also, I noticed that mice never seem to work (this also happened with Fedora Core) through my KVM switch in Linux, although they work just fine in Windows on the same PC. Is there any way around this, or will I need to keep using two mice?
 
And I don't want to kill GNOME every time I want to access a command line, and iI notice that the terminal program thingy is gone. How do I make a little terminal window inside my GNOME?
 
Summary of this post:
1. Is there any way to let me raise the resolution to 1280x1024?
2. I'm not able to install anything because I can't seem to log in as root. Whaddoido?
3. Are KVM switches a problem? K and V are working just fine, it's the M that's a problem.

---

### Post by Sutekh on 2006-03-09
[QUOTE=j-dawg]
1. Is there any way to let me raise the resolution to 1280x1024?[/quote]```
sudo dpkg-reconfigure xserver-xorg
```

You should be able to choose the resolution that you want X to run at.

Note there may be another way too.

[quote=j-dawg]
2. I'm not able to install anything because I can't seem to log in as root. Whaddoido?[/quote]
Use **sudo**.  It gives you the power of root temporarily.  Use sudo (and your user password) before any command that requires root privileges to do.

Such as editing a system file
```
sudo gedit /etc/apt/sources.list
```

The Ubuntu Wiki has a lot of information about why Ubuntu uses sudo rather than allowing root to be enabled.

[Ubuntu Wiki - RootSudo](wiki.ubuntu/RootSudo)
[quote=j-dawg]
3. Are KVM switches a problem? K and V are working just fine, it's the M that's a problem.[/QUOTE]
There are lots of people with KVM working, but I have had no experience using them with Ubuntu yet.

---

