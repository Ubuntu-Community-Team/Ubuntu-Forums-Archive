---
title: "No sound from AD1986A"
date: 2006-04-12
forum: General Help
---

### Post by TripleE on 2006-04-12
I have a Asus A8S-X with a ADI AD1986A SoundMAX on-board sound card.  I just installed ubuntu32 (breezy), but the sound does not work.  When I look at the volume control, it shows 2 sound devices: “0: SiS SI7012 (alsa mixer)” and “1: Analog Devices AD1986 (oss mixer)”.  The motherboard came with linux alsa sound drivers (see below), but it does not seem to let me compile the drivers per the instructions that came with the drivers. There is no configure file to run.  I do have g++ installed.

I have Breezy32 triple booted with Dapper64 and Windows XP32.  Windows is the only OS that plays sound.  I would like to get rid of the Windows partition.  Please help.

[http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8S-X/Linux_ADI_Audio.zip](http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8S-X/Linux_ADI_Audio.zip)

_____________
Thanks,
TripleE

AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16

---

### Post by TripleE on 2006-04-12
I kept playing with the settings for the SiS SI7012 (Alsa Mixer) sound device, and I found that the Master Surround and PCM control the volume.  I unmuted them and adjusted the settings.  Now it works great.  Chalk one up to user error:) 

_____________
Thanks,
TripleE

AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16

---

### Post by ulask on 2008-03-07
hei,
I have just install ubuntu on my computer and &#305; m begineer,,
my sound card is SoundMax AD1986 High Definition Audio driver and I can not hear anything :(
Also I cant install my nvidia graphic card too even I want to install beryl on my ubuntu,  but here is not the place for that I know,,
How can I fix it,,
My computer is packard bell,
I hope somebody can help me and send a message,,
tahnx  a lot :KS
ULAS

---

