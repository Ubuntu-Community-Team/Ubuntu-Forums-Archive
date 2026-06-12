---
title: "Volume Maximum on Boot"
date: 2011-07-03
forum: General Help
---

### Post by exiztone on 2011-07-03
I've noticed this problem occurring for several Ubuntu releases. It's very small, but continually annoys me. Maybe someone can confirm it's a bug and then I can submit it as such.

On the default installation of Ubuntu 11.04 (32) the audio volume was too low. Even when I set it at its maximum, I couldn't hear enough through my Logitech headset. For that, I installed alsamixer, opened it, chose "Logitech USB Headset" as the card and increased the "speaker" bar to its highest. This gave me a much higher threshold and is fine.

The problem is that when I boot Ubuntu, the volume is always at its maximum. Unless I adjust the GNOME panel slider a bit left or right, it won't return to normal. Sometimes I forget to do that and get a nasty shock in the ears. :)

Did anyone else come across this? Can it be fixed easily?

---

### Post by Ezraghast on 2011-08-28
Hi exiztone. I had a similar problem on 11.04 and 10.10 and found [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/661885") bug report. Commenting out the 'flat-volumes = no' line of /etc/pulse/daemon.conf did the trick for me:). I'm using a digital output for sound. Hope this helps.

---

### Post by etisdale on 2012-04-22
> **Ezraghast said:**
> Commenting out the 'flat-volumes = no' line of /etc/pulse/daemon.conf did the trick for me:). I'm using a digital output for sound. Hope this helps.

I'm having the same problem (i.e., volume maximized at reboot); unfortunately, commenting out the 'flat-volumes = no' line of /etc/pulse/daemon.conf did not work for me.

---

