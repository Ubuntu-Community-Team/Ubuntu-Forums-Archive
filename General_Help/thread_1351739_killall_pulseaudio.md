---
title: "killall pulseaudio"
date: 2009-12-10
forum: General Help
---

### Post by michaelzap on 2009-12-10
I'm getting very sick of having to run this command every hour or so in order to keep pulseaudio from gobbling up gigs and gigs of memory. Thanks to a udev update shortly after Karmic was released, I'm stuck with [this pulseaudio memory leak]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655"). The only other fix (reverting to the old udev package) disables USB automounting, and I'm not sure whether that cure isn't worse than the disease.

Has anyone found a reasonable fix for this yet? Isn't this affecting everyone with an updated Karmic system? I haven't seen many posts on it, which surprises me because this is more than a minor bug.

---

### Post by vgrisham on 2009-12-11
I agree. [This bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655") is the pits. I have been happily using Ubuntu since Dapper Drake, and for the first time, I've found myself considering other operating systems that shall not be named. Karmic is really testing my faith in Ubuntu. I hope this along with other problems (network printing is really glitchy and the system tray is rendering 3rd party icons like a 4 year old with a crayon) get fixed soon.

---

### Post by slumbergod on 2009-12-11
Can't you just remove it and revert to alsa?
I never had pulse working so if I install a new distro the first thing I do is get rid of it. Then everything works properly again.

---

### Post by akashiraffee on 2009-12-11
> **slumbergod said:**
> Can't you just remove it and revert to alsa?
I never had pulse working so if I install a new distro the first thing I do is get rid of it. Then everything works properly again.

Yeah.  I couldn't get sound to work properly at all when I first installed 9.10.  On thing I noticed is that the kernel was loading drivers for both the inboard sound (unused) and the sound card.  Alsa was trying to use the inboard, and pulseaudio just plain did not work, eg, for web noise.

I built my own kernel, uninstalled pulseaudio, reconfigured/reinstalled alsa, and now everything is fine.

I think you should only use pulseaudio if you have trouble with alsa, and not otherwise.

---

### Post by michaelzap on 2009-12-11
> **slumbergod said:**
> Can't you just remove it and revert to alsa?
I never had pulse working so if I install a new distro the first thing I do is get rid of it. Then everything works properly again.

I tried to do that when I first installed Karmic and found that my 5.1 sound didn't work, but I couldn't get Alsa to work properly afterwards so I had to reinstall pulseaudio. Seems much more difficult to get rid of it in Karmic. If there's a way to do this that works in Karmic and doesn't otherwise cripple audio on my system I'd be glad to try it again.

---

### Post by vgrisham on 2009-12-11
Hey, that works! Thanks!

The only problem now is that my laptop volume up and volume down function keys don't work (I'm using a System76 Pangolin). Keyboard Preferences still recognizes them, but they no longer have an affect on volume. Any tips?

---

### Post by michaelzap on 2009-12-11
> **vgrisham said:**
> Hey, that works! Thanks!

What works exactly? Just uninstalling pulseaudio? Last I tried that in Karmic I couldn't get any sound output at all.

---

### Post by vgrisham on 2009-12-11
After dumping pulseaudio. I installed alsa mixer, et voila, no memory leak in the ironically named Karmic.

Edit: And, yes, I have sound.

---

### Post by vgrisham on 2009-12-11
In addition to the volume function keys not working now, when I choose Sound from the System>Preferences menu I now get the message, "Waiting for sound system to respond." How do I adjust my sound preferences now?

---

### Post by michaelzap on 2009-12-11
> **vgrisham said:**
> In addition to the volume function keys not working now, when I choose Sound from the System>Preferences menu I now get the message, "Waiting for sound system to respond." How do I adjust my sound preferences now?

Hmm. I seem to remember having that problem also.

---

### Post by michaelzap on 2009-12-24
Almost two months since Karmic came out, and I still need to killall pulseaudio constantly...

---

