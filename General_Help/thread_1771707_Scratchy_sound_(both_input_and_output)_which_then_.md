---
title: "Scratchy sound (both input and output) which then clears up"
date: 2011-05-30
forum: General Help
---

### Post by Objekt on 2011-05-30
Been having a really strange sound problem recently with my Ubuntu 10.04 install.

Basically, the sound is completely unusable upon login, but clears up within a couple of minutes, without me doing anything in particular.

For example, if I try to watch a video or play music through VLC Media Player right after login, the sound is distorted and scratchy, regardless of volume.

Same deal with the microphone.  Chat apps such as Teamspeak 3 are rendered unusable, because the sound is awful both going out and coming in.

I played with every setting I could find, both in gnome-alsamixer and the Sound Preferences applet, to no avail.  The problem just sort of went away for no apparent reason.

I'd rather sound worked all the time.  It did, until fairly recently.  Can't say when exactly the problem started, just some time in the past few weeks.  Wondering if anyone else has seen this.

[s]None of these problems occur when I run Windows 7[/s], so I'm fairly sure it isn't caused by hardware defects.

FWIW, I use a SoundBlaster Audigy 2 ZS for sound.  My motherboard sound device is an Analog Devices chipset, but I don't use it at all.  I disabled it in BIOS because it doesn't play nicely with Teamspeak 3 and is useless in general.  So Ubuntu doesn't "see" it at all.  But I guess it could still be causing problems somehow.  Any ideas?

eta:
Not sure why I didn't notice it sooner, but the mic is periodically unusable in Windows 7.  It seems there's some problem with using a SoundBlaster Audigy 2 ZS in a 64-bit OS.  There's no pattern to it, but sometimes the sound coming from the mic is choppy and weird-sounding, almost as if I were speaking underwater.  

The takeaway is that my sound hardware now works BETTER under Ubuntu than it does in Windows 7.  Go figure.

---

### Post by Objekt on 2011-06-06
On further inspection - this problem seems to be also related to VLC Media Player.

It's really strange, but if I run VLC for a few seconds right after login, the microphone input is thereafter clear and normal.

VLC has its own playback problems.  Sound output is unbearably scratchy at anything approaching a reasonable volume, and it only gets worse at higher volume.

No idea what's going on.  I had no sound problems whatsoever in Ubuntu as recently as a few months ago.

---

### Post by jcoles on 2011-06-10
Try selecting Tools > Codec Information. That instantly clears up the sound for me.

---

### Post by jcoles on 2011-06-10
Here's a fix I found in another thread:

[http://ubuntuforums.org/showpost.php?p=9948061&postcount=2]("http://ubuntuforums.org/showpost.php?p=9948061&postcount=2")

---

### Post by Objekt on 2011-06-22
Several reboots later, it seems that the problem is fixed.  Haven't had scratchy VLC Media Player output or unusable mic input since I made the change in the thread you linked.  Thanks!

---

