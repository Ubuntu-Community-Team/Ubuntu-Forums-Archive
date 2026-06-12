---
title: "Video Playback Problem at 1600x1200"
date: 2006-05-17
forum: General Help
---

### Post by unnes on 2006-05-17
Ever since I installed Ubuntu, I've been running a desktop resolution of 1280x1024 with no problems. Recently, I chose to switch to 1600x1200, and after tinkering with modelines in xorg.conf, I managed to get my display at that resolution.

I have, however, since run into some problems: Every time I want to play a video, I get audio playback, but the video appears to be a blue screen. This happens in Totem, VLC, and MPlayer, and happens with xvids (AVIs and MKVs), MPEGs, and every other video format I have tried.

[CENTER][IMG]http://img2.imagepile.net/img2/1274581765.jpg[/IMG]

[(click here to view 1600x1200 screenshot)]("http://img2.imagepile.net/img2/1157467654.png")[/CENTER]

Does anyone know a possible cause of or solution to this problem? I don't use this machine for video playback regularly, but it would be nice to be able to maintain this resolution and still be able to play videos.

My graphics chip is an onboard Intel i810 using shared RAM.

---

### Post by cssutto on 2006-05-17
I have had exactly the same problem and have had no luck in finding a solution.

If you find one, I would appreciate your letting me know.

I might be able to give you a clue.

First, I am running my display, a Sonly LCD, at 1280 x 1024.

My machine is a Thinkpad A31p.  I almost never use the display on it as it is going bad for the thrid time.  I have a Sony remote display at home and at the office.

So here is the clue.  After fighting the problem for a week or so, spending hours on it checking codecs, reloading players, etc., for some reason I opened the lid on the Thinkpad and there was the movie playing perfectly.

So I had two displays, one identical to your illustration, and the other exactly as it should be.

So my conclusion is that all of the codecs are loaded properly or the laptop would not be perfect.

What I suspect, in my complete and total ignorance, is that the DVD player is sending a signal to the LCD that it can not handle whereas the Thinkpad is happy with what it is getting.

So it has to be something like refresh rate, horizontal or vertical settings; I have no idea which.

There has to be an expert on monitors out there somewhere, but I have not had any luck.

CSSJR

---

### Post by unnes on 2006-05-17
> So it has to be something like refresh rate, horizontal or vertical settings; I have no idea which.

That sounds like a reasonable assumption. However, I'm like you and really don't know much monitors, refresh rates, etc.

How did you eventually get around the problem, if you did?

---

### Post by cssutto on 2006-05-17
"How did you eventually get around the problem, if you did?"


I have not.

Mplayer will work, but I do not like it.

Everything else gives me the same blue screen you have....totem, VLX, Xine, Gxine...blue.

CSSJR

---

### Post by GhandiBurger on 2006-05-17
This is my problem as well (only I am running a Dell 2005FPW at 1680x1050). I also would appreciate a solution.

---

### Post by BeFs on 2006-05-21
Its a bit tricky to get the codecs to play on both screens.
Most codecs will only play on the primary monitor, try to disable it.

---

