---
title: "crackling/buzzing sound when playing videos"
date: 2009-07-04
forum: General Help
---

### Post by abelthorne on 2009-07-04
Hello,
I have a problem since a few days : when I play video files with Totem or MPlayer, I get a loud crackling/buzzing sound (not sure of the exact term in english).
I get good sound :
- when listening to a MP3 with Totem
- when viewing the same videos with VLC
- when viewing or listening to sound on the web (i.e. YouTube)
- in most of the games I play (although I get strange sound in some ; guess it has to do with SDL / Pulseaudio issues)

I thought the problem was related to GStreamer (as it happens with Totem and not with VLC) but I tried to remove totem-gstreamer and install totem-wine insted with no change.

Any idea ? Has someone encountered the same problem recently that would indicate it come from an update ?

---

### Post by moster on 2009-07-04
You can wait here to Jesus Christ come back to us and answer all of your questions including this one, or you can post result of ```
aplay -l
``` in terminal and somebody from forum will answer you.

Nobody knows what soundcard you have!

---

### Post by abelthorne on 2009-07-05
**aplay -l** gives the following :
```
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : STAC92xx Digital [STAC92xx Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
```

I use PulseAudio (from Jaunty repositories, no specific config).

---

### Post by abelthorne on 2009-07-05
There's something else I've encountered today that may be a hint : while playing a game through Wine, I had the same sound problems than in Totem/Mplayer. After changing sound settings from ALSA to OSS in winecfg, they are gone and the sound plays fine.

I guess my problems are somewhat related to ALSA but I don't know how.

---

### Post by moster on 2009-07-05
Ok... first try this quick fix 1 that will maybe help you

1. Enter in terminal "gnome-volume-control" and remove in tab "switches" check-box "headphones". Put few problematic songs/videos in playlist and investigate now.

2. Many players in ubuntu except mplayer based (smplayer, mplayer...) and VLC are using gstreamer. Enter in terminal "gstreamer-properties" and there try to change something. I personally use mplayer based player called smplayer.

3. Look at this, it it similar, heavier problem but on same hardware.
[https://answers.launchpad.net/ubuntu/+source/nautilus/+question/71853]("https://answers.launchpad.net/ubuntu/+source/nautilus/+question/71853")

4. If everything fail. Download Ubuntu 9.10 carmic Koala. It is alpha 2 now. Burn it and try with live cd if you there have problems. I have it on my laptop and it is quite usefull, it is not like windows beta.

You write down some of stuff if it help you. For later. Hope I help you :)

edit:
If any of this stuff help you, reply to this thread with answer. For other that maybe need exact solution. bye, for now.. :)

---

### Post by abelthorne on 2009-07-05
> **moster said:**
> 1. Enter in terminal "gnome-volume-control" and remove in tab "switches" check-box "headphones". Put few problematic songs/videos in playlist and investigate now.
My system is in french and I'm not sure of what you call "switches". Anyway, I don't seem to have a "headphones" checkbox in the volume control.
I have "headphones" in the playback tab when selecting ALSA mixer but muting it doesn't change anything.

> 2. Many players in ubuntu except mplayer based (smplayer, mplayer...) and VLC are using gstreamer. Enter in terminal "gstreamer-properties" and there try to change something. I personally use mplayer based player called smplayer.
No change whichever settings I choose (autodetect - which sets PulseAudio -, ALSA, OSS, PulseAudio).

> 3. Look at this, it it similar, heavier problem but on same hardware.
[https://answers.launchpad.net/ubuntu/+source/nautilus/+question/71853]("https://answers.launchpad.net/ubuntu/+source/nautilus/+question/71853")
Mmm, it doesn't seem to be the same problem to me : I have sound, except it's bad in some contexts.


> 4. If everything fail. Download Ubuntu 9.10 carmic Koala. It is alpha 2 now. Burn it and try with live cd if you there have problems. I have it on my laptop and it is quite usefull, it is not like windows beta.
I'd rather not use an Ubuntu alpha on my laptop, as it's my work PC. ;)

What's nagging me is that the problem occured for no reason, so I guess it comes from an update I ran a few days ago. But I can't find anyone that has encountered the same issue. :/

---

### Post by moster on 2009-07-05
> **abelthorne said:**
> My system is in french and I'm not sure of what you call "switches". Anyway, I don't seem to have a "headphones" checkbox in the volume control.
I have "headphones" in the playback tab when selecting ALSA mixer but muting it doesn't change anything.



Here :)

edit:
I forgot to say UNcheck it, I assume you have that checked. :)

---

### Post by abelthorne on 2009-07-05
Well, on my laptop (Dell XPS M1330), I get no headphones option in the switches.

---

### Post by moster on 2009-07-05
Ok, this is last trick.

Enter this in terminal
gksu gedit /etc/modprobe.d/alsa-base.conf

add to the end.

```
options snd-hda-intel model=dell-bios
```

All of this you can find in this page.
[http://doc.ubuntu-fr.org/audio_intel_hda]("http://doc.ubuntu-fr.org/audio_intel_hda")

Restart computer after configuring, to be sure it is NOT working :)

edit:
I wonder why anybody else is not answering... hm, like a bad karma.

---

### Post by abelthorne on 2009-07-06
Still the same.

---

### Post by mocha on 2009-07-06
Pulseaudio seems to be more of a problem in Jaunty vs. Intrepid.  For SDL application issues, try adding ```
export SDL_AUDIODRIVER="esd"
``` to the end of your ~/.bashrc file then logout/re-login.  This takes care of extreme CPU consumption issues with SDL and pulse for me.

---

### Post by abelthorne on 2009-07-06
Mmm, ok, but :
- I have problems with Totem, MPlayer and Wine (which don't use SDL).
- I'm not sure I have problems with SDL apps : e.g. Enemy Territory with SDL hack works fine, while I'm not sure that the game that has sound issues (Hedgewars) use SDL.

It doesn't look like to a SDL-related problem to me, rather a "ALSA emulation through PulseAudio" one.

EDIT : I can add that the problem doesn't happen with another user, so it looks like a config issue.

---

### Post by mocha on 2009-07-07
> **abelthorne said:**
> EDIT : I can add that the problem doesn't happen with another user, so it looks like a config issue.

heh..  I can believe that.  I've been upgrading one of my boxes since Feisty, then I had a problem where I deleted some entries from the Gnome menu and it totally borked my desktop environment.  So instead of reinstalling the whole system I just "reset" the environment by deleting all the .gconf and .gnome/.metacity directories, escentially starting over with a fresh config with the same user.

I'll tell you this is the best thing I have done and I should have done it after each upgrade.  There are many workarounds I don't need to use anymore and new features that I never saw before as well as many annoyances that I thought were bugs have now disappeared.

---

### Post by abelthorne on 2009-07-14
It seems that the problem has been fixed by adding a .asoundrc file following the instructions of the thread about PulseAudio settings / Equalizer.
While I don't think the equalizer works (it's specified in the thread that it doesn't in Jaunty due to missing plugins), I guess the file set general sound levels in a way that they don't saturate anymore.

I'll confirm it's fixed after a few more tests.

EDIT : well, after a few tests with different videos, it looks like the problem is fixed.

---

### Post by abelthorne on 2009-07-16
Damn ! The problem is not solved at all.
In fact, adding the non-working equalizer stopped PulseAudio working, thus the impression that the problem was gone (as my system was back to ALSA). :(

Removing the equalizer to allow PulseAudio again makes the problem reappear.

---

### Post by brott8 on 2009-07-27
> **mocha said:**
> Pulseaudio seems to be more of a problem in Jaunty vs. Intrepid.  For SDL application issues, try adding ```
export SDL_AUDIODRIVER="esd"
``` to the end of your ~/.bashrc file then logout/re-login.  This takes care of extreme CPU consumption issues with SDL and pulse for me.

This one fixed my issue, thanks! (unless just rebooting fixed it temporarily... I'll post back if it happens again....)

Much appreciated

---

