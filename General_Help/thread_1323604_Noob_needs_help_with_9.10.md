---
title: "Noob needs help with 9.10"
date: 2009-11-11
forum: General Help
---

### Post by hosinfefer on 2009-11-11
Hi Guys

First off I am a noob. I am trying ubuntu again after a failed attempt. I have a few questions regarding 9.10 i just installed.

My HD is a 60gb ssd ocz vertex. Is there a way to run ocz's wiper.exe to help keep the drive clean?

I cant play any you tube videos..talks about having java off or downloading flashplay (no clue how to do either)

I have a dlink dns 323 with raid 1 1tb drives. Can i map drive to this and how do i do so...ip is 192.168.0.199

I also have no sound. I have a single spdif plug (digital?) goign into my home auto receiver. How can I get this working?


My hardware is a core i7920
6gb mem and an asus p6tdul v2 MB
Thanks for all your help

---

### Post by hosinfefer on 2009-11-11
ok I got the nas and youtube sorted. still need help with sounds and info on how to keep the ssd working fast.

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
For mapping a network drive I assume you want to access it on your network: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Not sure what that wiper.exe is but you say you want to keep the drive tidy. System>Administration>Computer Janitor. You can also run some windows apps using wine (free) and Cedega (paid version). I use wine to run all kinds of games and some Office stuff. [www.winehq.org](www.winehq.org) has an app database that can show you what will run in wine (has been tested anyway). If you want to try your wiper.exe then install wine, open a terminal, run winecfg and check out the settings... make sure it sees all your drives and sound works and what not, cd to where wiper.exe is and type "wine wiper.exe" and it may or may not work. If not there are many programs out there that will do this.

Sound is an ongoing issue but I've gotten it to work on every system I've installed Linux on. This [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) may help.

Google is your friend. most of the info I gave you here I got from a simple google search using your words (copy and paste). Just a little FYI

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
Not to insult your intelligence, but sound is muted by default in 9.10. It took me several minutes of searching to find that myself, so do double check!

---

### Post by hosinfefer on 2009-11-12
Yes i did find the sound was turned off. I have a set of wireless usb logitech headset that is playing sound fine. Just cant get my onbaord to work. Kinda sad walking around the house with headphones because you 1000w surr. sound wont work :(. The wiper.exe is a program for SSD hard drives to keep them from degrading over time. I am not sure the janitor program will do the same thing. I will have to google more :)

Thanks guys

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
I have heard of people needing to switch to ALSA audio, but sound worked fine for me, so you'll need to do some searching to confirm fixes.

---

### Post by hosinfefer on 2009-11-12
I am not even sure what ALSA is. Are you running an asus mb with onbaord sound?

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
Yes I am, but I did an upgrade from 9.04 instead of a clean install... I don't know if that made any difference.

---

### Post by hosinfefer on 2009-11-12
ok I am stuck on step 3 of the sound guide. all i get when i click on the link is this



Index of /alsa-doc

Icon  Name                    Last modified      Size  Description[DIR] Parent Directory                             -   
[DIR] alsa-lib/               09-Sep-2009 14:37    -   

Apache/2.2.3 (Linux/SUSE) Server at [www.alsa-project.org](www.alsa-project.org) Port 80

I went into the alsa-lib directory and dont see what it is i am looking for. Anyone help?

---

### Post by hosinfefer on 2009-11-12
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



this is what i get when i do step 2

---

### Post by hosinfefer on 2009-11-12
ok so I plugged in a new cable from the analog sound to 2 rca analog plugs and set up to an analog signal and got sound no problem. Does digital sound not work in ubuntu?

---

