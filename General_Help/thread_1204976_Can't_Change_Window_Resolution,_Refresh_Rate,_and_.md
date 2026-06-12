---
title: "Can't Change Window Resolution, Refresh Rate, and can't play DirectX games"
date: 2009-07-05
forum: General Help
---

### Post by zombieplasticclock on 2009-07-05
Ok, so I switched from Windows XP to Ubuntu Jaunty, and it's pretty sweet. However, there are problems I've tried very hard to get around, but nothing seems to work.
(by the way, I'm running a computer that's about 5 years old, and my video card is an Nvidia GeForce MX 4400. And, as mentioned earlier, I'm running the latest version of Ubuntu)

I can't change my video resolution. When I first installed Ubuntu, it defaulted my screen to a nice 800x600 resolution that I'm used to, at 70hz. However, I'm a gamer, so I turned on my hardware device (Via Administration-Hardware Drivers), and now it's kinda screwy. Now, I can only select 640x480 (a rather large resolution for my monitor), and 320x240 (so insanely large it's out of the question). Regardless of what I pick, I can only choose 50hz for the refresh rate on my monitor (which my computer can't detect, by the way), which gives it a painful, high-pitched whine at times. I've tried several options ranging from directly messing with the XORG.conf file, to downgrading ubuntu entirely, and nothing worked. If someone could help me with this, I'd be intensly grateful

Another Question for those wanting to listen: How do I get DirectX games to work on Ubuntu? I've got friends who can run Doom 3 and several old games (Ultimate Doom and Quake 2 old) games on their Ubuntu'd computers without problems. But I can't. Every time I try to install a game, it just doesn't work. And on the rare occasion it does, it crashes, saying it couldn't implement DirectX. The strange thing about this is that I have several emulators, and they have no problem using DirectX. It's very confusing, and I'd like help on this as well (I have Wine, and Play On Linux, if it'll make it easier)

---

### Post by ivanvajar on 2009-07-05
You should have configuration tool for nVidia in System/Administration or Preferences. Did your friends install those games with Wine?

---

### Post by zombieplasticclock on 2009-07-05
> **ivanvajar said:**
> You should have configuration tool for nVidia in System/Administration or Preferences. Did your friends install those games with Wine?
 

Configuration Tool? You mean the "Graphics Driver Vendor's Tool"? When I try to change my graphics settings, I get a popup that says "It appears that your graphics driver does not support the necessary extensions to support this tool. Do you want to use your graphics vendor's tools instead?". I have that, but I don't want to tinker with it too much without knowing what I'm doing.

I believe so. However, when I try to play the game, it crashes, saying some gibberish about graphics (I can't exactly say what it was, since I uninstalled the game. sorry). Another instance, when I tried to install Quake 2, I opened up the setup file with Wine, it opened fine, but when I selected "Install", it froze.

Something that just occurred to me: My friend who could play these games on his computer said that he actually had windows files or something in Wine. I figure actual DLL's or something? He was rather vague. All I know is that it worked

---

### Post by CatKiller on 2009-07-05
> **zombieplasticclock said:**
> Regardless of what I pick, I can only choose 50hz for the refresh rate on my monitor

It's not 50Hz. If you look in NVidia's own configuration tool, it will report the correct refresh rate. The NVidia driver deliberately misreports the refresh rate for the standard methods. There is a way to change that behaviour if it really bothers you.

For your refresh rate problem; you've already said that your monitor isn't reporting the correct information which would let it be automatically configured. It's a common problem amongst some monitor manufacturers; [EDID]("http://en.wikipedia.org/wiki/EDID")'s only been around for 15 years, you can't expect them to have actually implemented it :rolleyes:

Happily, you can specify the information that the monitor should report. The most critical parts are the refresh rate ranges that your monitor can do; without this information, X defaults to really low ranges that won't damage any monitors. You can get this information from the manual or specifications for your monitor. This information goes in the monitor section of xorg.conf, like so:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```

You'll need to replace aa-dd with the values for **your** monitor.

To go onto your second question, DirectX is a Windows technology. It's a pretty fundamental part of Windows. Microsoft won't share it with anyone else. Which means that DirectX system calls are meaningless on anything other than Windows. However, the WINE project has produced a compatibility layer which translates Windows commands into native Linux commands, using OpenGL for accelerated graphics.

Wine's [Application Database]("http://appdb.winehq.org/") will give you information on ways to get particular applications to work. Occasionally this will involve using a Windows-native DLL, but it's not that common. Many of iD Software's games have been ported to run natively in Linux and, since the game engines were open-sourced, there are a number of free games based on iD games. I understand that Tremulous, Urban Terror and Enemy Territory, which are all Linux-native and all use the Quake 3 engine, are popular. Personally, I always preferred Unreal Tournament to Quake. That runs natively too. But I have also enjoyed Deus Ex and Half-Life through Wine. It didn't really take any setting up for those two.

---

### Post by zombieplasticclock on 2009-07-05
That may help a bit, although I've yet to think of a way to find my monitor's specs.

And I still don't know about the game thing. Another game I have in mind is "The Typing of the Dead", which is a somewhat old game, and another that my friend can run while I cannot.

Maybe I'm just doing the game thing wrong, so that problem is solved. What I would love to learn how to fix is my ridiculous screen resolution

---

### Post by CatKiller on 2009-07-05
> **zombieplasticclock said:**
> That may help a bit, although I've yet to think of a way to find my monitor's specs.

It might help if you told us what your monitor was :)

---

### Post by zombieplasticclock on 2009-07-06
It might. Sorry to not mention it sooner. It's an Impression 7Plus monitor (IE: Old as hell). I looked at the label on it's back, but it only had serial numbers and stuff, nothing that could really help fix these problems

---

### Post by CatKiller on 2009-07-06
According to [this page]("http://logicalplus.stores.yahoo.net/im7plus17in1.html"), the numbers you need are
```

        HorizSync       30-70
        VertRefresh     50-160

```

Never underestimate the power of a Web search :)

---

### Post by zombieplasticclock on 2009-07-07
lol, that thought didn't occur to me, so thanks for the help!

So if I input these values, then my screen won't be so large?

---

### Post by zombieplasticclock on 2009-07-07
Whoa, something is wrong here. My resolution is awesome, but now all my programs are acting funny. They worked perfectly fine before the change, and now they don't, and reinstalling doesn't help. any ideas?

---

### Post by zombieplasticclock on 2009-07-09
Whoa, something is wrong here. My resolution is awesome, but now all my programs are acting funny. They worked perfectly fine before the change, and now they don't, and reinstalling doesn't help. any ideas?

(btw, sorry for the double-post. Last attempt accidentally "edited' my last post into this one. My bad)

---

### Post by CatKiller on 2009-07-09
"Acting funny" isn't really that precise. Is it dancing clowns, or what?

---

### Post by zombieplasticclock on 2009-07-09
> **CatKiller said:**
> "Acting funny" isn't really that precise. Is it dancing clowns, or what?

Lol, no clowns here. I'm saying that my programs don't work the way they used to. Some are still stuck in 640x480 resolution (which can't be changed), some of my games now have glitchy graphics, and now my programs are generally slowed down.

Is there a way to fix it? I mean, my first plan was to re-install Ubuntu completely, but if there's a quicker solution, I'd be glad to hear it

---

### Post by CatKiller on 2009-07-09
> **zombieplasticclock said:**
> Is there a way to fix it? I mean, my first plan was to re-install Ubuntu completely, but if there's a quicker solution, I'd be glad to hear it

Re-installing Ubuntu isn't going to help. It'll just mean that you only have the low resolutions again. The change that you've made has only made more resolutions available. Strictly speaking, it's just stopped the higher resolutions being thrown away.

Are the applications that you're having problems with Wine applications? You might want to check out your Wine config to see if you're emulating a 640×480 Desktop or something.

---

### Post by zombieplasticclock on 2009-07-09
> **CatKiller said:**
> Re-installing Ubuntu isn't going to help. It'll just mean that you only have the low resolutions again. The change that you've made has only made more resolutions available. Strictly speaking, it's just stopped the higher resolutions being thrown away.

Are the applications that you're having problems with Wine applications? You might want to check out your Wine config to see if you're emulating a 640×480 Desktop or something.

Well, what I had in mind was re-install ubuntu, do the monitor fix again, THEN reinstall everything. It'll work, but it'll take a while. Wine config, you say? That may do it. Lemme take a look at that (yes, a majority of my programs are run by WINE)

EDIT: Worked. Some programs are tiny, but screw it. I'll figure it out. Thanks for the help!

By the way, I also fixed my DirectX game problem now

---

