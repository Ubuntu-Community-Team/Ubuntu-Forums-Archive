---
title: "Audio - how to?"
date: 2011-08-11
forum: General Help
---

### Post by Colo2 on 2011-08-11
Hey

Fresh install - no errors, everything seems to be working, apart from the fact that I have no audio playback. :|

I found out my chipset is SIS SI7012 , upon googling, I found this:

> The SiS7012 sound card (the one on the A9T laptop) will work by removing Alsa modules and enabling the corresponding DSP driver (i810_audio). You need to configure XMMS to use the DSP (in XMMS options).

problem is, I dont know what he means, and how to do it :S

Can anyone help

Thanks :)

---

### Post by zero2xiii on 2011-08-11
Please post the link to the site you qouted from.

There are a few options I believe, but for anyone to help, we need more information.

What ubuntu install did you do? version etc.

And the link, computer harware  "sudo lshw"

Thanks :)

---

### Post by Colo2 on 2011-08-11
> **zero2xiii said:**
> Please post the link to the site you qouted from.

There are a few options I believe, but for anyone to help, we need more information.

What ubuntu install did you do? version etc.

And the link, computer harware  "sudo lshw"

Thanks :)
Hey
Thanks for your reply

here: [http://ubuntuforums.org/showthread.php?t=384945](http://ubuntuforums.org/showthread.php?t=384945)

The audio card is SiS SI7012 
Ubuntu version is 11.04
Mobo is made by foxconn

Is that enough info?

Thanks :)

Tom

---

### Post by realzippy on 2011-08-11
That side is outdated!

---

### Post by Colo2 on 2011-08-11
only help I could find

---

### Post by Colo2 on 2011-08-11
> **Colo2 said:**
> only help I could find

hm, Guess I cant use ubuntu on this pc then :S

---

### Post by realzippy on 2011-08-11
You can do what is suggested in post#6 of that link,
means open terminal,type
```
alsamixer
```
and check your device settings.
But don't try post#7 !
You could also click on the Loudspeaker icon in panel,audio-settings,
and see if your device is present.

---

### Post by Colo2 on 2011-08-11
Hey

Under output in Sound Preferences, I have "Internal Audio Analog Stereo"

The volume is turned up, theres no obvious malfunctions.

I've already been in alsamixer, and unmuted every single channel, and turned the volumes up.

:S

---

### Post by realzippy on 2011-08-11
what does
```
cat /proc/asound/cards
```
say ?

---

### Post by Colo2 on 2011-08-11
> **realzippy said:**
> what does
```
cat /proc/asound/cards
```
say ?

```
0 [SI7012                ]: ICH - SiS SI7012
                            SiS SI7012 with ALC655 at irq 18
```

thanks

---

### Post by realzippy on 2011-08-11
and
```
sudo aplay -l
```

---

### Post by Colo2 on 2011-08-11
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by realzippy on 2011-08-11
..so card (chip) is seen.

```
find /lib/modules/`uname -r` | grep snd
```

...if modules are loaded,I have no idea.
Maybe you are affected by this natty bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/794748](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/794748)

You could try Ubuntu 10.04/10 liveCD to confirm...

---

### Post by Colo2 on 2011-08-11
Thanks so much for your help :) Ill download a livecd overnight and install it tomorrow.

;]

---

### Post by realzippy on 2011-08-11
If the sound doesn't work when booted live,there is no sense in installing the system I guess...anyway,we will see (hear).

---

### Post by Colo2 on 2011-08-12
No sound

not even a beep. I even tried different speakers. :\

---

### Post by realzippy on 2011-08-12
Real sorry.
Maybe you start a new thread,eg titled:
*No sound SiS SI7012 with ALC655*
Or you could test an older Ubuntu version,8.10...you might get sound,
but had any security updates.

---

### Post by Colo2 on 2011-08-12
Thanks for your help :)

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

