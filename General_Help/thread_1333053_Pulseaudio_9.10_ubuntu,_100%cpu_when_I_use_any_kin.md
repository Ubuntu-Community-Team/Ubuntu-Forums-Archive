---
title: "Pulseaudio: 9.10 ubuntu, 100%cpu when I use any kind of recording"
date: 2009-11-21
forum: General Help
---

### Post by milro on 2009-11-21
I had (clean) installed karmik coala (9.10 version) on two different computers (the first: laptop with SIS Audio Controller+ Realtec AC97 Codec, the other: Desktop Computer with VIA audio controller and HDA Realtec Codec) and I had the same problem on both of them.
When a program (like Skype or even the default gnome volume control settings applet) access the recording-capture part of the sound system, pulseaudio goes to 100% cpu usage (on one of the cpu cores). Until I shutdown the offending application my sound is jerky or doesn't work at all and the cpu usage remains to 100%. Of course recording does not work.
I've searched the forum for a solution and I've seen numerous reports about sound problems similar to mine but none of the proposed solutions solved the problem for me. The only thing that it did work was to switch off the autospawn capability of pulseaudio server and after that, to kill pulseaudio. Of course that meant I was back with ALSA (no problem at all with that part of the solution) and I had no volume control mixer applet on my panel (that was a problem). With Jaunty pulseaudio is usable. The problem does not occur, at least on my Desktop computer (I've just test that, because now I am back to Jaunty).

It would be simpler if I had a choice, a real choice, about the sound solution that I prefer, so if pulseaudio doesn't cut it for me to be possible to go to my sound system preferences and change to ALSA or OSS or whatever (like in Jaunty). Gentlemen make pulseaudio default for karmik but give real access to other choices. If pulseaudio wasn't forced to everyone throat and there was a choice I wouldn't had revert back to Jaunty installation and many people would be happier with their ubuntu box.
I was a microsoft windows user and now I am trying to learn my way with linux. Ubuntu is great: the perfect entrance point to the linux world. Sometime is frustrating (especially for a Windows user) to have many choices (Gnome vs KDE vs..., pulseaudio vs esound vs OSS vs ALSA.... etc) but with Linux I believe is the only viable choice. Give us access to options and choices in order to solve our problems.

By the way, has anyone found a way to enable the analog sound part of Pinnacle 320e Hybrid Pro Usb Tuner?

---

### Post by eschvoca on 2009-11-23
Hi, I have the same problem.  I have an es1371 based sound card and I can't record on the line-in.  I get 100% cpu and the recording doesn't work.  I haven't found a solution yet either. :(

---

