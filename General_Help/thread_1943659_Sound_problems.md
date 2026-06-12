---
title: "Sound problems"
date: 2012-03-19
forum: General Help
---

### Post by mgm112 on 2012-03-19
Hello, I am having trouble getting my audio to work anymore. I reinstalled Ubuntu and still cannot hear anything from my internal laptop speakers. It just stopped working suddenly. Here is a script I just ran if that helps any, thanks!
[http://www.alsa-project.org/db/?f=bc8728b6deb2dda7aa3ca00a23f890aba9b77444](http://www.alsa-project.org/db/?f=bc8728b6deb2dda7aa3ca00a23f890aba9b77444)

---

### Post by Rodney9 on 2012-03-19
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


**pavucontrol**

> sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal

---

