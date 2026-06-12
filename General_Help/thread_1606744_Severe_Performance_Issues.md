---
title: "Severe Performance Issues"
date: 2010-10-26
forum: General Help
---

### Post by kerryhall on 2010-10-26
I hate to say this, but having performance issues that are rendering my computer unusable.

Firefox with all extensions and addons disabled, and only one tab open, (the about:blank) is using 500 mb. Pidgin uses well over 100 mb. Transferring videos from my camera to my computer uses over 500 mb and takes about 15 minutes to transfer 500 mb. Clicking cancel on that copy operation takes about a minute for it to cancel. Rhythmbox uses over 100 mb and will just simply stop playing and will not restart if cpu usage spikes. Evince takes around 30 seconds to load a 500k pdf. Nautilus takes up over 100 mb. Java runtime uses over 500 mb for a simple hello world application. I can't run OpenOffice and firefox at the same time without thrashing. Firefox or Evince takes around 15 seconds to minimize and redraw the desktop. Pulseaudio uses over 100 mb. mysqld uses over 100 mb. Loading a resonable sized png in the gnome image viewer takes around 15 seconds. Gnome terminal takes around 15 seconds to load. Xorg is using over 100 mb. Evince takes several seconds to scroll down at all on a simple text based pdf. 

The faster computers seem to get, the slower all my programs seem to go.  I seem to recall playing Half Life on a Pentium 2 233 with 64 mb of ram, but I can't use a web browser and a word processor at the same time on an 3 ghz with 512 mb ram??

---

### Post by PRC09 on 2010-10-27
You may have to upgrade the ram in your machine....


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by kerryhall on 2010-10-27
I had 1.5 gigs until a 1 gig module failed the other day. It was working fine then, but I have noticed that processes seem to use more memory then they probably should. And now that memory has failed, my machine is unusable. I could certainly buy a replacement module, but this has become a matter of principle. 

Seriously Pidgin? >100 mb?? For an irc client?? I would expect it to use 10 mb, tops. What does it have to store in memory besides the chat logs? And if we consider I am connected to five rooms, each message is 1k, with a history of 1k messages per room = 5 mb of string data. Yet I am currently showing pidgin using 400 mb. I know shared libraries are included in VIRTUAL, but would a chat program be using 400 mb worth of shared libraries?

Here is my idea: lets try and fix the software, or better yet, write better code in the first place.

Also: could this be a gtk or x.org issue?

---

### Post by TeoBigusGeekus on 2010-10-27
Me thinks it's time for a lighter browser (Chromium, Opera) and a lighter wm (Openbox).

---

### Post by philinux on 2010-10-27
What does 

free -m

show?

---

### Post by kerryhall on 2010-10-30
> **TeoBigusGeekus said:**
> Me thinks it's time for a lighter browser (Chromium, Opera) and a lighter wm (Openbox).

It's too bad firefox isn't up to par. I don't understand what the problem is! Lol Lynx runs well for me at least.

I switched over to Compiz, and all the window manager related issues went away (minimizing, etc)

Does compiz take metacity out of the equation entirely?

---

### Post by kerryhall on 2010-10-30
> **philinux said:**
> What does 

free -m

show?

Running it right now gives me 54 mb free.

Firefox is using 516 mb, Xorg is using 208mb, gmplayer is using 170mb, mysqld is using 140mb (not sure why it's even being used. firefox?) 

Tried double clicking on a text file on my desktop. (1k file) It took approx 5 seconds for the click to register, then, unfortunately no exaggeration here, 50 seconds for gedit to load.

Clicking on any menu item in any application takes about two seconds to register, making any UI very frustrating to work with.

I think firefox is my main problem. Although it is a shame it must be relegated to the trash bin, rather than having memory leak issues fixed.

All the bitmaps that must be displayed, such as widgets, images in browser, images in nautilus preview (sadly disabled for now), are those kept in system memory or video memory? (Obviously the buffer when they are displayed, but I mean like as textures, opengl style) Seems like video memory would be a good place to store them, or at least have the option, and free up system memory for other things.

Thanks for the help everyone!

---

### Post by TeoBigusGeekus on 2010-10-30
> **kerryhall said:**
> Firefox is using 516 mb, Xorg is using 208mb, gmplayer is using 170mb, mysqld is using 140mb (not sure why it's even being used. firefox?) 

:shock:

Here's my htop with Opera (9 tabs), gimp and rtorrent running.
...oh, and we're talking about a P4 here.

---

### Post by kerryhall on 2010-10-30
Haha yep. Got a problem here.

Got the screenshots to prove it too, will post em later.

---

### Post by kerryhall on 2010-11-09
Bump

---

### Post by russo.mic on 2010-11-09
So you said that it was fine before you had a 1 ghz stick die?  I think the problem is honestly you just need to get more ram.  your not used to the drop in speed.

Still, it might be worth looking at your HD speed and what your swap is doing...

---

### Post by kerryhall on 2010-12-02
I just think it is completely unacceptable for gedit to take 30 seconds to one minute to start up on a computer with 512 MB ram. 

Not everyone can afford top quality hardware, or even one new stick of ram, we should be trying to make software that can run well on even the slowest or memory deficient hardware.

Obviously take advantage of the hardware if its there, but detect how much ram the user has, and adjust accordingly, or at least allow the user the option of adjusting features according. 

Not sure what features cause nautilus to take 30 seconds and 100 Mb to display a folder of maybe 200 files and folders (preview disabled)

---

