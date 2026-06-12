---
title: "TeamSpeak (used with aoss)/ALSA problem - Stuttering, clicking quality"
date: 2010-03-06
forum: General Help
---

### Post by XtremeGamer99 on 2010-03-06
Hello,

I use TS with my MMO (which runs nearly flawlessly via WINE). I'm currently using the 32 bit teamspeak2, and it starts and works just fine (I run it via `aoss`). Except the sound quality. This is a problem that seems to plague the Linux client, which is the reason why so many people run the windows client through WINE. I can't run it through wine due to other circumstances (PTT key not working, other issues).

I've looked around, and came across [this](http://ubuntuforums.org/showthread.php?t=546715) post which links to [this](http://ubuntuforums.org/showpost.php?p=4869171&postcount=16) post. It seems that if you increase the sound buffer, it help, if not completely eliminates, the stuttering.

However, I can't get it to work at all. I copied and pasted what is there, and when I start up TS it doesn't detect my sound device or mic. I tried to edit it to fit my machine via ALSA wikis and whatnot, but I'm really flying blind here as I've never worked with any audio stuff and it's just going over my head, and I can't seem to get a configuration that even works, let alone fixes the problem.

Can anyone help me? I'm willing to provide information about my computer via /proc/, but I don't know where to find info regarding the sound card and whatnot, or even what kind of info is relavent.

BTW, it's an on-board sound card.
BTW#2, I'm not on ubuntu, I'm on Arch Linux w/ KDE4. Figured I'd ask here due to the huge community and for the fact that Linux is Linux either way. =P

Thanks to anybody that can help. =)

This might be some relavent info:
```
$ sudo lshw
       *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f9ff8000-f9ffbfff
$ cat /proc/asound/pcm
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 3
00-01: AD198x Digital : AD198x Digital : playback 1 : capture 1
```
EDIT: I've noticed that sometime the sound is crystal clear, when other times it's choppy and clicky... I dunno. I'm still googling the problem, and I'm still unable to edit ~/.asoundrc to include anything without TS not able to find an audio device.

EDIT: Here's some more info (found a nifty ALSA script): [http://www.alsa-project.org/db/?f=b63b441ed4b7ba7a9c98cf001d952aa35f77e455](http://www.alsa-project.org/db/?f=b63b441ed4b7ba7a9c98cf001d952aa35f77e455)

---

### Post by XtremeGamer99 on 2010-03-06
This forums moves too fast. Maybe I should have put this in another forum. >_>

---

### Post by XtremeGamer99 on 2010-03-10
Last bump

---

