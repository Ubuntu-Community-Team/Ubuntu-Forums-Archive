---
title: "Ubuntu Pulse audio unstable"
date: 2009-11-17
forum: General Help
---

### Post by whitethorn on 2009-11-17
Hi,

A couple times I've just been watching videos or just listening to music then the sound will just loop and the computer hangs.  The only way to get it to restart is by pushing the reset button.  I've tried switching to the first console, and I've tried using alt+print+reisub nothing works.  I've just checked my syslog after one such freezes and I think this is the reason.

> 
Nov 18 04:30:39 wt-ub vdr: [2685] exiting, exit code 2
Nov 18 04:30:39 wt-ub runvdr: stopping after fatal fail (No protocol specified)
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov 18 04:30:40 wt-ub pulseaudio[2782]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.


This might not be the problem but I haven't found anything else which my be the problem in my syslog.

---

### Post by P4man on 2009-11-18
Might help if you tell us which version of ubuntu, which kernel and what sound card you have. That said, if you google on the error, you'll find plenty of bug reports. I suggest you have a look there for workarounds and/or confirm the bug which matches your hardware.

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=A8g&q=ubuntu+Your+kernel+driver+is+broken%3A+it+reports+a+volume+range+from+18.00+dB+to+18.00+dB+which+makes+no+sense.&cts=1258535932233&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=A8g&q=ubuntu+Your+kernel+driver+is+broken%3A+it+reports+a+volume+range+from+18.00+dB+to+18.00+dB+which+makes+no+sense.&cts=1258535932233&aq=f&oq=&aqi=)

---

### Post by whitethorn on 2009-11-19
Right my bad.  I'm currently running 9.10 64-bit.  The kernel version I'm using is
2.5.31-14-generic and my sound card is a built in realtek card  I have an Asus P5Q-Pro motherboard.  It uses the snd_intel_hda module oh and it's an ALC1200 version.  I'll google it maybe I'll find something, if I do I'll post back. If any1 has any ideas help. :)

---

### Post by giftedwon on 2009-11-19
pulse audio is a nightmare.   i some how got mine to work by uninstalling and reinstalling pulse audio

---

### Post by lrcaballero on 2009-11-20
there is some important updates for Pulse Audio today!!! did you download them yet??? maybe this will eliminate your problem!!!!

best of luck

Luis

---

### Post by beausoleil on 2010-03-12
Well, I'm running PulseAudio 1.0.9.19-0ubuntu4.1, and the error is still there...

---

