---
title: "No sound on Lucid fresh install"
date: 2010-06-23
forum: General Help
---

### Post by Aiffe on 2010-06-23
I tried Intrepid on this computer a few years back, and remember sweating over my computer for days trying to get the sound to work, before eventually giving up and going back to Windows. :( Now I figured I'd give it a second go. 100% fresh install, Lucid Lynx. I was hoping maybe the new version would have fixed whatever I was having trouble with before. No such luck.

Have checked that nothing is muted, in the tray icon and in alsamixer and in a bunch of others. Have made sure that I'm in all the proper groups.

"aplay -l" gives me:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

That looks hopeful, right?

"find /lib/modules/`uname -r` | grep snd" gives me a whole long list of stuff, like it's supposed to.

"lspci -v | less" gives me a whole bunch of stuff, including:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) A
C'97 Audio Controller (rev 03)
        Subsystem: Rioworks Device 203e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

"alsactl init" gives me:

Unknown hardware: "ICH4" "Analog Devices AD1981B" "AC97a:41445374" "0x161f" "0x203e"
Hardware is initialized using a guess method

I throw myself on your mercy, Ubuntu Forums! Please help me.

---

### Post by VH-BIL on 2010-06-23
Try [_***this thread***_]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/72206-intel-82801-ba-bam-ac97-sound-driver.html"). It is the same model sound card as yours.

---

### Post by Aiffe on 2010-06-23
Thanks for the link, I'm looking at that now. I'm not sure I get it, though? The other person's problem was interrupts during boot, which also killed ethernet for them. My ethernet works fine. How can I tell if I'm having the same problem or not?

---

### Post by Aiffe on 2010-06-24
Bumping. I don't understand what I'm supposed to do, and I need more help. Sorry.

---

### Post by qweabab1 on 2010-06-24
I have the same issue

---

### Post by Aiffe on 2010-06-24
FIXED.

Okay, so someone on the IRC channel suggested I reinstall with a working ethernet connection. I did this, and still had no sound, but this time I had sound with the headphones in. (I didn't previously, pretty sure.) That was enough of a clue for me to google for answers.

What finally worked for me was installing and running gnome-alsamixer. Check the external amplifier box, close gnome-alsamixer, run gnome-alsamixer again, and uncheck both external amplifier and line jack sense. I have no idea why this worked, but it did! I definitely have sound now.

qweabab1, I hope this helps you too.

---

