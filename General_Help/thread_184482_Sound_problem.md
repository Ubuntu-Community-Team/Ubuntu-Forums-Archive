---
title: "Sound problem"
date: 2006-05-30
forum: General Help
---

### Post by nugglets on 2006-05-30
Posted this in the newbie forum too, but figured it couldnt hurt to put it here as well. If thats not cool, delete it please.. and sorry.

Sorry, I see there are a few other sound card threads with out replies, but none of them are for my sound card so I didnt want to thread jack someone.

Anyways, I have an ATI AC97 sound card that isnt working properly. Checked the alsamixer and all the typical things that every sound thread says to check, but nothing works still. Also tried checking out the alsa site, but i cant even use mkdir and cant get the root account working to save my life so that didnt get very far. Obviously I am a total linux noob, but I would say I am pretty computer saavy in every other respect(programming, hardware, windoze). Please help!

lspci:

> 
gabis@razorlives:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5951 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:03:07.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


lsmod | grep snd:
> 
snd_atiixp 18912 1
snd_ac97_codec 72188 1 snd_atiixp
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer 21764 1 snd_pcm
snd 48644 8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_os s,snd_pcm,snd_timer
soundcore 9184 1 snd
snd_page_alloc 10120 2 snd_atiixp,snd_pcm


Sorry, Im still too newb to decipher what to do from here. Though I can tell that it seems my sound card isnt installed entirely, looks like half the entries are right and half say they arent detecting it. Were this windoze, I would know exactly what to do.. but its not so help meh learn the ways Thanks!

---

