---
title: "Can't get sound to come from Flash videos in Firefox"
date: 2009-09-09
forum: General Help
---

### Post by RagingRobot on 2009-09-09
Hello, I have a Logitech USB headset. Previously, it worked fine and I was able to listen to music or watch videos online perfectly. I restarted my computer for the first time in a while and I can no longer hear any sound coming from flash videos (Firefox or Opera). When I do a sound test in the Sound preferences, I can hear the test noise fine. However, I still can't hear anything in Firefox or Opera! I have my playback device set to ALSA because I can't hear the test noise with anything else.

I'm on Ubuntu 9.04 and Firefox 3.0.13

Thanks!

---

### Post by RagingRobot on 2009-09-10
Can anyone help please?

---

### Post by Screwdriver0815 on 2009-09-10
have you checked the alsamixer?

open a terminal

type in

```
alsamixer
```

and then some equalizer bars appear. Check if the Master and PCM is not muted or on zero.

If they are muted, navigate to them with the arrow keys of your keyboard and tune them up (with the up-arrow-key)

leave the alsamixer by pressing ESC <-- this is important because otherwise the configuration will not be saved

---

### Post by RagingRobot on 2009-09-10
Yes, it's all at 100. I can hear sound coming from the system (like the sound test noise in Preferences>Sound) just not from flash video in Firefox or Opera.

---

### Post by Screwdriver0815 on 2009-09-10
> **RagingRobot said:**
> Yes, it's all at 100. I can hear sound coming from the system (like the sound test noise in Preferences>Sound) just not from flash video in Firefox or Opera.

so you also hear sound when you play a music file or a film? but not in flashvideos?

which flash plugin do you have? Is it the latest?

---

### Post by RagingRobot on 2009-09-10
Yes, that's right, and my version is the latest.

---

### Post by chriskin on 2009-09-10
i have the same problem, are you on 32bit or 64bit?

---

### Post by RagingRobot on 2009-09-10
It's 32-bit

---

### Post by chriskin on 2009-09-10
meaning it's not on the 64bit implementation of the plugin.
we will have to wait for someone who has seen it to help then :S

---

### Post by Screwdriver0815 on 2009-09-10
hmm... this is quite strange...

the only advise I could give you would be:

look into the sound preferences, save the output device and and the channels in your mind (or make a screenshot) so that you remember the current status and then play around with the devices and the channels. Trial and error...

sorry that I can't help any further...

---

### Post by RagingRobot on 2009-09-10
If it helps I think I may know why this happened. It was working fine, then before I restarted my computer I had removed the USB headset and plugged in an analog headset using the Line In and Line Out ports. Then I removed that and plugged the USB back in and it doesn't work in Firefox.

---

### Post by Screwdriver0815 on 2009-09-10
> **RagingRobot said:**
> If it helps I think I may know why this happened. It was working fine, then before I restarted my computer I had removed the USB headset and plugged in an analog headset using the Line In and Line Out ports. Then I removed that and plugged the USB back in and it doesn't work in Firefox.

have you tested it with the analog headset? Does this work?

Maybe it is an issue with the channels or with the USB stuff...

can you reboot it while leaving the usb-headset connected? And maybe do the same with the other one. I think the system became confused about which headset to use and therefore which port/driver and channel...

---

### Post by RagingRobot on 2009-09-10
Yes the analog one works, but not the USB one. How can I get it set to transfer sound to the USB again?

---

### Post by KodieG on 2009-09-30
i'm having this same problem. sound works perfectly fine on everything else but flash. the video and everything is fine, just no sound.

i feel like ive tried everything. :(

---

