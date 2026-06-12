---
title: "Alienware m17x Has No Sound When Headphones Plugged In"
date: 2010-06-28
forum: General Help
---

### Post by xluryan on 2010-06-28
The title pretty much says it all. I installed 10.04 on my m17x. I have sound from the laptop speakers, but when I plug in the headphone jack, it all goes quiet.

Any ideas?

---

### Post by fragos on 2010-06-29
Run alsamixer in a terminal window. use right arrow to select Headphon and M to toggle mute. Volume on headphones is controlled by the source so all you'll see is 00 or MM for mute state.

---

### Post by xluryan on 2010-07-01
> **fragos said:**
> Run alsamixer in a terminal window. use right arrow to select Headphon and M to toggle mute. Volume on headphones is controlled by the source so all you'll see is 00 or MM for mute state.

The headphone volume is set to 100, but I'm still having the issue.

Any other ideas?

---

### Post by fragos on 2010-07-01
Run alsamixer again, hit F3 and make sure no sources are muted. Then hit F4 to make sure you enough Capture volume set and that your Input Source is "Mic".

---

### Post by xluryan on 2010-07-04
> **fragos said:**
> Run alsamixer again, hit F3 and make sure no sources are muted. Then hit F4 to make sure you enough Capture volume set and that your Input Source is "Mic".

Nothing is set to less than 100, and nothing is muted. I tried removing pulseaudio as a remedy, but that had no effect either.

Any other ideas?

---

### Post by fragos on 2010-07-04
I'm getting into serious guess mode here. Click the sound icon on the applet bar and select "Sound Preference..." and then the Output tab. Here you choose a device for sound output. My mobo only has one choice "Internal Audio Analog Stereo". It also offers me a connector choice of "Analog Output" or "Analog Headphones". This may really mean amplified or not. My other thought relates to how the connectors are supported physically. A lot of desktops have sound and microphone jacks on the front and the back. If you're using the back output jack that might disable the front output jack. My front sound jack doesn't work either but I do have external speakers connected. My amplified speakers only work withe the "Analog Output" selection above. This may also be dependant on the sound chip set in your machine. As shown with "lspci" my Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1).

---

### Post by xluryan on 2010-07-05
> **fragos said:**
> I'm getting into serious guess mode here. Click the sound icon on the applet bar and select "Sound Preference..." and then the Output tab. Here you choose a device for sound output. My mobo only has one choice "Internal Audio Analog Stereo". It also offers me a connector choice of "Analog Output" or "Analog Headphones". This may really mean amplified or not. My other thought relates to how the connectors are supported physically. A lot of desktops have sound and microphone jacks on the front and the back. If you're using the back output jack that might disable the front output jack. My front sound jack doesn't work either but I do have external speakers connected. My amplified speakers only work withe the "Analog Output" selection above. This may also be dependant on the sound chip set in your machine. As shown with "lspci" my Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1).

In my sound preferences under Output I have "Internal Audio Analog Stereo" and "Juniper HDMI Audio [Radeon HD 5700 Series] Digital Stereo (HDMI)". When the first is selected, down below I have connector options that are either "Analog Output" or "Analog Headphones". The only way I can get sound is with the headphones no plugged in, "Internal Audio Analog Stereo" selected with "Analog Output" set.

If all three of those criteria are not met, I get no sound from any of the speakers. Everything works in Windows, so I know the hardware is good. Maybe I should try and use the Windows drivers somehow... ?

---

### Post by fragos on 2010-07-05
I rarely use headphones and in fact hadn't tried to use them until you needed help. Hardware wise I have a different system but I can't get headphones to work either with 10.4 and this I've a new mobo it may not have worked on 9.10 either -- just don't know. I looked in the Launchpad where Ubuntu bugs are reported and found that over time there have been a number of reports relating to headphones. The following bug report is for 10.04 and may give you some insight. You'll have to register to use Lanchpad.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/554959](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/554959)

---

### Post by xluryan on 2010-07-07
> **fragos said:**
> I rarely use headphones and in fact hadn't tried to use them until you needed help. Hardware wise I have a different system but I can't get headphones to work either with 10.4 and this I've a new mobo it may not have worked on 9.10 either -- just don't know. I looked in the Launchpad where Ubuntu bugs are reported and found that over time there have been a number of reports relating to headphones. The following bug report is for 10.04 and may give you some insight. You'll have to register to use Lanchpad.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/554959](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/554959)

I fixed it! Finally...

I ended up compiling the latest version of alsa (1.0.23), but I'm not sure if that was part of the final solution. The thing that had an immediate positive effect was modifying the **/etc/modprobe.d/alsa-base.conf** file and adding the following line at the end:

```
options snd-hda-intel model=alienware
```

---

### Post by fragos on 2010-07-07
Where did you get that configuration line?

---

### Post by xluryan on 2010-07-07
> **fragos said:**
> Where did you get that configuration line?

**LOTS** of searching. Then I found a list in the alsa source code with makes and models of sound cards. Luckily the only Alienware option they have was for my specific laptop model.

I just found an online version here: [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt").

More info here: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Don't forget you have to reboot each time you edit that file.

Check it out ;)

---

### Post by fragos on 2010-07-07
Thanks. You have been busy researching this one.

---

### Post by xluryan on 2010-07-07
> **fragos said:**
> Thanks. You have been busy researching this one.

I keep my laptop plugged into my stereo (obviously via the headphone jack). So headphones working is kind of a big deal...

Seems like there's constantly music playing from my laptop. The m17x has some pretty nice built-in speakers, but nowhere near as good as a full-fledged stereo system.

---

