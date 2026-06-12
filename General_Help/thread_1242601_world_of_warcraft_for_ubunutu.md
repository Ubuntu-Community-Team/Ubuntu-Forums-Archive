---
title: "world of warcraft for ubunutu"
date: 2009-08-17
forum: General Help
---

### Post by Arminius on 2009-08-17
are there any other options other then wine? and code weavers?
I tried wine, and it could never correctly mount wrath of the lich king dvd.
I tried code weavers, it all installed fine but constantly crashes in dalaran.

so any 3rd options?

---

### Post by Cheesemill on 2009-08-17
Windows :)

---

### Post by Arminius on 2009-08-18
yes thank u cheese, after I've stopped laughing, can someone else tell me any other real options?

---

### Post by P4man on 2009-08-18
Have a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

Scroll down until you see: "Problems in Dalaran with Jaunty"

Solution seems to be removing pulseaudio.

And no, there is not other way than wine. Code weaver's crossover is also wine based.

---

### Post by xagapiou on 2009-08-18
Try playonlinux. It is based on wine also but has some preconfigured settings. I don't know if it solves your problem because i don't play wow but you can give it a try.

---

### Post by geirha on 2009-08-18
Problems mounting the wow dvd is a well known problem. It's explained at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Master_Q on 2009-08-19
Hello Everyone, I'm new to Ubuntu and I'm kinda running into a brick wall with alot of programs I used in Windows XP that I am trying to get working in Ubuntu, and even though I know that Wine and PoL are a couple of programs I can use for them, World of Warcraft is one I am trying not to install from the beginning again.  Is there an instructional Step by step guide a person with WOW already installed can use to reconfigure and work through Wine on Ubuntu 9.04, if so can you please show me where?  Thanks for your Time..:)

---

### Post by Arminius on 2009-08-28
> Problems mounting the wow dvd is a well known problem. It's explained at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

well this worked for me, got it mostly working under wine.
except one annoying flaw, when I alt tab away, check something on wow head, then alt tab back, the game is unstable.
camera keeps staring at the ceiling, ubuntu tool bars at the bottom and top are still visible, obscuring the game bars, and soon after the wow server kicks me.

---

### Post by jerome1232 on 2009-08-28
Switch to a different workspace instead, ctrl+alt+left or right arrow.

If you hold shift+ctrl+alt+left or right arrow you will shift the current active application to another workspace (in case the program you want was on the same workspace as wow)

---

### Post by Arminius on 2009-08-28
nah when I ctrl alt my way over to the wow screen it's the same problem, ubuntu bars are still there.
and wow is now unstable.
all the same problems I had before.

---

### Post by themusicalduck on 2009-08-28
Unless you're only willing to play in full screen mode, running wow in windowed mode might make using other windows a fair bit easier.

Also running it on a virtual desktop may help too, if you do want to use full screen only.

---

### Post by Arminius on 2009-08-28
I can't run it in virtualbox?
it keeps saying it can't find my video card?
I asked ages ago if I could, I was told it wasn't possible until virtualbox supports 3D
when I noticed it seemed to have some kind of prototype 3D setting I tried again, but still virtualbox still didn't like it
I think it's exact words were "can't find your display adapter"
not to sure though

---

### Post by jerome1232 on 2009-08-28
Do you have compiz on? I have to turn it off or WoW goes crazy when I alt+tab/switch workspaces.

---

### Post by P4man on 2009-08-28
> **Arminius said:**
> I can't run it in virtualbox?
it keeps saying it can't find my video card?
I asked ages ago if I could, I was told it wasn't possible until virtualbox supports 3D
when I noticed it seemed to have some kind of prototype 3D setting I tried again, but still virtualbox still didn't like it
I think it's exact words were "can't find your display adapter"
not to sure though

3D support in virtualbox is indeed experimental, and ironically, using parts of wine. For gaming you're better off under wine.  Better, but not great yet. Start petitioning blizard for a native linux client :)

---

### Post by Arminius on 2009-08-28
> Do you have compiz on? I have to turn it off or WoW goes crazy when I alt+tab/switch workspaces. 

didn't know what u ment by compiz, so I googled it, and if the wikipidia entry I found is right, then it's the desktop visual effects?

yeah I had maximum visual effects on, so I turned it off, and yes no problem now.

thanks

---

### Post by jerome1232 on 2009-08-28
There a nice little app that puts an icon in your sys tray which allows you to easily turn compiz on and off. (and yeah compiz is what allows for special effects btw)

It's called fusion-icon. 

You can use synaptic to install it then add it to your list of applications to start up by default (System-Preferences-Startup Applications)

To start it for the first time hit alt+f2 and type fusion-icon, a little blue square should appear in the upper right corner.

You can then click it and select Compiz (special effects) or Metacity (no special effects) under the Window Manager option.

---

