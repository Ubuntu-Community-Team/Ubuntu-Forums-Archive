---
title: "Media Centre Advice please."
date: 2011-06-16
forum: General Help
---

### Post by elsmandino on 2011-06-16
Hello,

I recently gave Ubuntu 11.04 a go on my lap top (dual boot) and am now a fan of Linux - prior attempts to use it were too difficult, but it has stuck with me.

Anyway, I am currently thinking about where to go from here (in addition to the laptop, I also have an Acer Revo Aspire, a Desktop and an HTPC).

At the moment all computers are running Windows 7 and they are running Mediaportal to stream media from the HTPC.

I am getting a bit fed up with the amount of bloat that Windows has with it and stuff that is generally not needed and it is starting to have a bit of an impact - especially on the server/HTPC.

Now - I originally started using Windows Media Centre but decided to leave it as it was so limited and then I moved on to Mediaportal which I absolutely love, due to the way that it can do so much more - it did take me me a hell of a long time to set up though and understand.

My question really is whether I should install Ubuntu 11.04 (or rather Mythbuntu) on all my computers and be done with Windows (might keep a dual boot on one just in case).

I am very worried about doing this as I am a Newbie to Linux.  In particular, I am very worried about changing from Mediaportal to MythTV - can someone provide an unbiased comparison generally.  Are they largely similar or what are the main differences?  Very importantly, how complicated is MythTV to set up?

Thanks a lot.

---

### Post by unimpressedwithunity on 2011-06-16
I went through this process a couple of years ago and ended up completely abandoning the idea. However, my problem was the lack of available drivers and a non-standard platform - a Sony machine!

As you point out, I also found Windows Media Centre wanting and it simply did would not work for me as an 'in living room under the TV' appliance. The main difficulties were that a) the remote would lock up and it would often take a long time to come out of standby or not at all; b) codec support was lacking. At the time I was working with WMC on XP, but what I have seen so far with the version on Windows 7 does not inspire further confidence.

Overall I thought MythTV looked very promising so I initially I made the decision to spend some time installing Ubuntu and MythTV and eventually moved on to MythBuntu. The latter made setting up easier, but unfortunately could not resolve the issues I encountered, which were primarily driver issues. There was simply no driver firmware that would correctly identify and work with the Sony tuner. The same was true of the built-in irDA sensor for the remote and the driver for my plan-B - a USB TV stick - which could not support digital TV, giving me only analogue tuning. I eventually managed to get an external USB sensor and remote working, but even this did not work properly because the USB device wouldn't work in standby mode - I couldn't wake the system back up - although other functions seemed to work fine.

MythTV is probably more complex to install and set up than WMC although, not being familiar with it, I can't really compare with MediaPortal. I still believe that MythTV would have worked well and the time invested would probably had been well spent had I not had issues with hardware support. From the lessons I learned, I would say that regardless of whether you go for Ubuntu/MythTV or MythBuntu, the first thing to check is whether your tuner, remote control, audio and display hardware are supported. This will probably save a lot of time and frustration. Using MythBuntu might also save some time because the MythTV software is already installed as part of the OS install, but you will still need to configure it and maybe install drivers/firmware. Assuming that your hardware is supported and you are prepared to spend some time setting up  and fiddling, you might stand a good chance of ending up with a working  project.

Unless you don't mind trashing or have the means to back up the Windows installation then, assuming you have the available disk space, by all means use a dual boot setup. Ubuntu co-exists quite well with Windows 7 and you can always revert back should the Ubuntu option not work out as expected.

---

