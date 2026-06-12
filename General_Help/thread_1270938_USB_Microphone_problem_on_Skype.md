---
title: "USB Microphone problem on Skype"
date: 2009-09-20
forum: General Help
---

### Post by TheStroj on 2009-09-20
Hi everyone!

I'm using Ubuntu 9.04 and this microphone:
[http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=US,EN](http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=US,EN)

When i try to record sound with it in Sound Recorder it works great, I can hear my voice.

But it doesn't work in skype.
I remember that in Windows i had to set some setting to "USB microphone" or something like that to make it work. It was really easy, but in Skype for Ubuntu i can't find this option.

If I go to sound devices I have 3 options to set:
Microphone
Speakers
Ringing

When I make a call to my friend I can hear him, but he can't hear me and the test call doesn't work either.

My settings in Sound Devices are:
Microphone: PulseAudio Server(local)
Speakers: PulseAudio Server(local)
Ringing: PulseAudio Server(local)

The problem is, that none of these settings can't be changed. If I click on "PulseAudio Server(local)", I don't get any options.

I also used "lsusb" command in terminal and that's what it shows:
```

jure@jure-desktop:~$ lsusb
Bus 002 Device 004: ID 058f:6254 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046e:5503 Behavior Tech. Computer Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0461:4ea6 Primax Electronics, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Please help! If you think that I have to set something in Volume settings please say!

---

### Post by TheStroj on 2009-09-20
*bump*
I need to make it work plzzzz

---

### Post by TheStroj on 2009-09-20
*bump* again, please answer

---

### Post by kostkon on 2009-09-20
You need to install the *PulseAudio Device Chooser* utility using *Synaptic*.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by TheStroj on 2009-09-20
> **kostkon said:**
> You need to install the *PulseAudio Device Chooser* utility using *Synaptic*.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").
Thank you, I'll try and report when done.

---

### Post by TheStroj on 2009-09-20
I did it! It works great! Thanks you sooo much for that link!

---

### Post by stevecoh1 on 2010-06-15
Well, the thread says 10.04 but you say you're running 9.04 which sounds about right since 10.04 wasn't released when the thread started.  Actually, I don't know when the thread started, I was looking at your join date, but it seems related to 9.04 rather than 10.04.

I had this problem too under 10.04, and your solution doesn't quite work because there is no PulseAudio device chooser available.  But I did go into synaptic and install everything I could find related to Pulse Audio.  There were several such packages.  I don't know which ones were critical and which weren't - it's not very well documented - but after doing so, skype worked correctly.

It would be nice if there could be a more definitive explanation here about what all is necessary.  This Pulse Audio multiple package business is a bit of a mess, IMHO.  But thanks, for at least pointing me in the right direction.

---

### Post by stevecoh1 on 2010-07-09
> **stevecoh1 said:**
> Well, the thread says 10.04 but you say you're running 9.04 which sounds about right since 10.04 wasn't released when the thread started.  Actually, I don't know when the thread started, I was looking at your join date, but it seems related to 9.04 rather than 10.04.

I had this problem too under 10.04, and your solution doesn't quite work because there is no PulseAudio device chooser available.  But I did go into synaptic and install everything I could find related to Pulse Audio.  There were several such packages.  I don't know which ones were critical and which weren't - it's not very well documented - but after doing so, skype worked correctly.

It would be nice if there could be a more definitive explanation here about what all is necessary.  This Pulse Audio multiple package business is a bit of a mess, IMHO.  But thanks, for at least pointing me in the right direction.

Aargh!  Now one or two Ubuntu updates later and the microphone no longer works.  It doesn't work in skype and it doesn't work in sound recorder.

---

### Post by theNthDoctor on 2010-10-05
> **kostkon said:**
> You need to install the *PulseAudio Device Chooser* utility using *Synaptic*.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

Make sure to read the original post AND follow your headset's pairing instructions - this worked for me on 10.04.

---

