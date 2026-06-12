---
title: "Removed pulseaudio, &quot;volume control&quot; is gone."
date: 2009-11-02
forum: General Help
---

### Post by Kristofer Gustafsson on 2009-11-02
As i do normally i removed pulseaudio because it.. Just does not work well for me. Sadly my volume control at the top of the screen is gone. Anyone kno how to get it back? :p .. Kinda need it..

---

### Post by The Funkbomb on 2009-11-02
Right click on the top menu.  Add to panel.  Try adding the notification area again.

---

### Post by astrakhan on 2009-11-02
might have to install gnome-volume-manager

---

### Post by Kristofer Gustafsson on 2009-11-02
Hm there's no aplet tho.. To add that is..
I installed gnome volume manager and it does not start on boot.. Well it won't show up. I think this might be the problem if i run "gnome-volume-control" in terminal it gives me 

** (gnome-volume-control:3201): WARNING **: Connection failed, reconnecting...

And actually if i go system > preferences > sound .. That app can't connect either.
I broke it!

--

Edit: Could just use alsamixer, guess that works but it's a bit old school feel to that :P

---

### Post by henkeC on 2009-11-03
Having the same problem right now... :-(

---

### Post by 3rdalbum on 2009-11-03
The volume control is built for Pulseaudio. The "Connection failed" message means that there's no Pulseaudio instance running.

You can run the "alsamixer" command in the terminal to get some volume control, or install the "gnome-alsamixer" package to get a graphical volume control. Or, better yet, put Pulseaudio back.

---

### Post by Stelaninja on 2009-11-04
Is there no way to have an equal type of volumecontrol in the panel without Pulseaudio??

It sucks having to start gnome-alsamixer to change the volume.. And  the touchkeys stopped working too, when I uninstalled pulse..

---

### Post by Stelaninja on 2009-11-04
I've found this panel applet

[http://gqapplets.sourceforge.net/applet-smon.html](http://gqapplets.sourceforge.net/applet-smon.html)

that might do the trick, but I can't install it.

When i run configure I get this 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.22 found
checking for perl... /usr/bin/perl
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas/ as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking for libgnome-2.0 libgnomeui-2.0 libpanelapplet-2.0 gconf-2.0... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package libpanelapplet-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libpanelapplet-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libpanelapplet-2.0' found Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (libgnome-2.0 libgnomeui-2.0 libpanelapplet-2.0 gconf-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

Then I tried
```
sudo apt-get install libgnome-2.0 libgnomeui-2.0 libpanelapplet-2.0 gconf-2.0

```
But it says it can't find libgnome-2.0

=(

---

### Post by T-MAN3000 on 2009-11-04
you should probably install the -dev packages (libgnome2-dev, libgnomeui-dev etc)

---

### Post by dublued on 2009-11-05
i'm having the same exact issue

pulseaudio wasn't playing nice so i got rid of it to use alsa which works much better.

only problem is that the volume applet is gone and cannot be re-added to the panel.  the keyboard volume keys have stopped working.

i installed alsamixergui and gnome alsa mixer but nothing beats the convenience of using your mouse scroll as it hovers over the volume control applet.

---

### Post by Kristofer Gustafsson on 2009-11-06
Still using the alsamixer, It sure is akward.. In the previous version of ubuntu my volume thingy worked fine still.

---

### Post by Stelaninja on 2009-11-14
I've reinstalled PulseAudio again and I did some more things (can't remember) but now the clicking sound I had problem with is gone.

My only problem now is that FlightGear doesn't like PulseAudio.. =(

---

### Post by cornholder on 2009-11-14
I also removed my volume control applet from the top bar and couldn't find it under "add to panel" but I tried the earlier poster's suggestion to add "notification area" and sure as shinola it was in there. Thanks, man. However, along with it is an annoying handicapped emblem that I can't get rid of. No response to a right-click. It is as if it is there to remind me of my failures. It mocks me.

---

### Post by Hairy_Palms on 2009-12-13
same problem, pulseaudio is such a steaming pile, its really getting on my nerves how useless its been in multiple releases now.

---

### Post by 3rdalbum on 2009-12-13
Pulseaudio is fine. I don't know what the fuss is about; I don't have a problem with it these days. Just remember that when a program wants you to set up audio inputs and outputs with Pulseaudio, you need to do it in Pulseaudio (the volume control applet) itself, not with the client program.

---

### Post by Hairy_Palms on 2009-12-13
well just the pulseaudio problems that affect me personally in a default karmic install are off the top of my head, 

wine apps, in most of them the sound jumps or is slowed down, the ones that do work have various sound glitches.

random loss of sound requiring a killing and restarting of pulseaudio or a reboot,

many microphone errors complaining about it sending data faster than it should be.

all of these are fixed when pulseaudio is purged from the system, merely disabling it at the runlevels does not work, it has to be totally removed, ive made and signed to multiple bug reports and ive just given up on it.

---

### Post by spadewarrior on 2010-01-01
> **hairy_palms said:**
> well just the pulseaudio problems that affect me personally in a default karmic install are off the top of my head, 

wine apps, in most of them the sound jumps or is slowed down, the ones that do work have various sound glitches.

Random loss of sound requiring a killing and restarting of pulseaudio or a reboot,

many microphone errors complaining about it sending data faster than it should be.

All of these are fixed when pulseaudio is purged from the system, merely disabling it at the runlevels does not work, it has to be totally removed, ive made and signed to multiple bug reports and ive just given up on it.

qft

---

