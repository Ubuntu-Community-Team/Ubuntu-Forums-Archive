---
title: "no sound.. realtek alc850"
date: 2012-03-17
forum: General Help
---

### Post by gandalf3 on 2012-03-17
I am new to Linux (and posting on forums) and just installed Ubuntu 11.10 but I don't get any sound.
I tried drivers from asus.com ([http://usa.asus.com/Motherboards/Intel_Socket_775/P5N32SLI_SE_Deluxe/#download](http://usa.asus.com/Motherboards/Intel_Socket_775/P5N32SLI_SE_Deluxe/#download))

and i *think* they installed correctly, but I don't really know how to install a driver (or anything not in the software center) in Linux.

yes, the speakers work, and no, it's not on mute.
also, the sound never worked in windows7 either, but there are no windows7 drivers for Realtek alc850

System:

Asus p5n32-sli DELUXE
Intel pentium4
nvidia nx7900 gt

---

### Post by Rodney9 on 2012-03-17
This post has some help

[http://ubuntuforums.org/showthread.php?t=1390746](http://ubuntuforums.org/showthread.php?t=1390746)

These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

sudo apt-get install pavucontrol


Rodney

---

### Post by gandalf3 on 2012-03-20
everything i tried said there was sound coming out of the speakers, but of course there wasn't..
eventually i gave up, blamed the mobo, and got a used cheap Soundblaster which worked out of the box :D
Thanks for all the help!

---

