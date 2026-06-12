---
title: "pulse audio and firefox"
date: 2009-08-01
forum: General Help
---

### Post by sonicb00m on 2009-08-01
I am having pulse audio trouble since reinstalling Juanty, which is strange as the setup was near flawless before.

I have the Intel HDA using the digital out which is working just fine but I have now noticed that firefox won't play any sound if I have something like Totem open first. The converse is also true, totem doesn't play anything if I have firefox open first.

I tried installing the pa tools but they won't open, they are just crashing out. I even installed the 0.15 PPAs of pulseaudio but the problem persists.

Before I upgraded to the 0.15 ppas i had another problem. After a few minutes of sound playback it went completely silence until i logged out and in again. Changing the mixer settings made no difference.

Can anyone help me? I really thought all this audio nonsense was behind me!

---

### Post by sonicb00m on 2009-08-03
I have gone back to the 32bit version now. There seems to be less problems than with the 64bit and im not sure the so called "performance" differences are noticeable.

---

### Post by Vaphell on 2009-08-03
i had such problem in 8.04 (lack of concurrent playback for FF and audio player) but i fixed it by installing libflashsupport package. I don't know if it is a solution for a jaunty setup though.

---

### Post by bobince on 2009-08-03
You really don't want libflashsupport. See the note at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) .

When you get applications that won't support concurrent output, that's because one or more of them is going straight to the ALSA backend instead of going through PulseAudio. (ALSA *can* be configured to support concurrent output itself, but Ubuntu doesn't do that.)

The reason the Flash plugin won't share audio nicely in a 64-bit environment is that you're using a 32-bit Flash plugin with some unpleasantly hacky wrappers around it; this approach doesn't pick up Pulse properly.

The much better solution is to uninstall the default 32-bit Flash and run the native 64-bit plugin instead. This is supposedly ‘alpha’ software, but in practice it's at least as stable as the official release. You can grab it from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) .

---

### Post by Vaphell on 2009-08-03
i stand corrected - libflashsupport made things work for me, but flash sucked both before and after :) Since then i installed native 64bit version of flash 10 to fix grey box issue and apparently it's not needed anymore

---

### Post by sonicb00m on 2009-08-03
thanks for the replies. I actually installed the native version of flash and the same problem persisted. In fact from what i could tell the flash refused to work through pulseaudio at all (firefox never appeared in the volume control mixer).

libflashsupport isn't installed in the jaunty repos so i never go it installed.

Since going back to 32bit I've had zero audio issues and my sata drives are also performing at full speed. Which was another quirky performance issue in 64 bit.

I won't go back now until Koala is released and hopefully these issues are sorted out.

---

