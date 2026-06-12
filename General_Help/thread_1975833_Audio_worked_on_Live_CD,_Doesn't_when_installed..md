---
title: "Audio worked on Live CD, Doesn't when installed."
date: 2012-05-07
forum: General Help
---

### Post by Dr3gul4a on 2012-05-07
So I have a Dell Vostro13, on which I had used a Live USB to try Ubuntu 11.10.  After working off the live distro for about a week I decided to make it the permanent OS for my laptop.

So here's my problem, after installing the installation from the very USB that I was running the live image off of, my sound no longer works, I have been scouring the forums and have tried multiple "fixes" that have had no avail on my system.

Anyone that can offer some insight to a total noob would be much appreciated.

---

### Post by Rodney9 on 2012-05-07
```
sudo apt-get install pavucontrol
```

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

Rodney

---

