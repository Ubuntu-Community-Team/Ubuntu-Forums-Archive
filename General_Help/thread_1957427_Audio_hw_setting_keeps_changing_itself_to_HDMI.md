---
title: "Audio hw setting keeps changing itself to HDMI"
date: 2012-04-12
forum: General Help
---

### Post by gnugu on 2012-04-12
Hi,
I have:
- Ubuntu 11.10
- Gnome 3.2.1 session
- Monitor connected via HDMI cable. Monitor has no speakers.

This started few weeks ago after the update.

In SoundSettings->Hardware I select "Analog Stereo Duplex" profile so I can hear the sound from my laptop speakers.
Every time the session is locked (logout, shutdown, lock screen) the thing sets itself to one of the HDMI profiles.

Any idea why? I suspect the HDMI connection of the monitor.
Regardless, how can I lock to analog profile?

Thanks.

---

### Post by jdawg70 on 2012-04-12
I've got the exact same issue, and it seems like it started a week or so ago after some updates.  A quick look at dmesg output tells me that the monitor hooked up via HDMI is telling Ubuntu that it does have speakers associated with it (LG 2241).  Don't know if the monitor is actually reporting that or if Ubuntu is assuming that, but it does seem like that hot plug event (i.e. the monitor waking up) is causing Ubuntu to switch to that output device.

---

### Post by papibe on 2012-04-12
Hi gnugu.

Could you post the result of this command?
```
ls -la .pulse .pulse-cookie
```
Regards.

---

### Post by gnugu on 2012-04-13
```
-rw------- 1 gnugu gnugu  256 2010-07-23 17:55 .pulse-cookie

.pulse:
total 172
drwx------  2 gnugu gnugu  4096 2012-04-13 08:25 .
drwxr-xr-x 88 gnugu gnugu  4096 2012-04-13 08:25 ..
-rw-r--r--  1 gnugu gnugu 24576 2012-04-09 09:23 e1c339c9937faf26d21007764c4a39cd-card-database.tdb
-rw-r--r--  1 gnugu gnugu    43 2012-04-13 08:34 e1c339c9937faf26d21007764c4a39cd-default-sink
-rw-r--r--  1 gnugu gnugu    42 2012-04-13 08:34 e1c339c9937faf26d21007764c4a39cd-default-source
-rw-r--r--  1 gnugu gnugu 61440 2012-04-05 15:38 e1c339c9937faf26d21007764c4a39cd-device-volumes.tdb
lrwxrwxrwx  1 gnugu gnugu    23 2012-04-13 08:25 e1c339c9937faf26d21007764c4a39cd-runtime -> /tmp/pulse-CcctT9RwKSB1
-rw-r--r--  1 gnugu gnugu 73728 2012-04-02 12:00 e1c339c9937faf26d21007764c4a39cd-stream-volumes.tdb

```

---

### Post by papibe on 2012-04-13
I was expecting to see an ownership or permission problem, but it looks OK.

You could try remove all personal pulse setting, so you can start from clean:
```
rm -rf ~/.pulse ~/.pulse-cookie
```
Then set the setting as you want, and try login out and in again to see if they stick this time.

Regards.

---

### Post by gnugu on 2012-04-13
Ouch. Now I don't have any hardware in Sound settings. How do I get it back?

---

### Post by gnugu on 2012-04-13
Ok, after the reboot I have my sound profiles and hw back.
But the problem remains.

It keeps switching itself to "Digital Stereo (HDMI) Output + Analog Stereo Input" profile.

Interesting thing is that under Output tab I only have HDMI connector available. Not quite sure what that means.

---

### Post by jdawg70 on 2012-04-14
Interestingly enough, hitting the power button on the offending monitor does not cause the issue.  However, unplugging/replugging in the HDMI connector does replicate.

dmesg output upon resume from lock:
[693816.119215] HDMI hot plug event: Pin=7 Presence_Detect=1 ELD_Valid=1
[693816.119255] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=1
[693816.122745] HDMI: detected monitor  at connection type HDMI
[693816.122748] HDMI: available speakers: FL/FR
[693816.122752] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16

dmesg output from unplug/replug:
[694925.068280] HDMI hot plug event: Pin=7 Presence_Detect=0 ELD_Valid=1
[694925.068320] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[694925.121312] HDMI hot plug event: Pin=7 Presence_Detect=1 ELD_Valid=1
[694925.121359] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=1

In both cases, the Profile in the Hardware tab of Sound Settings gets reset to Digital Stereo (HDMI) nr 3 output...where I really really really just want it to stay with Analog Stereo Output.

Powering the monitor on/off does not spew anything out on dmesg.

---

### Post by gnugu on 2012-04-16
Dell ST2420L monitor here.

It has audio setting and I have set the "Line out source" to "PC Audio". It did not help to solve the problem.

---

### Post by jdawg70 on 2012-04-19
Just noticed another symptom today:
If I log out and log back in, Ubuntu sets the default sound profile to HDMI, but will also now only detect "Dummy Output" as an output device no matter which profile I select.  I have to reboot to get sound back.

This is bloody irritating.

---

### Post by jdawg70 on 2012-05-06
gnugu (and anyone else who has this issue) -

I just updated to 12.04, and the problem has gone away.

---

