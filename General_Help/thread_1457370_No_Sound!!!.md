---
title: "No Sound!!!"
date: 2010-04-18
forum: General Help
---

### Post by Cubhicbu on 2010-04-18
I turned on my computer, and there's no sound. I've tried reinstalling Ubuntu Restricted Formats, but it doesn't change anything, I've updated, and I've used the Repair Mode.

I know there isn't a problem with my hardware, because I just checked it on my Windows (dual-boot system) OS.

---

### Post by itiswhatitis on 2010-04-18
Is this a new Ubuntu install?  Was the sound working in Ubuntu previously?

Have you added any new hardware?  Maybe USB Headphones?

---

### Post by Cubhicbu on 2010-04-18
It's Ubuntu 9.10. I've had it for a few days, and the sound worked. No, I haven't installed any new hardware.

---

### Post by cogier on 2010-04-18
It sounds like something has been muted. Right click on the speaker icon and select preferences and make sure nothing is muted.

It sounds a silly thing but I have seen it a few times. It's worth checking.

---

### Post by Cubhicbu on 2010-04-18
That was the first thing that I checked lol. It's not muted.

---

### Post by Cubhicbu on 2010-04-18
And it's not just the music that's not playing--it won't even play the login sound.

---

### Post by itiswhatitis on 2010-04-18
Okay - let's get specifics here.

Can you post screenshots of your Sound Preferences?

Open a terminal and type:
```
sudo aplay -l
```and paste the results into your reply.  

Same Terminal

```
lspci -v |grep Audio
```

and paste the results

That will help figure out what's going on.

---

### Post by garvinrick4 on 2010-04-18
Mute Fix: If every time when you boot up and are muted. Comment this line out in root and save.

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore


Sound fix if nothing is muted does not work:Code:


sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio

If those do not work this is next step; 

[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by garvinrick4 on 2010-04-18
> **Cubhicbu said:**
> I turned on my computer, and there's no sound. I've tried reinstalling Ubuntu Restricted Formats, but it doesn't change anything, I've updated, and I've used the Repair Mode.

I know there isn't a problem with my hardware, because I just checked it on my Windows (dual-boot system) OS.
No big deal everyone has there sound fixes as time go's by. I have not had a sound problem since installing 9.10 and 4 or 5 different times on flash drives. They were all fixed in a couple of minutes. Sometimes hardware and drivers just take a little kick in the ***.

Save the fixes I gave you somewhere just to have them.

---

### Post by lidex on 2010-04-18
If that was the first time you rebooted after installing karmic, chances are you're loading the wrong kernel, if an upgrade. In any event, go to this page and work through the known issues with karmic audio:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

