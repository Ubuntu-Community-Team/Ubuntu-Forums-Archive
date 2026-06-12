---
title: "On Ubuntu, NVIDIA 3rd party drivers, and screen refresh rates"
date: 2010-08-12
forum: General Help
---

### Post by RB_ on 2010-08-12
I have a laptop computer, containing a GeForce 9600M GS, using an external CRT (eek!) monitor, running the latest release of Ubuntu(64 bit) - up to date with updates.

I also installed the NVIDIA driver via. 

System -> Administration -> Hardware Drivers

Currently, the Hardware Drivers interface tells me that the green-lighted "Activated and currently in use" driver is:

"NVIDIA accelerated graphics driver (version current) [Recommended]"

**My issue:**

In 
*System -> Administration -> NVIDIA X Server Settings *
then clicking the
*X Server Display Configuration *
tab, i see the following, under the *Display* sub-tab:


[IMG]http://imgur.com/LnTRH.png[/IMG]


Where it says 60Hz, in other operating systems I can have up to 72 Hz. 60 Hurts my eyes a little, and I'd like 72 as the monitor and card can support (under the same resolution!).

**Question:**

Can I allow the 72Hz under these settings to be selected, as I can in other operating systems, and if so how can I do that?

*Please keep things simple for me, whilst I'm a technical person Linux is not familiar to me.*

---

### Post by earthpigg on 2010-08-12
I'm assuming you can't simply click on where it says 60 Hz and switch it to 72?

It's possible that nVidia's proprietary Linux drivers simply don't support the switch... in which case there isn't much anyone can do except for an nVidia employee.

---

### Post by RB_ on 2010-08-12
> **earthpigg said:**
> I'm assuming you can't simply click on where it says 60 Hz and switch it to 72?

Correct. 60Hz is in fact the only option, including any lower refresh rates.

> **earthpigg said:**
> It's possible that nVidia's proprietary Linux drivers simply don't  support the switch... in which case there isn't much anyone can do  except for an nVidia employee.[

I was afraid this might be the case, I'm disappointed if it is so, but thank you for your help!

---

### Post by earthpigg on 2010-08-12
if it's a huge deal, you could forego nVidia's drivers altogether (& 3d gaming) and use the system -> preferences -> monitors tool to configure it.

---

### Post by RB_ on 2010-08-12
I tried your idea, and I've received the exact same: 60Hz, and nothing else.

Does it require me to uninstall the NVIDIA driver for this to pick things up? Something like that?

It is a big deal, I have no real heavy graphics requirements. I'm willing to use any solution to give me 1152*864 @ 72Hz. All I want to do is run Eclipse, which runs fine at my current settings, but makes me dizzy on a CRT monitor.

---

### Post by RB_ on 2010-08-13
I've been poking around a bit trying to set this manually with no luck all today.

I tried setting the refresh rates that pop up in my monitors configuration menu (the actual hardware button on front of the monitor), and my system didn't survive when I restarted X (I just got a black screen with a flashing | that allowed me to type, but no commands seemed to do anything).

I also tried to get my monitors ability through [COLOR=Gray]

[I][COLOR=Black]ddcprobe

[/COLOR][/I][COLOR=Black]with no luck, as it gave me an 

[I]Edidfail

[/I]error. I've tried a reinstall of the drivers, made sure they're up to date, and i'm out of ideas.
[/COLOR][/COLOR]

---

