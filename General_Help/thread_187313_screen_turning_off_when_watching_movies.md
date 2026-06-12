---
title: "screen turning off when watching movies?"
date: 2006-06-02
forum: General Help
---

### Post by mbirkis on 2006-06-02
Is there a way to disable all screen saver / power saving features when watching movies? if i watch a movie the screensaver starts and the screen eventually goes black after a while, and i have to move the mouse to get the display back.

How can this be sorted?

---

### Post by joshrobinson on 2006-06-02
[QUOTE=mbirkis]Is there a way to disable all screen saver / power saving features when watching movies? if i watch a movie the screensaver starts and the screen eventually goes black after a while, and i have to move the mouse to get the display back.

How can this be sorted?[/QUOTE]

system > preferences > screensaver.. click the activate screensaver when idle to uncheck it.. or crank the time up to 2 hours

---

### Post by mlind on 2006-06-02
Which movie player are you using?

Totem should keep gnome-screensaver and gnome-powermanager informed
to not start doing any fancy stuff usin DBUS when you're watching movie, but
I'm not sure if mplayer, VLC or other 'non-gnomish' media players know how to do this..

This was also on top-5 bugs on Dapper flight versions, but it should have been fixed by now (?)

---

### Post by mbirkis on 2006-06-03
i am using mplayer

---

### Post by spite on 2006-06-03
Use gmplayer or run mplayer with -stop-xscreensaver. It works for me.

---

### Post by mbirkis on 2006-06-03
[QUOTE=spite]Use gmplayer or run mplayer with -stop-xscreensaver. It works for me.[/QUOTE]

Ok! I there a way i can add this so that it automatic runs when i double click movie files?

---

### Post by panurge77 on 2006-06-03
right click> edit menus> right-click mplayer>proprieties
change the command
:)

---

### Post by SiMoNsAyS on 2006-06-03
are you using xgl, meaning can you choose between gnome and xgl on GDM?

---

### Post by zitch on 2006-06-03
Actually, I'm having the same problems on my laptop.  My screen seems to blank out after 15 minutes of no keyboard or mouse input.  I have my System->Preferences->Power management set to never on all options under Running on AC and Running on Battery tabs.  I also disabled the screensaver (System->Preferences->Screensaver: Set the Session to idle after 2 hours and deactivated the screensaver) and the screen still blanks after about 15 minutes.  Makes it a real pain when watching a movie on the laptop.

It doesn't matter if I'm using MPlayer, Totem, or VLC, the screen will still blank out.

Any other suggestions of where to look?.

SiMoNsAyS: "are you using xgl, meaning can you choose between gnome and xgl on GDM?"

Actually, I am running Xgl this way...

---

### Post by mcpish on 2006-06-03
I had this problem

Turn off all power-management

System > Preferences > Power Management
 
turn both sliders to "Never" on the far right

---

### Post by SiMoNsAyS on 2006-06-03
then that's the problem, i filled this issue before: [http://www.ubuntuforums.org/showthread.php?t=170920&highlight=](http://www.ubuntuforums.org/showthread.php?t=170920&highlight=)

problem is that i didn't know where to report it :(

---

### Post by cbudden on 2006-06-11
I have also got this problem. ATI mob radeon 9700 with repo fglrx with XGL/compiz.  I have commented out dpms in xorg.conf but it didn't work.

---

### Post by denkedran on 2006-06-11
try to set dpms manually
```
xset -dpms
```
or set dpms option in xorg.conf to false

---

### Post by cbudden on 2006-06-11
This doesn't work. Thanks anyway.

---

### Post by mlind on 2006-06-11
[QUOTE=SiMoNsAyS]then that's the problem, i filled this issue before: [http://www.ubuntuforums.org/showthread.php?t=170920&highlight=](http://www.ubuntuforums.org/showthread.php?t=170920&highlight=)

problem is that i didn't know where to report it :([/QUOTE]

I guess you should report it against gnome-power-manager on launchpad.net
[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bugs](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bugs)

---

### Post by zarej on 2006-07-24
Try use this script which stop gnome-power-managment while mplayer is running, and then when you quit mplayer start it again.

```
#!/bin/sh
killall gnome-power-manager
gmplayer $@
gnome-power-manager

```

---

### Post by mlind on 2006-07-24
There seems to be related patch for mplayer
[https://launchpad.net/people/siretart/+branch/mplayer/gnome-screensaver-handling](https://launchpad.net/people/siretart/+branch/mplayer/gnome-screensaver-handling)

---

### Post by stairwayoflight on 2006-08-13
hi,

i have this problem when playing movies with totem. i double click on a movie file, then a few minutes into it, the screensaver comes on.

is there any way to get rid of this without totally disabling power management features? i leave my box on 24/7 for p2p; i don't want the monitor on all the time.

---

### Post by warjowuch on 2006-09-28
*bump* I'd also like a solution to this stupid problem. I am using xscreensaver though, because a while ago, the gnome-screensaver made a lot of crashes, as I read around these forums and exprecienced on my own computer.

So, anyone allready seen or knows a solution??

---

### Post by koniu on 2008-02-27
Its a bit old thread, but maybe someone will find it useful anyway . 

[http://ubuntuforums.org/showthread.php?t=535103]("http://ubuntuforums.org/showthread.php?t=535103")

Didn't work for me but there are happy people there. 

Ta,
Koniu

---

