---
title: "[GAME] Machinarium - Slow Mouse"
date: 2009-11-07
forum: General Help
---

### Post by Xog on 2009-11-07
):P Hello all,

I'm running 9.10 and I downloaded Machinarium ($20) for linux. I'm having some problems with my mouse. It works fine in browser mode for the DEMO online which u an play ([http://machinarium.net/demo/](http://machinarium.net/demo/)).

However in the full version when I try to move my mouse around, it works fine, until it goes over a certain area on the screen to which I can use (in the game), and the cursor will change to an animation (intended) but it slows down and is very annoying because I wind up going way across what I want to click on.

I hope there's an easy fix to this. Oh and I have the latest Recommended driver from NVidia, and the game is up to its latest patch. It's a very simple game and not graphics heavy at all, just point and click.. I don't understand why this would be such a big problem.  :(

Also, this uses WINE to run.

[UPDATE]
I switched to Windowed mode and it works fine. Is there a way to fix this so that I can play in full screen?
I noticed that when the game starts, it's as if I press "Full Screen" for a video on YouTube, it says "Press Esc to exit Fullscreen" (but this doesn't work, I have to go to the options in the game, I don't think that was part of the game's code, but a general protocol for ubuntu when switching to full screen)

Something else to note:
On the bottom task bar, instead of saying "Machinarium" for the game as it's running, it says "Adobe Flash Player 10"

---

### Post by Devi 710 on 2009-11-13
I just bought the full version and the mouse is so bad it is completely unplayable. 

I keep reading that it works in Windowed mode, but I can't get to it. "esc" doesn't work and I can't click on it in the options because the mouse is beyond delayed. Doesn't matter if I have "hardware acceleration" turned on or off in Flash.

I am sooo disappointed and would really like my money back.

---

### Post by Xog on 2009-11-14
> **Devi 710 said:**
> I just bought the full version and the mouse is so bad it is completely unplayable. 

I keep reading that it works in Windowed mode, but I can't get to it. "esc" doesn't work and I can't click on it in the options because the mouse is beyond delayed. Doesn't matter if I have "hardware acceleration" turned on or off in Flash.

I am sooo disappointed and would really like my money back.

When you're in full screen mode, bring your mouse to the bottom of the screen. From there, a menu with a bunch of options will pop up. Click "[x] Fullscreen" to go into windowed mode

---

### Post by Devi 710 on 2009-11-14
Thanks for the reply.

I was eventually able to switch to windowed mode. It took a long time. My mouse would be in the middle of the screen and the bottom menu would appear. I had to guess where the computer thought my mouse was.

Great game now that I can play it.

---

### Post by kalos on 2010-08-19
I just picked this up recently and found that right clicking and turning off hardware acceleration from the flash menu made the mouse more responsive in fullscreen.

---

### Post by aapo4 on 2010-12-27
I confirmed both workarounds for slow/laggy mouse:
*Windowed mode
*Hardware acceleration OFF

(64bit Ubuntu 10.10 + Flash 10.0 r22)

---

### Post by thecapsaicinkid on 2011-01-03
I have the same issue when running at my screens native 1080p but not at lower res such as 1280x720p (game is 1280x800 so I obviously can't have the 100% option)

Windowed mode works fine (makes no sense :confused:) Hardware accel is disabled. CPU never exceeds 60%, again, makes no sense.

God I hate Flash.

---

### Post by skolnick on 2011-02-07
Hi

I have my laptop running fedora 13 and KDE 4.5 and my desktop, which runs Ubuntu 10.04 and GNOME. I tried the machinarium demo on both and I just found out the laptop works perfectly, even with hardware acceleration on, but the desktop exhibits the exact same problem described by the original poster. This makes me think the problem is related to the desktop environment used.

Regards.

Edit: typo in the fedora version.

---

### Post by pqwoerituytrueiwoq on 2011-02-07
try setting the quality to low the game is made in adobe flash
sadly you have to set the quality ever time you change location
use 64bit flash if possible
edit i did not use wine to play it
i got mine via humblebundle.com
there is a .tar.gz it has a compiled app in it that opens it in flash

---

### Post by Cherry Cotton on 2011-08-07
In fullscreen mode, I have the problems described above, whether or not hardware acceleration is enabled. In windowed mode, I... can’t click on anything. Seriously, nothing responds to the mouse, not the title screen, not the initial options, not the objects in the game. The only thing to do then is quit (or use the Flash player’s own menu to go back to fullscreen). Any idea of what’s going on?

---

### Post by HDave on 2011-11-24
I can confirm this issue on 11.10.  If you get manage to get to the menu at the bottom of the game, then you can disable full screen and run in windowed mode.  Everything works fine after that.

Thanks very much aapo4 for the tip. :D

---

### Post by AaronP_ on 2012-01-14
Try this patch to libX11 to work around it:
```
git clone -b machinarium-workaround git://people.freedesktop.org/~aplattner/libX11
cd libX11
./autogen.sh --prefix=$HOME/games/Machinarium
make install
cd $HOME/games/Machinarium
LD_LIBRARY_PATH=`pwd`/lib ./Machinarium
```
Add "CFLAGS=-m32 LDFLAGS=-m32" to the autogen.sh line if you're building on a 64-bit system.

---

