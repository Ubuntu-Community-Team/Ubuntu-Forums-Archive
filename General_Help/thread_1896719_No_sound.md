---
title: "No sound"
date: 2011-12-17
forum: General Help
---

### Post by JimS on 2011-12-17
...
Acer laptop, Extensa 4420-5237
Ubuntu 10.04
Lost sound, first microphone and weeks later speaker.
Got sound with Windoz, both mic and speaker.
Got speaker, but no mic, with live 10.04 CD.
I don't want to lose data, emails, etc. by upgrading.
So --- what to do?
Thanks in advance.
...

---

### Post by Rex Bouwense on 2011-12-17
Is this a dual boot install or a WUBI install?  I'm not sure that it makes a difference.  Anyway see here:
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

---

### Post by JimS on 2011-12-18
...
Thanks for the reply.
I'll check the url.

This is a duel-boot (really triple-boot w/ Puppy & Vista)
Puppy is broken, so I can't check sound.
Vista works and sound is good, both mic and speaker.
...

---

### Post by JimS on 2011-12-20
...
Rex - Thanks for your help.
Reading "Sound Troubleshooter's Guide"
'Your speakers are turned on fully (on AlsaMixer)'
I don't find AlsaMixer

I tried sudo aplay -1 and I get:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Then I ran sudo apt-get install --reinstall libasound2

I'm going to restart and see if sound has returned.

Restarted cold boot and still no sound.
What to do next?
ALSA??
...

---

### Post by JimS on 2011-12-23
...
Did the following 2 commands:

$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Acer Incorporated [ALI] Device 0123
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

$ find /lib/modules/`uname -r` | grep snd
and got lots of .ko files.

I think that alsa is damaged.  
It doesn't show in "Sound Preferences".
Sound Preferences Hardware:  Internal Audio 1 Input Analog Stereo Input
Sound Preferences Input: Internal Audio Analog Stereo - not muted
Sound Preferences Output: Dummy Output Stereo - not muted

No mention of alsa.
The Ubuntu docs say I should have alsa.
Shouldn't it show in Sound Preferences? 
...

---

### Post by JimS on 2012-01-02
...
Found ans in Full Circle Magazine #42 pg 43.
Deleted .pulse folder.
Rebooted and all sound came back.
...

---

### Post by kidknapp on 2012-04-08
Had the same problem this morning on my Dell Inspiron 1440 running 10.04.
Nothing was on mute and the only output option in Sound settings was "Dummy Output Stereo." Went to the home folder and selected show hidden files in View. Found .pulse and deleted the folder. Rebooted and sound works perfect again! Thank You! :guitar:

---

