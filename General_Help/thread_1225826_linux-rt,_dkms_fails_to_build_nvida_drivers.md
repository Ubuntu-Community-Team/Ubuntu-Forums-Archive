---
title: "linux-rt, dkms fails to build nvida drivers?"
date: 2009-07-29
forum: General Help
---

### Post by jerome1232 on 2009-07-29
So me and my friend are both having problems with Teamspeak (an oss app), it's a voice conference program.

Audio transmitted from the mic will stutter badly when using pulseaudio, playback is fine, just what's is captured by the microphone stutters. We have to use pulseaudio otherwise sound will not work in teamspeak and in our game at the same time.

From my looking around I saw mention that this may be caused because Ubuntu's generic kernel has high latency so as an attempted solution I installed linux-rt and linux-headers-rt, linux-restricted-modules-rt is also installed.

When I boot from the rt kernel my nvidia drivers fail to compile (the dkms auto thingy) and as a result x fails to start.

What else do I need to get the drivers working with linux-rt.

---

### Post by jerome1232 on 2009-07-29
Well I've had it with teamaspeak them using oss. I found out about mumble, supports pulseaudio natively, initial testing of it results in very good capture.

So I'm installing the mumble-server on my server and ditching teamspeak and oss :).

---

### Post by zer0x on 2009-10-12
Hi,

I have had a similar problem with ATI's fglrx on the karmic linux-rt, a patch was derived from this Nvidia patch:

[http://www.nvnews.net/vbulletin/showthread.php?p=2087519#post2087519]("http://www.nvnews.net/vbulletin/showthread.php?p=2087519#post2087519")

HTH

zer0x

---

