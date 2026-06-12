---
title: "Alsamixer Difficulties [precise]"
date: 2012-04-26
forum: General Help
---

### Post by IWantFroyo on 2012-04-26
So everything was going fine with Precise Pangolin until I tried to listen to some music.

I plug my headphones in, turn on the music, nothing goes through the headphones. I take off the headphones, and find the music is playing through my computer speakers.
:p

Anyways, I checked alsamixer, and noticed something interesting. Whenever I change the volume with the notification panel, it turns Speaker and PCM all the way up. Tinkering doesn't change anything, because it all goes back to its earlier configuration.

Output for: lspci -v | grep -A7 -i "audio"
```
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fda0
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
    Subsystem: Toshiba America Info Systems Device fda0
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at ff410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```Thanks!

---

### Post by kmas on 2012-04-28
> **IWantFroyo said:**
> So everything was going fine with Precise Pangolin until I tried to listen to some music.

I plug my headphones in, turn on the music, nothing goes through the headphones. I take off the headphones, and find the music is playing through my computer speakers.
:p

Anyways, I checked alsamixer, and noticed something interesting. Whenever I change the volume with the notification panel, it turns Speaker and PCM all the way up. Tinkering doesn't change anything, because it all goes back to its earlier configuration.

Output for: lspci -v | grep -A7 -i "audio"
```
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fda0
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at ff700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
    Subsystem: Toshiba America Info Systems Device fda0
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at ff410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```Thanks!

you have to umute the speakers by hovering over it and pressing m... The problem I have however is how to make those settings stick everytime I unplug and plug in my headset..

---

### Post by IWantFroyo on 2012-04-28
I've done that. The problem is the settings revert after I try to change the volume via the icon.

---

### Post by IWantFroyo on 2012-04-30
24 hour bump.

---

### Post by cortman on 2012-04-30
Hi Iwantfroyo, how goes?

I had a similar problem with Lubuntu and Xubuntu (11.10 and 12.04) on my Acer netbook. I assume you're using stock Ubuntu?
Sounds to me like a conflict between the volume manager applet and alsa. Have you tried a different volume manager program (just a stab in the dark)?

---

### Post by IWantFroyo on 2012-05-01
I looked into it, cortman, but didn't find anything. Ubuntu is pretty limited, having, as far as I could tell, only alsamixer available.

---

### Post by IWantFroyo on 2012-05-03
Kabump.

---

### Post by fkurniaaziz on 2012-05-04
check you codec via terminal

cat /proc/asound/card0/codec* | grep Codec

and find the same codec in [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txthttp://"). there is a model according to your codec

and add the following to your /etc/modprobe.d/alsa-base.conf
snd-hda-intel model="model"

change "model" to your model. and restart your laptop

it works for me

---

### Post by IWantFroyo on 2012-05-08
Nevermind. A switch to gnome-shell fixed it all. :p

---

### Post by jcoles on 2012-05-13
> **fkurniaaziz said:**
> check you codec via terminal

cat /proc/asound/card0/codec* | grep Codec

and find the same codec in [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txthttp://"). there is a model according to your codec

and add the following to your /etc/modprobe.d/alsa-base.conf
snd-hda-intel model="model"

change "model" to your model. and restart your laptop

it works for me

Should the line begin with "options"? Most other lines in the file do. 
Is the position in the file at all critical? Beginning, end?

Thanks.

---

