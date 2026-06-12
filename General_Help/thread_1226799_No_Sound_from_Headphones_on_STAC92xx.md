---
title: "No Sound from Headphones on STAC92xx"
date: 2009-07-29
forum: General Help
---

### Post by razorboy5 on 2009-07-29
Hi
sry i know this has been done before but can't find a good solution

i had sound on my ubuntu before from some tweaking then i switched to Kubuntu briefly to see what it is like (not for me) and came back to ubuntu and now i can't remember what i did to get my sound working.

i followed at least 4 different tutorials to fix this problem with no success

my sound card shows up (STAC92xx)
non of it is muted

any solutions that have worked for u please send them this way

it's a MUST to have sound on my laptop and i'm half crying right now ...

thx

EDIT: the speakers on the laptop work fine, sound comes out if it and everything just not when i plug in the headphones

---

### Post by razorboy5 on 2009-07-29
sry i just noticed this now but

when i go the System -> Pref -> Sound

set my Sound Playback to: HDA Intel STAC92xx Analog (ALSA)

then press Test it errors

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

is this a problem with the alsa mixer?

---

### Post by razorboy5 on 2009-07-30
ok solved it by removing pulseaudio and alsa mixer then replacing it with OSS4 for anyone else having this problem

---

### Post by helpdeskdan on 2009-10-05
Thanks for the suggestion, same card.  

I tried everything, modifying the puleaudio config for the correct card, installing the latest alsa - nothing worked!  

Finally, I followed the instructions here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

That finally worked.  What people say about oss seems true, the sound is very good.  

Downside: Had to set many apps to use oss, and plain give up on others. See this page:
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

Upside:
Only thing that worked!

---

### Post by helpdeskdan on 2009-10-09
Finally got it working in Jaunty. You need to add this to your /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=ref

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/363721](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/363721)

Hope that helps somebody out!

---

