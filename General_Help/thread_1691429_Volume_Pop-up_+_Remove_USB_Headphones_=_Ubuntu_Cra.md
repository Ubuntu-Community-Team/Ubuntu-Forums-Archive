---
title: "Volume Pop-up + Remove USB Headphones = Ubuntu Crashes"
date: 2011-02-19
forum: General Help
---

### Post by Snow Pickles on 2011-02-19
Removing usb headphones (I tried two brands) from my computer while the volume pop-up is up renders Ubuntu completely unresponsive, it crashes. It leaves behind a black screen with a single underscore at the top left and my mouse pointer (although once it froze with the everything intact, just frozen - did X crashing or something?). 

I believe it's not that I'm changing the volume, but the pop-up that is crashing things. If I wait for the pop-up to disappear, everything's fine and it doesn't crash when I remove my headphones. 

  So I removed notify-osd, restarted, and sure enough, that familiar volume pop-up went away. However, it was replaced by its ugly cousin (see attachment), which suffers the same crashing problem. So I was hoping someone would recognise this pop-up and know what package it came from so I can uninstall it (I was just messing with my sound, so it could come from some pulse-audio utility, jackd, fluidsynth - any of that junk).

  Otherwise, perhaps someone could help me gather some info on the nature of the crash and maybe file a bug report?
Thank you in advance!

---

### Post by Snow Pickles on 2011-02-23
Well, I narrowed things down a bit.

I had a beat-my-head-against-the-wall adventure with pulseaudio and alsa, for a while thinking that removing pulseaudio would fix the problem. Once  I configured alsa to my liking, I found out that it too would crash when I removed my headphones. In fact, after all this fiddling, I've worn out one port to the point that plugging my headphones into it will crash my computer within a few seconds.

So after much despair, I got pulseaudio back, since alsa decided to completely crap out on me.

Now my system is back to <mostly> the way it was. However, while I was messing aronud, I found that my problems weren't directly from the Volume Pop-ups, as at one point I had broken both of the volume pop-ups yet my system would still crash.

It might not even have anything to do with changing the volume and removing the headphones at the same time.

In short, I've gotten almost nowhere, and now the problem could be anything. Anyway, suggestions on what dark cavern of sound related pain I should dive head first into next?

---

### Post by tredegar on 2011-02-23
This looks like a hardware problem.

If you poke/gently stress the "worn out" USB port with a piece of plastic, does your machine crash?

---

### Post by Snow Pickles on 2011-02-23
Hadn't thought of that, thanks.

But alas, no dice.

I poked it like you said, I tried other USB devices (mouse, printer) , and I even tried windows. Only my USB headphones in ubuntu could crash it. Plus, it happens on all 3 USB ports.

I will try this on the livecd though, later tonight.

Thank you for the advice anyway!

---

### Post by Snow Pickles on 2011-02-24
The livecd did not have the error!

Now I just have to figure out what package/change to my system is causing this.

I'll report when (if) I do.

---

### Post by robla on 2011-02-28
I've had a very, very similar problem on my machine (Lenovo Thinkpad T510 with Plantronics Audio 655 USB headset).  The machine is completely frozen in my case, though not with the black screen.  I also spoke with someone else who I work with that is also seeing this behavior.

I wasn't able to find any logs that provide any useful information about this problem.

I had not noticed any correlation between the volume popup being up and the crashing occurring.  I tried killing PulseAudio before unplugging (trying to unplug before it respawned), but no joy.

---

### Post by steve7777777 on 2011-03-15
Has there been a solution? Seems like a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727554)

I have a similar problem with an Asus AS 1410 netbook. When unplug the Logitech USB headphones the system crashes - get the black screen.

The headphones have a microphone built in.

---

### Post by steve7777777 on 2011-03-17
0 replies????

---

### Post by LenW on 2011-04-26
> **steve7777777 said:**
> Has there been a solution? Seems like a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727554)
....

Good news (or at least I hope it is)!
This bug looks very similar to another one:

    [url]https://bugs.launchpad.net/ubuntu/+source
/linux/+bug/715318[/url]

which seems to be fixed in Natty.
First one to test it and post results here gets
the emoticon of their choice   :-)

-Len

---

