---
title: "[New user] No sound on ubuntu 9.10"
date: 2010-04-19
forum: General Help
---

### Post by Skumleren on 2010-04-19
Hello
I recently installed ubuntu 9.10 on my laptop on top of windows 7. After i installed however, i noticed that there is no sound on the computer at all.
The video on youtube and ubuntu's standard video player also speeds up the video to a speed much greater than x2.
The laptop is a HP pavillion model. I used a couple of the commands i actually know to pull some info, please prompt if you need more.
Btw. I tried hooking the computer up to my (rather manhoodextending) speakerset and tried turning the volume up both on the alsamixer and system-preferences-sound.

Please help if able, i cannot live without my youtube kitten-clips:)

lspci(After some editing)

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

aplay -l (Full list)
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Skumleren on 2010-04-19
A little correction: After turning my speakers all the way up to max, i can hear some faint sounds from the video. But its not even loud enough to hear the voices consitently.
So. Sound, but stupidly low sound.

---

### Post by sandyd on 2010-04-19
try these few things. go into the terminal (applications -> accessories -> terminal) and type in "alsamixer". set the volume (using the up-down keys to change the volume and the left/right keys to navigate.). make sure PCM and MASTER are not muted. if that doesnt work, try ```
sudo pulseaudio -k
```.

---

### Post by Skumleren on 2010-04-19
command gives this response (in red)
E: core-util.c: Home directory /home/martin not ours.
E: main.c: Failed to kill daemon: Permission denied

As for alsamixer everything is unmuted and on full audio including capture devices.

No joy. Sound is still almost undetectable. The only reason i can hear it at all is because im running it through an external amp.

---

### Post by Skumleren on 2010-04-21
Has noone had any similar problems?

ooh and, bump!

---

### Post by Skumleren on 2010-04-28
Come on, exiting mysterious wierd sound problem puzzle available?
Noone?

---

### Post by lidex on 2010-04-28
HP Pavillion? What's the model number? Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Also go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and work through the steps.

---

### Post by Skumleren on 2010-05-10
Model number is PADV62153EO


```
Linux Lappy 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
```

cat
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
```

head
```
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```

---

### Post by Skumleren on 2010-05-10
Oh and the debug link made no difference either:(

---

### Post by lidex on 2010-05-11
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

### Post by lidex on 2010-05-11
Still no joy? Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel
  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by notbitmonk on 2010-05-11
On alsamixer, did you check that externalaudio is muted?  And that the correct hardware and output is selected in Sound preferences?

---

### Post by Skumleren on 2010-05-17
Im sorry to be a buzzkill but  i just upgraded to lynx. Now the sound works!
Well. The pc speakers does not turn off when i plug headphones in, but that will get a different topic since it is a very different problem.

Thanks for all your help though. I almost want to reinstall 9.10 to see if the last suggestion solves it:)

---

