---
title: "Headphones and Speakers?"
date: 2010-04-05
forum: General Help
---

### Post by flierdude on 2010-04-05
So I have looked and looked and was unable to find a helpful, successful thread on this out of the few that I looked at.

It's simple, when my headphones are plugged into my computer, the sound comes from both the speakers AND the headphones. 

I just want the sound from the headphones if they are plugged in.

Please excuse me if I may have missed a thread that already has the answer to this.

Thanks!

~Flierdude

---

### Post by loell on 2010-04-05
this is somehow common on intel based sound devices,

to know the exact device, try this command, then copy paste it here.

```
lspci -v|grep Audio
```

---

### Post by flierdude on 2010-04-05
> **loell said:**
> this is somehow common on intel based sound devices,

to know the exact device, try this command, then copy paste it here.

```
lspci -v|grep Audio
```

Alrighty, here was my computers response to the command you gave me:

                          > 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

---

### Post by loell on 2010-04-06
hi, another question, is this a laptop? If so, pls state the brand and model.

---

### Post by cryptotheslow on 2010-04-06
Interesting - I have been wondering how to achieve the same thing myself (have the speakers cut when headphones are attached).

Same chipset by the look of it:

xxxxxxxx@gt-desktop:~$ lspci -v|grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

In my case it is the ATI SB600 chipset on an Asus M2A-VM motherboard (desktop not laptop). In the BIOS I have the front panel type set to AC97 rather than HD Audio. Headphones jack into the front panel, speakers into the usual rear output.

Apparently this chipset will "Support Jack-Sensing, Enumeration and Jack-Retasking technology" - which kind of worked under Win2K once the driver suite was loaded up, although a little flaky.

I'm guessing now - but surely PulseAudio will somehow need to be aware that the headphones have been jacked in and automagically mute the Speaker output at the rear. Is the jack-sensing supported at all in the Linux/Ubuntu driver for the ATI SB600? How could one find out?

---

### Post by loell on 2010-04-06
sometimes these steps can work.. it could auto-switch headphones and speakers.

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")


Though I guess, it is model dependent.

---

### Post by cryptotheslow on 2010-04-06
I got as far as looking at /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz to find a relevant model but nothing seems to really suit.

I appear to have a Realtek ALC883 (as per the mobo manual and Ubuntu has selected the right codec).

I have 3 jacks rear, 2 front and the board does have SPDIF out capability, so from the list below.... who knows?

I'm inclined not to just start randomly trying different model options, from past experience I'm quite good at totally breaking the sound by messing around with it. I think because I don't actually really understand how the sound system hangs together and I end up confused between OSS, ALSA and Pulse.

ALC883/888
==========
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire    Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  medion    Medion Laptops
  medion-md2    Medion MD2
  targa-dig    Targa/MSI
  targa-2ch-dig    Targs/MSI with 2-channel
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e    Lenovo 101E
  lenovo-nb0763    Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66    Haier W66
  3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell    Dell machines with 6stack (Inspiron 530)
  mitac        Mitac 8252D
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  auto        auto-config reading BIOS (default)

---

### Post by flierdude on 2010-04-06
Ya I'm using a laptop. It's a Gateway NV Series.

It's running on an AMD Athlon X2 64 with an ATI Radeon mobile GFX Card.

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

