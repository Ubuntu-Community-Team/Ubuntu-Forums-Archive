---
title: "No sound after reboot from windows"
date: 2011-01-05
forum: General Help
---

### Post by monkey21stc on 2011-01-05
Hi all

I run windows XP sp3 and Ubuntu 10.10 on an ASUS EeePC 1000HE (I know its a pretty old model). I have been facing this problem ever since installing Ubuntu side by side with Win (*not WUBI*). Every time I switch to Ubuntu after a reboot from windows, I get no sound from Ubuntu, the sound driver appears to be working fine, but there is just no audio output. This problem does not occur if I do a clean boot to Ubuntu after shutting down Windows, I am wondering if anyone has experienced similar issues and is willing to help.

Thanks! Your help is greatly appreciated!

---

### Post by happyhamster on 2011-01-05
Could be that the soundcard is still claimed by the previous OS. Does shutting down windows produce a shutdown tune? Disabling that sound might do the trick.

In XP: go to Start -> Control Panel -> Sounds and Audio Devices -> Sound tab -> Program Events -> Exit Windows. Instead of "Windows XP Shutdown.wav" select "None". Then choose Apply and Ok. Reboot into Ubuntu. 

Good luck.

---

### Post by monkey21stc on 2011-01-05
Hi happyhamster,

Unfortunately, your solution did not help. I am pretty sure the sound card is working as PulseAudio Volume Meter (Playback) did produce output whenever I play a song, it's just that there is no sound coming out from the speakers. I believe like what you said, windows has claimed the soundcard, and therefore fixing that would probably solve my problem. 

Thanks!

---

### Post by GWBouge on 2011-01-11
Similar issue here ...

Ubuntu 10.10 using ALSA, Windows 7, both 64-bit, Sound Blaster X-Fi

Only been dual-booting for about a month (just can't kick those gaming habits  XoD ), and everything worked fine for the first week or so.  Windows purely for games, Ubuntu for everything else.  For whatever reason, the sound stopped working after rebooting from Windows to Ubuntu, and the only resolution I've found is just to keep rebooting until it decides to work.  However, it's been getting worse and worse ... first just had to reboot twice, then three times ... just now I gave up after 11 or 12 restarts and I'm back into Windows.

Starting up VLC or Audacious gives a 'failure to initialize sound device' message, and on one of those dozen recent reboots a lot of errors were displayed.  I don't remember exactly what it said, but something along the lines of:

```
worker [devd] did not receive message (connection refused) -1.  kill it.
```

I could deal with a couple restarts, but this is getting *insanely* aggravating.

---

### Post by West201 on 2011-01-11
I have the exact same issue. Please let me know if you find a solution :)

---

### Post by nathan28 on 2011-01-13
I'm getting a similar issue in 10.04 64-bit (also a dual-boot), but without even loading booting into windows. Killall pulseaudio will *sometimes* fix the issue, but not ATM.

This was also after a hard reboot, too, as in, no power. I have to wonder if this isn't a hardware issue tied to those useless volume controls on the laptop's keyboard. I wish there was a way to disable them without a soldering iron.

---

### Post by GWBouge on 2011-01-15
> **nathan28 said:**
> I'm getting a similar issue in 10.04 64-bit (also a dual-boot), but without even loading booting into windows. Killall pulseaudio will *sometimes* fix the issue, but not ATM.

This was also after a hard reboot, too, as in, no power. I have to wonder if this isn't a hardware issue tied to those useless volume controls on the laptop's keyboard. I wish there was a way to disable them without a soldering iron.

I just noticed this as well.  Typically I don't reboot unless I'm switching OS's, but I had somewhere to go for a couple days, so I shut it down from Ubuntu, powered off, come back two days later, turn it on, no sound.  =o(

Now, I just got whatever updates came out over the past couple days, required restart (kernel upgrade), and I have sound ... but I don't really want to restart it again to find out if it was just a fluke, lol.

---

### Post by GWBouge on 2011-01-26
... anybody?  anything?

I can't seem to find anything worthwhile in the logs, though I'm not really sure what I'm looking for.  Even disabling the card in Windows' Device Manager before restarting doesn't 'free' the card.

Haven't been able to get sound in Ubuntu at all for the past few days, and an OS without sound is pretty much worthless to me.  So aggravating  =o(

---

### Post by mad_dogs_bite on 2011-01-26
I have the exact same problem, also on an EeePC 1000HE with Windows XP SP3 and Ubuntu 10.10. Sound works fine if I do a complete shutdown of Windows, and then boot Ubuntu, but if I just reboot from Windows into Ubuntu I don't have sound, and then it takes an arbitrary number of reboots to get it working again...

---

### Post by rocthrttle on 2011-01-26
i looked up a EeePC 1000HE and it's an older laptop....two questions pop into mind. 
1: if a hard reboot works then just go with that. if it works, it works.
2: why havent you switched completely to ubuntu? 

is there something that ubuntu wont do for you? if not i would suggest you should just make the jump. if you have tasks that you cannot do without windows we would like to know. the list of windows only tasks is getting shorter and shorter.

ubuntu will be faster, cheaper and more secure, for a longer term.

faster: boot times, program load times, programs are easier to find and install, no anti-virus programs sucking the life out of your machine, no wasted time or energy running scans, updates integrate fast(usually without a reboot,

cheaper: your older/slower hardware will die before your machine feels slow, programs are free, your not wasting time and electric on antivirus scans*, the OS is free,

more secure:
i had an uncle go one year before geeksquad wiped his drive(he didnt call me to help him) due to malware. ubuntu is malware proof. it's also really easy to backup and keep your settings,bookmarks and data. dejadup is the program for that. similar programs run about $50. 

think about what you really need windows for and start digging for replacements in ubuntu. even if you have programs that you must have there is WINE. gamers should also try playonlinux.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by IWantFroyo on 2011-01-26
Check your Sound-Output settings. There should be a drop down bar there. Go through them until you might find something that works.
Or even simpler. Is your sound at 100%? When I installed Ubuntu on this computer, it was at an inaudible level.

---

### Post by GWBouge on 2011-01-26
rocthrttle - For me, the only reason Windows is installed (again ...) is better support for my G27 racing wheel and to play iRacing.  WINE is an awesome tool, but it doesn't work with everything.  Everything else I do (code, media, most other games, web/email, etc etc) I do with Ubuntu due to most of the reasons you mentioned.

IWantFroyo - I'm using ALSA and jackd, everything worked fine before I went back to dual-booting.  Reason:  I couldn't get PulseAudio to split outputs from separate programs (ex:  Skype through my headset with the TV/Music playing through my speakers), and PulseAudio likes to produce a high-pitch distortion at anything but full volume with my Sound Blaster X-Fi.

I also have on-board sound, but seems to lack whatever mixing capabilities it needs to play sound from multiple sources at the same time.  I have it disabled in the BIOS.

Opening VLC I get:

```
VLC failed to initialize your sound output device (if any).
Please update alsa-lib to version 1.0.23-2-g8d80d5f or higher to try to fix this issue.
```

My libasound2 is at 1.0.23-1ubuntu2.1 ... which seems to be the most recent in the repo's.  I don't see 'alsa-lib'.  Audacious just keeps skipping songs, and trying to Test in gstreamer-properties gives me:

```
'ALSA — Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(687): gst_alsasink_open (): /GstPipeline:pipeline10/GstAlsaSink:alsasink11:
Playback open error on device 'default': No such file or directory]
```

Now, I can select certain sets of speakers to work, and they produce the test tone, such as 'Front' or 'Surround', but 'Default' (which used to be my entire 5.1 system) doesn't work.

Note, again, everything was working fine when I only had Ubuntu installed, and worked fine for a week or so after I had set up dual-boot.  Then I noticed I had to restart a couple times to get sound back ... then a few ... now the only time I seem to get sound is after Ubuntu gets an update that requires a restart (such as a kernel upgrade).  A complete shut down doesn't work for me  =o\

---

### Post by monkey21stc on 2011-01-28
I use windows sometimes when my battery is running low and when I don't have my charger with me. Windows tend to handle battery usage better as compared to ubuntu. I can see that that this could be an issue with 1000he user so there is a high probability that its related to the sound card,   mad_dog_bites: have you checked whether pulseaudio shows any virtual output?

---

### Post by biloxiparish on 2011-03-04
I have the same netbook with the same problem. Anyone have a fix for it yet?

---

### Post by GWBouge on 2011-03-06
I'm not sure if this will help the OP or not (don't know anything about that netbook), but after a bit of observation I realized that the order of my sound devices were being assigned somewhat random at boot.  Following the advice [here]("http://ubuntuforums.org/showthread.php?t=922860"), I forced the desired default output device to always be the first device, and now ALSA and jackd are happy, therefore everything else is happy.

---

### Post by landeel on 2011-04-30
I have a Sony Vaio VPC-YB15AB and I have the same issue. When I reboot from Windows to Linux I have absolutely no sound.

No matter how many times I reboot again, still no sound. Restarting alsa doesn't help either.

I have found only one workaround; if I suspend the computer, and then resume (in Ubuntu), sound works again.

But still, very annoying.

Windows is either uploading some firmware to the sound card, or setting some flag alsa can't unset.

---

