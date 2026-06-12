---
title: "Flash issues"
date: 2011-08-03
forum: General Help
---

### Post by tehchibipanda on 2011-08-03
Greetings, fellow *nix users! I have stumbled into a problem a few months ago that I thought would be corrected with updates, and it has not. It is regarding Adobe Flash. I have done some research, and did find the Flash Aid for Firefox, and that did not seem to help with either version. Basically, the problem I have is when I go to a flash game, the frame rate seems to drop from about 30 FPS to about 15/20FPS. Also, there is a flickering issue on the games. However, videos seem to work fine. I'm using 10.04, 64 bit OS. System specs are:
Gateway NV52
4gb RAM
2.1ghz dual core processor
ATI Radeon HD 3200

I do not feel the hardware of the laptop is an issue; as flash worked fine when i was still a windows user many moons ago. Does anyone know a possible fix for this? I've already disable hardware acceleration as well, and that did not seem to help either. If not, videos still work fine, at least.

---

### Post by flipper T on 2011-08-03
when using flash aid did you choose the adobe labs beta version or the 32 bit version ?

i have 64 bit 11.04 and found that the 32 bit flash runs much better.

had nothing but crashes with the 64 bit beta

---

### Post by tehchibipanda on 2011-08-03
flipper,

Thank you for your response. I have tried both the 32bit stable build, and the 64bit BETA build, both yield similar results as far as flickering/dropped FPS.

---

### Post by tehchibipanda on 2011-08-03
Bumping, in hopes of someone being able to answer. Albeit, if this is the only problem I ever run into with Ubuntu, then so be it. Everything else works without a problem, so I cannot complain.

---

### Post by flipper T on 2011-08-03
hi again

i assume that you have tried using a number of different browsers  ?

have you tried these flash games using windows ? perhaps problem lies with the website

forgive me if i am being a bit too obvious :)

---

### Post by tehchibipanda on 2011-08-03
You are forgiven, sir, as I understand that all precautions must be taken. The websites work fine on windows; I used to have a windows partition on this computer....and when I first got this laptop, it came with Windows 7. It worked fine there; so I do not feel that the problem lies in there. Perhaps there is a conflict with existing flash plugins was my original guess, however, there were none installed in the OS until I installed Flash via Flash-Aid. And I have tried other browsers as well, and it appears to be the same issue. Perhaps Flash is just a spawn of Satan and not meant to work on Ubuntu. Would not surprise me, to be honest...

---

### Post by flipper T on 2011-08-03
can you post some links to the games that are causing you problems & i will give them a go and post back

---

### Post by tehchibipanda on 2011-08-03
[http://www.mochigames.com/game/feed-the-king/](http://www.mochigames.com/game/feed-the-king/)

Choppy^

[http://www.addictinggames.com/kittencannon.html](http://www.addictinggames.com/kittencannon.html)

^Slow FPS

---

### Post by flipper T on 2011-08-03
i dont know a easy way to tell you this, so i will tell you straight (however you may want a stiff drink and a comfy chair before reading on)

... both worked flawlessly for me

feel bad now  :(

using chromium 13.0.782.107 if that helps

---

### Post by tehchibipanda on 2011-08-03
I figured it would be something like my luck. :P Perhaps I will try that Chromium build and go from there, if needed.

---

### Post by Proxmty on 2011-08-16
What are other flash sites like e.g. youtube? If they're slow too, and judging by the graphics card it could well be to do with the compizconfig settings.

Go to Composite, untick detect refresh rate, then go to OpenGL and untick Sync to Vblank.

Try it again, if still issues, uninstall your proprietary driver, then reboot.

Let me know if that helps.

---

### Post by Proxmty on 2011-08-16
> **Proxmty said:**
> What are other flash sites like e.g. youtube? If they're slow too, and judging by the graphics card it could well be to do with the compizconfig settings.

Go to Composite, untick detect refresh rate, then go to OpenGL and untick Sync to Vblank.

Try it again, if still issues, uninstall your proprietary driver, then reboot.

Let me know if that helps.

Sorry, you did say videos are fine. Anyway, if you haven't already is still worth trying

---

### Post by tehchibipanda on 2011-08-19
Did Compiz just now; Oddly enough, I can't find OpenGL O_o; It just...apparently doesn't exist on my system. But for now I will test flash and report results!

---

