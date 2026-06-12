---
title: "Ubuntu 9.04 and no sound."
date: 2011-10-30
forum: General Help
---

### Post by LeDechaine on 2011-10-30
Hello again.

Yes, i'm still using linux (I guess I was a masochist in another life).

I've already used the ".asoundrc" file to set my Audigy 2 soundcard to only output sound through the optical output. Now, I don't want that anymore, and i'm back in command line hell.

**.asoundrc file**
was:
```
pcm.!default iec958:Audigy2
```
and was working #1 with speakers with optical inputs.
file is now:
```
pcm.!default front:Audigy2
```
and nothing works.

```
$ **aplay -L**
front:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    Audigy 2 ZS [2001], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture
```

```
[B]$ aplay -D front:Audigy2 test.wav
$ aplay -D hw:0,0 test.wav[/B]
```
those commands both says "playing file etc". but they're lying.
no output from the speakers. and yes, they're connected.

i'm also using ubuntu 7.10 (dual boot), and the sound works. seems like to have something working with ubuntu, you have to downgrade.

how to fix this?
And don't tell me to upgrade. I'm here because i need a mechanic, not a car reseller.

---

### Post by WasMeHere on 2011-10-30
Hello LeDechaine,

Why are you running such old Ubuntu versions? The security updates have finished long ago. Have you tried some newer version, for example Ubuntu 10.04 LTS or Ubuntu 11.04?

Is the problem that newer versions will not cooperate with your hardware, or is it simply that until now you have been happy with Ubuntu 9.04 (and 7.10)? By the way, my very first Ubuntu was 7.10.

Instead of frustration, have fun finding out about Ubuntu :-)
Olle

---

### Post by LeDechaine on 2011-10-30
> **LeDechaine said:**
> And don't tell me to upgrade. I'm here because i need a mechanic, not a car reseller.

Linux is not windows. Linux takes 3 years to configure as you want it to be and by the time you've finished everyone tells you it's time to upgrade because of "security upgrades" on an operating system "sealed" with no open ports by default and "sealed" again because you download everything from the official repositories. I'll upgrade in 10 years.

---

### Post by LeDechaine on 2011-10-30
Anyone?

---

### Post by WasMeHere on 2011-10-30
This link should make you happy (a step the the right direction)
[[COLOR="RoyalBlue"]_http://ubuntu.se/threads/18846-Ubuntu-12.04-LTS-Desktop-To-Be-Supported-for-Five-Years_[/COLOR]]("http://ubuntu.se/threads/18846-Ubuntu-12.04-LTS-Desktop-To-Be-Supported-for-Five-Years")
Maybe this link would be interesting for you
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1859702_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859702")

I understand your point, but it will be difficult, if you need some new program or new feature in an existing program or new hardware, that is not supported by your old system. I don't know how to help you with the problems you have today. *I hope someone who knows how to do it will read this thread.*

Good luck
Olle

---

### Post by LeDechaine on 2011-11-02
boing.

---

### Post by WasMeHere on 2011-11-09
> **LeDechaine said:**
> Linux is not windows. Linux takes 3 years to configure as you want it to be and by the time you've finished everyone tells you it's time to upgrade because of "security upgrades" on an operating system "sealed" with no open ports by default and "sealed" again because you download everything from the official repositories. I'll upgrade in 10 years.

Yes I understand because I used to think so too. But I have been convinced that ***I need at least the security updates***, and it is almost impossible to do without upgrading to a supported version (now Ubuntu 10.04 LTS). If you think Linux is perfectly safe, please read this wiki under construction
[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

I have found that more things work out of the box with 10.04, for example drivers for wireless LAN, and there are improved versions of several software packages (but of course these are not necessary).

And I promise that I wish there is ***[COLOR="Red"]someone around who can help you with the audio[/COLOR]***, but if you can't fix it yourself and won't get help, please consider switching to a supported version or upgrading! It might even run out of the box from a live CD or USB drive, or you make some minor tweaks in the audio settings.

Have fun finding out :-)
Olle

---

### Post by LeDechaine on 2011-11-09
Yeah, and as if it was not enough, by trying to fix this problem, now the iec958 (optical) output of my sound card now only outputs the LEFT audio tracks*. Yeah, you saw that right. It's not even MONO. It's stereo, but with the missing RIGHT track. And what have I done for this? I've installed programs that maybe could fix the first problem, and uninstalled them after.

I swear linux is so irrational that i'm having a hard time believing that it's actually PEOPLE who are coding it.

---

