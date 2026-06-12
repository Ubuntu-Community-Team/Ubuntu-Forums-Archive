---
title: "Help! Headless 10.10 desktop with VNC?"
date: 2011-04-03
forum: General Help
---

### Post by davidfeldman on 2011-04-03
I bought a little Zotac nettop as a home file, print, and backup server and put Ubuntu 10.10 on it. It works great overall but I'm having a hell of a time getting it to work as a headless server with VNC.

I'm not afraid of command lines but let's face it, some things are easier with a GUI. What's more, lots of good things happen when Gnome starts up that aren't strictly part of its UI. In other words, I'd like to VNC into the server sometimes and interact with it via Ubuntu's lovely GUI.

That works great when it starts up connected to a monitor. Using vino or x11vnc I can VNC in and mouse around to my heart's content. But when I detach the monitor so I can stick the server in a closet, everything goes south. Gnome doesn't start, so VNC doesn't start.

I've tried vino, x11vnc, tightvnc, vnc4server. I've gone through countless HOWTOs and forum posts. A number got me partway there -- looking at a blank white screen, for instance. Or looking at a Gnome desktop where apps won't launch. Or apps will launch but randomly minimize when I type. Media don't mount properly, perhaps because I started Gnome as something other than root.

It feels like this shouldn't be that hard. I just want to tell Ubuntu, "I know you can't find a monitor. That's OK. Start Gnome anyway at 1280x800 as if you had one." But I don't see any way to do this and none of my hours of searching and messing around have gotten me any closer.

Help?

---

### Post by HermanAB on 2011-04-04
Howdy,

It is very easy to run a headless server, if you use SSH.  VNC is mostly a Windows thing.  It can work, but as with most things Windows, it is more difficult and insecure.

If you installed the Ubuntu Server edition, then the SSH daemon is already running, so from an Ubuntu desktop do:
$ ssh -X -C -c blowfish user@serveripaddress "gedit /etc/fstab"

or
$ ssh -X -C -c blowfish user@serveripaddress "gnome-panel"
and go click happy.

It also works from Windows, if you install Cygwin.

---

### Post by davidfeldman on 2011-04-04
Thanks for the reply! At first glance that seems to work, but unfortunately doesn't quite do the trick. (I should note that the client here is a Mac OS X machine rather than another Linux one.) 

First, I'm getting a bunch of errors and warnings:

```
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Xlib:  extension "RANDR" missing on display "localhost:10.0".
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

```

I then get others in the console as I mouse around. More importantly I'm having some of the same issues I had with VNC, presumably because I'm launching Gnome as a regular user:
[LIST]
[*]External drives aren't mounting properly, and attempts to mount them in Ubuntu Disk Utility fail with permissions errors.
[*]Nautilus is complaining about certain types of file paths, like "computer".
[*]Less important but still annoying: the UI is a whole lot less polished. Ubuntu's gone to a lot of trouble to create a nice-looking experience and it's a shame to lose it.
[/LIST]

I'm sure most or all of these problems have solutions of their own...but I'm also sure more problems will crop up. One of the great things about Ubuntu vs. a lot of distros is it comes a lot closer to just working, which means a lot less time spent fiddling around to get it functioning properly. Booting up normally (with monitor attached) and then using VNC preserves that experience, while it seems like every other technique I've tried puts me back into combing the Web for solutions. I'd just like to ditch the monitor.

---

### Post by KingBobo on 2011-04-05
I'll be following this thread closely as I too have just bought a ZBOX and am attempting the same thing. With Gnome installed, I've so far got both vncserver and NX (Free edition) running fine, and this works great for remote access. BTW, I highly recommend trying NX -- quite a lot faster than VNC. From my own Googling, it certainly appears that Gnome won't start unless a monitor is detected. One simple trick which I am planning to try next is to attach a dummy load onto my video adapter. A few resistors inserted into the ZOTAC's included DVI-to-VGA adapter are supposedly all that is required to fool the system into completing Gnome startup. There are instructions online for accomplishing this (Google vga dvi dummy plug).

You'll no doubt encounter other threads in which the above 'solution' is heavily disparaged, that running a local GUI poses an  unnecessary resource burden, doesn't meet the definition of headless operation, etc. However, I am a Linux newbie and really appreciate the familiarity of the Gnome desktop and access to the various GUI tools. True, it's a crutch but I'm happy to have it.

When you tried Herman's suggestion, had you in fact disabled GDM? I'm trying to understand the issues that you reported (especially drives not mounted). It doesn't seem logical that an  essential function would be tied to whether or not the GUI was running. 

Anyway, I first plan to try the dummy plug cheat since it looks so simple. My specific purpose for the ZBOX is to run SqueezeBox Server and XBMC. SB configuration is via a Web-based interface, so no GUI needed at all. I still need to read up on XBMC, but I think that most of the common XBMC settings are accessible via HDMI out. So, I'll most likely try reconfiguring Ubuntu for true headless operation after getting myself a little more educated.

BTW, if anyone has positive recommendations for an alternative to XBMC, please chime in. I haven't really looked at other options and would appreciate any suggestions. MythTV perhaps?

-rob

---

### Post by davidfeldman on 2011-04-16
I haven't tried disabling GDM. But here's the thing: I don't really want to. (I know this is turning into a rant; bear with me.) The reason I chose Ubuntu vs. any other distro is how well it works out of the box. Gnome seems to be pretty central to that. I'm sure that I could disable it and make everything work but I'm also sure that would require hours and hours of looking through forums and editing config files.

I feel like there has to be a way to tell Ubuntu, "Ignore your current hardware configuration and just assume you have a standard 1280x800 display." Then everything continues to work out of the box with no additional fiddling required, and I can spend my time on things I actually _want_ to run differently. Any thoughts?

---

### Post by winchendonsprings on 2011-04-19
I'm interested in the answer to this too. 

I will be running a similar setup(headless) in two weeks. It will be crucial that it works properly.

---

### Post by ucy74 on 2011-04-25
I have similar expereince with Atom/ION based nettop without any display.
My installation of the vnc server was based on starting services shown in web tutorials.
Finally rcconf help me launch service for vncserver.

First, some applications cannot start in VNC client mode. I was not found solution for that.
For example I cannot set solid color for desktop background - color picker dissapearing quickly. Same thing is with installed Filezilla - after clicking in any folder shown in application it falls down.

Funny shortcut: when You press "d" on keyboard it minimizes all windows. It is simple to change that in shortcut setup application - change "d" to other combination.

---

### Post by AllGamer on 2011-04-25
i came across this issue several months ago.

the solution that i found in another topic was simply to set the monitor & size to use VNC as the default "monitor" server

you add an entry into the **xorg.conf** to make it think it's a valid monitor. [http://ubuntuforums.org/showpost.php?p=9466830&postcount=14](http://ubuntuforums.org/showpost.php?p=9466830&postcount=14)

there are many more topics referencing the same solution, and alternative methods as well

but that's the one that worked for me, on one machine that was having exactly the same problem as the **[OP]** reported.

all other machines that I VNC into will work fine even without a monitor connected, but it defaults to 800x600 which is **ok** for most admin tasks

---

### Post by a904guy on 2011-06-12
I've found a solution to the 800x600 resolution issues. You can use the dummy driver in xorg to get a full list of supported resolutions to use in a headless VNC

[http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/]("http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/")

---

