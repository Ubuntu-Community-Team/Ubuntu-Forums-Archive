---
title: "VLC loss of sound or static noise"
date: 2011-10-30
forum: General Help
---

### Post by Mordrogyn on 2011-10-30
I'm still fairly new to ubuntu but, I'm running 11.10 and use vlc, because I know and love it from using windows.

Problem is, if I install codecs to play mp3's from my ipod in banshee VLC then loses all sound.  Fixed this the noob way with a total clean install and haven't done the banshee thing again yet, all was fine.  Then after a skype call with my parents VLC developed a horrible static noise, regular sound can be heard but the interference is nasty.

Took to using the standard media player after installing the right codecs but would love to be able to use VLC again.

Anyone else had this issue?

---

### Post by ricardisimo on 2011-11-17
I've been experiencing an intermittent static issue in VLC ever since the upgrade to 11.10. Very annoying. Can't pin it down. All video formats. Any hints?

---

### Post by ricardisimo on 2011-11-17
Edit: So I know how to get rid of it, but it still makes no sense to me. I have to go to Audio >> Visualizations >> Spectrometer, and then disable it. Then the audio is fine. How crazy is that?

---

### Post by scottbomb on 2011-11-17
I've had this problem as well, since 11.04 in fact. Sound drops out at unpredicable times when playing a video. The only way to recover ANY sound is to reboot! I gave up on VLC for the time being and I'm using SM Player instead until the devs can find/fix the issue.

On the VLC website, a dev suggested I upgrade to version 2 but there is no such version in any repo that I'm aware of (incl multiverse, universe, restricted, etc... I have 'em all turned on except the proposed repo. I enabled it to see if I could find it there, no dice). The highest version I can find is 1.1.12.

---

### Post by ricardisimo on 2011-11-17
> **scottbomb said:**
> I've had this problem as well, since 11.04 in fact. Sound drops out at unpredicable times when playing a video. The only way to recover ANY sound is to reboot! I gave up on VLC for the time being and I'm using SM Player instead until the devs can find/fix the issue.

On the VLC website, a dev suggested I upgrade to version 2 but there is no such version in any repo that I'm aware of (incl multiverse, universe, restricted, etc... I have 'em all turned on except the proposed repo. I enabled it to see if I could find it there, no dice). The highest version I can find is 1.1.12.

Maybe a build direct from the VideoLAN site? Thanks for the tip. Still curious what it could be and why a visualization would "fix" it. Filed a bug on Launchpad in the meantime:
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/891505]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/891505")

---

### Post by cairnzi on 2011-11-22
hi,i had the same problem with xubuntu 11.10, all i did was goto,VLC- tools-preferences-audio, then change the output module to alsa audio output. hope this works for you.:D

---

### Post by notmyidea on 2011-12-02
> **cairnzi said:**
> hi,i had the same problem with xubuntu 11.10, all i did was goto,VLC- tools-preferences-audio, then change the output module to alsa audio output. hope this works for you.:D

That fixed it for me, thanks! :P

---

### Post by Elzigzag on 2012-02-06
> **cairnzi said:**
> hi,i had the same problem with xubuntu 11.10, all i did was goto,VLC- tools-preferences-audio, then change the output module to alsa audio output. hope this works for you.:D

Somehow it worked for me it, this alsa thing... Thanks like a LOT!

---

