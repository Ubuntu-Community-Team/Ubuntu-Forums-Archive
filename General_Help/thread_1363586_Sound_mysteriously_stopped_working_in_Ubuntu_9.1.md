---
title: "Sound mysteriously stopped working in Ubuntu 9.1"
date: 2009-12-24
forum: General Help
---

### Post by cmwebuser on 2009-12-24
My audio on my ubuntu setup died on me last night, and only change that comes to mind is I put the machine in "Suspend" possibly at time of it dying.  I tried reinstalling ALSA, restarting all related services (pulseaudio, alsa), tried restarting numerous times, and google'd for solutions for 2 hours last night.  Other users online have had problems with audio not working after suspend, but a restart always fixes their issue.  

My system is running the Zotac Ion A-U board which has HDMI and SPD/IF out.  Both of these were working earlier this week. I've tried going to System -> Admin -> Sound and switching which hardware i'm using (analog vs. HDMI vs. digital, etc.).

Running "aplay -l" shows that the audio device is there:
-----------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
------------------------------------------------------


Running "aplay -Dplughw:X,0 -fcd /usr/lib/openoffice/basis3.1/share/gallery/sounds/romans.wav" throws this error: 
-----------------------------------------------------
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
aplay: main:608: audio open error: No such device
ALSA Mixer has all volumes maxed out and unmuted.
-----------------------------------------------------


I'm running latest version of Unbuntu (Karmic Koala 9.1) downloaded last week.

I originally ran a ALSA Upgrade Script ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)) which my audio was working fine with.  I've tried rerunning this after resinstalling alsa via apt-get.

Any other ideas?

---

### Post by cmwebuser on 2009-12-25
More information from Alsa:

[http://www.alsa-project.org/db/?f=2a528ca1f69fbe1446950b443ffbcce13fbc7981](http://www.alsa-project.org/db/?f=2a528ca1f69fbe1446950b443ffbcce13fbc7981)

I'm not seeing anything wrong in this output.. anyone else?

---

### Post by switch10 on 2009-12-25
I've had this same thing happen.  I have know idea what causes it.  but if you go into alsa mixer from the terminal:
```
alsamixer
```

and mess with the volumes, it seems to help me.  they get turned down randomly for me sometimes.

good luck

Dave

**EDIT**  Omit this post.  I didn't read the bottom part of your post.  I thought it was a signature :)

---

### Post by franklamoureux on 2010-03-25
Hi all, I'm running into the exact same situation, the sound simply mysteriously stops working.
[FONT="Courier New"]
--------------
francois@gras:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
--------------
[/FONT]

And same test & result:
[FONT="Courier New"]
--------------
francois@gras:~$ aplay -Dplughw:X,0 -fcd /usr/lib/openoffice/basis3.1/share/gallery/sounds/romans.wav
ALSA lib pcm_hw.c:1435:(_snd_pcm_hw_open) Invalid value for card
aplay: main:608: audio open error: No such device
--------------
[/FONT]

alsamixer shows all sound bars to the max.

---

### Post by thejaswi.hr on 2010-03-25
I have been an openSuSe for the past 7 years, before I decided to give Ubuntu a shot. I have been facing the exact same problem.

Sound was working fine and suddenly it stopped working after a suspend. A restart did not fix the problem. And I get the same error as the rest of the them in this post.

But however, my problem is slightly different. I dont get sound on KDE, but it works perfectly fine in Gnome. 

Can someone help us out here? Its very annoying to face this problem.

~ m.a.v.e.r.i.c.k

---

### Post by franklamoureux on 2010-03-26
Never mind all this, more digging around I found the solution at [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/").

Once Alsa upgraded, full sound!

---

### Post by franklamoureux on 2010-03-26
Never mind all this, more digging around I found the solution at [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/").

Once Alsa upgraded, full sound!

---

