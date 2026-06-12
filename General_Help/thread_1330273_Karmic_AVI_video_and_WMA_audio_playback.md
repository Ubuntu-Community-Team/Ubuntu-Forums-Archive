---
title: "Karmic AVI video and WMA audio playback"
date: 2009-11-18
forum: General Help
---

### Post by canadianwriterman on 2009-11-18
Something has changed in Karmic with video playback... I am no longer able to play AVI files. 

After a fresh install of Karmic, I installed restricted extras and the windows w32codecs through the medibuntu repositories like I always do. Both Totem and VLC are no longer able to play AVI video files and Rhythmbox can't play WMA audio files like Jaunty used to. MPlayer will play the AVI's but with an error message flashing annoyingly during playback.

Frankly, I can't figure out what has changed, since I set up the install the same as I have every release in the past. Any ideas?

---

### Post by Giblet5 on 2009-11-18
I installed what you installed and AVI works from totem. The color is way off, but it works.

Have you tried a reconfigure of the codecs? ```
sudo dpkg-reconfigure ubuntu-restricted-extras
```

---

### Post by mc4man on 2009-11-18
As far as avi playback try starting vlc and or mplayer from the command line and see what shows up
mplayer -v /path/to/avi
vlc -vv /path/to/avi

Most likely problem  would be your video output which by default would be xv

As far as wma and video with wma audio, gstreamer apps (and repo vlc), in karmic should play wma2.

That would be the extent of wma playback for the repo vlc

rhythmbox should play wma3 (9.1), but it won't in karmic (the use of w32codecs thru the pitfdll gstreamer plugin appears to be somewhat broken in karmic

The only repo app you've mentioned that can play wma3 (10), and wma lossless is mplayer thru w32codecs.

The restricted extras package is written wrong in karmic and will install the regular stripped ffmpeg libs, though that should only affect encoding, not decoding.
You could search ffmpeg and bump your ffmpeg libs to the 'extra' versions

Edit
sometimes in karmic you need to reboot more often then you should

---

### Post by canadianwriterman on 2009-11-18
Thanks all for your suggestions... I'll try them out when I get home tonight.

---

### Post by redcodefinal on 2009-11-18
There is a good possibility one of the codecs didn't install. Did you install vlc through a package or through a channel?

---

### Post by canadianwriterman on 2009-11-18
I installed VLC through this ppa:

[http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) karmic

---

### Post by andrew.46 on 2009-11-18
Hi mc4man,

> **mc4man said:**
> Most likely problem  would be your video output which by default would be xv

This is a problem that is now commonly seen across the forums. What is the problem with *-vo xv* under Ubuntu? This has been puzzling me for a while now...

Andrew

---

### Post by JBAlaska on 2009-11-18
> **Giblet5 said:**
> **I installed what you installed and AVI works from totem. The color is way off, but it works.**

Have you tried a reconfigure of the codecs? ```
sudo dpkg-reconfigure ubuntu-restricted-extras
```

In totem go to edit, preferences, display..set to default button.

---

### Post by mc4man on 2009-11-18
> What is the problem with -vo xv under Ubuntu?
I don't have much technical knowledge here, more some observations and logical T & E.

I'd think it's mainly about hardware, specifically the display adapter and the drivers in use. While I guess on some setups resources may also be a factor in overall performance, as far as xv support you either have it or don't.
(though xvinfo produces some varying results here on different adapters, though all can output xv, so possibly there is a 'degree of' ...?

So while one's hardware may (or did) support the XVideo extension for hardware acceleration, it's clearly not a given that it will in the future/current release(s)

---

