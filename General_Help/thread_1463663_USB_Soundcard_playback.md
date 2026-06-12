---
title: "USB Soundcard playback"
date: 2010-04-27
forum: General Help
---

### Post by Diminished on 2010-04-27
Hi all,

I've just bought a very cheap USB sound device as the jacks built into my laptop are practically dead. I bought it as I'd googled around and seen that other people have it working in linux.

Anyway, I plug it in and am able to select "USB AUDIO (ALSA)" from the xfce4-mixer. However, I don't get any sound from any applications. 

Here is my aplay -l output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I can't find any options for the output on alsamixer and don't really know what to do. 

Any advice would be greatly appreciated. Thanks.

Also, I'm running Mint with xfce4 on a Dell Studio 15 if that's any help.

---

### Post by Diminished on 2010-04-27
Bttt.

---

### Post by Mark Phelps on 2010-04-27
Since you're new to the forums, let me pass along a couple of lines of advice ...

First, don't start bumping every hour or so.  That's considered rude.  The polite approach is to bump no more than once every 24 hours.

Second, this is the Ubuntu forums, not Mint, and while they have similarities, they are not identical.  So, don't be surprised if you get few responses here. You would do better going to the Mint forums at the link below:

[http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

---

