---
title: "installed kubuntu, sound and mic not working"
date: 2006-03-01
forum: General Help
---

### Post by harty83 on 2006-03-01
Howdy,

So I did a install from the Kubuntu 5.10 install cd on my laptop.  Before (when I installed from Ubuntu) my sound worked fine, but now it does not.   I've checked alsamixer and my sound card and mic are unmuted.  I've checked kmix and again sound is unmuted.  I've checked lspci and my sound card is listed.  I'm not for sure where to go from here.  I've looked at kcontrol and my sound system is enabled.  It has the option of selecting Autodetect, OSS, ESD, ALSA, and a couple others.  I know that in Ubuntu I had alsa.  I made sure that alsa is selected as my sound system (also tried autodetect) but no go.  Alsa is starting up at system boot.  

What do I do?

Here is my card:

```

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 015f
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

```

While I'm talking about sound, what is people's personal/professional opinin on what sound system to use?  I'm not familar with OSS, ESD, or really ALSA.  Thanks!

---

### Post by metwo on 2006-03-01
Do you get any sound on KDE startup? Which apps have you tried playing sounds with?

---

### Post by rudiz on 2006-03-01
In terminal:

alsamixer

---

### Post by harty83 on 2006-03-01
I tried alsamixer from terminal.

Figured it out.  I had to have "External amplifier" checked in kmix.

Installed Jack and I think that fixed my mic problem.

---

### Post by cmrugby on 2006-03-01
i had the same problem when i installed kde on ubuntu, im not sure how in kde but in gnome go to system>Preferences>Multimedia Systems Selector.  I had to change it to ESD and it worked

---

### Post by Talikar on 2006-03-01
[QUOTE=cmrugby]i had the same problem when i installed kde on ubuntu, im not sure how in kde but in gnome go to system>Preferences>Multimedia Systems Selector. I had to change it to ESD and it worked[/QUOTE] Don't suppose anyone could please point me in the direction of the kernel source of 2.6.12.16.1 ? It's not in my repository for Adept (not sure why?). Ubuntu is made simple, but, they make it slightly more difficult to manually do anything. Which is a pain, because, I'd have my audio 100% working if I could just go get the drivers from ALSA's site and install them manually (which I did under Yoper). Back to searching for the kernel source I go lol.

Oops, nevermind, downloading the "Headers" pack from the repo worked, not sure why I didn't try that prior. Thanks anyway, have fun all. :)

---

