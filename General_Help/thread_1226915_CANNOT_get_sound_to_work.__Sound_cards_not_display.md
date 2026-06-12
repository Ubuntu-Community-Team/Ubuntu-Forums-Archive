---
title: "CANNOT get sound to work.  Sound cards not displayed."
date: 2009-07-30
forum: General Help
---

### Post by danielkabrinski on 2009-07-30
I'm a new Xubuntu user so bare with me... I switched from windows XP...  really don't want to go back...

I have a GeForce6100PM-M2 Mobo, sound blaster audigy, and Logitech Z-10 speakers which are plugged into USB and the onboard sound (the first one that worked for me, temporaraly).  I got the little display to work on the Z-10's...

The sound USED to work on and off for me and it was driving me nuts.  I followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) multiple times and got more than one result.  First the sound worked and I thought I solved the problem, but when I shut the comp down and started back up, it didn't work.  Then I tried other steps and now all I see is the Z-10 USB Speaker option in mixer.  The other cards are not displayed at all even when I do "aplay -l".  BUT, when I do "lspci -v | less" I see these:

```

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Device 2609
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

01:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
        Subsystem: Creative Labs Device 100a
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>
        Kernel modules: snd-ca0106

```

If anyone can take the time to give me a walkthrough it is greatly appreciated.  I've pretty much done all I could do.

---

### Post by danielkabrinski on 2009-07-30
OK.  After using the package manager and reinstalling the kernel? i believe.. and just about everything to do with the sound..  my sound is back on and the drivers are displayed.  

If I shut down my system and start again will I lose my sound?

---

