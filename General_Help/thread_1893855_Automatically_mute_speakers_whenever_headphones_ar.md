---
title: "Automatically mute speakers whenever headphones are connected."
date: 2011-12-11
forum: General Help
---

### Post by HumbleNoob on 2011-12-11
_Confirguration:_

- Gigabyte X58A-UD7 (Azalia codec disabled in BIOS)
- Creative X-Fi Titanium PCI Express (04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 04))
- Corsair 800D case (including audio/usb front panel)
- Ubuntu Oneiric/11.10 64 bit


Dear Ubuntu gurus,

I know this problem has been reported several times on this forum but unfortunately, none of the proposed solutions worked for me.

Here is my problem: whenever I connect headset on the audio front panel, the speakers are not automatically muted. I therefore get sound on both the headphones and speakers which is not desired.

I also noticed that the microphone is somewhat synced with the sound outputted. For example, if I listen some music with Audacious, the microphone input level bar (displayed in system->sound->input) moves according the music (even is the microphone is turned off by a switch on headset).

Could the problem be related to some kind of Alsa profile for my XFi sound card?

Please find hereafter the information provided by alsa-info.sh script:

[http://www.alsa-project.org/db/?f=eaf7100415456fda7d5a9354a4dc0703ec277710](http://www.alsa-project.org/db/?f=eaf7100415456fda7d5a9354a4dc0703ec277710)

For information, all hardware is working fine under Windows. I also tested the Oneiric/headset 64 bit on a laptop configuration and everything was fine. I therefore suspect a configuration problem with my Xfi soundcard.


Many thanks in advance for your assistance!

Kind regards,

---

### Post by Xorlium on 2011-12-11
Hello,

I had the same problem with my Asus G50Vt, but I found a thread that solved it. 

[http://ubuntuforums.org/showthread.php?t=1649956](http://ubuntuforums.org/showthread.php?t=1649956)

I edited the file /etc/modprobe.d/alsa-base.conf and added the following line at the end:
options snd-hda-intel model=auto

If it doesn't work like that, then you can try adding some other line, described in this thread:
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by HumbleNoob on 2011-12-11
Many thanks for your prompt reply, Xorlium,

Unfortunately, adding* options snd-hda-intel model=auto *didn"t solve the problem. It can probably be explained because I do not use the integrated Intel soundcard but an external Creative X-Fi Titanium on PCI Express slot.

To avoid any conflict, I disabled in Bios the integrated Intel sound chip.

But as you pointed out, my problem could be related to some kind of "profile" for Creative X-Fi in alsa-base.conf but I couldn't find that specific profile (or at least try it)

Any suggestion is welcome!

---

