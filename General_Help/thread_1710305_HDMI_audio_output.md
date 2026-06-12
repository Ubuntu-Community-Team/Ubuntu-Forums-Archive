---
title: "HDMI audio output"
date: 2011-03-19
forum: General Help
---

### Post by unbuntunewb on 2011-03-19
Hello,

I just installed a nvidia 9500 gt with HDMI and I am not able to get audio out from the HDMI, how do I enable this?

thank you

---

### Post by bryanl on 2011-03-19
In system preferences sound look at the output tab. It will likely have 2 options with the internal sound system checked. The other is HDMI and you need to select it.

---

### Post by unbuntunewb on 2011-03-19
> **bryanl said:**
> In system preferences sound look at the output tab. It will likely have 2 options with the internal sound system checked. The other is HDMI and you need to select it.

I tried editing the output in the sound preferences from analog to digital and I get nothing

---

### Post by linuxman94 on 2011-03-19
You should have an option for the analog output and an hdmi output.  That is what i have running amd

---

### Post by unbuntunewb on 2011-03-20
unfortunately I do not

---

### Post by lidex on 2011-03-20
A lot of good info here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by unbuntunewb on 2011-03-22
I notice that when I go to the alsa settings my computer is reading my integrated sound card as opposed to the HDMI card I installed, how do I get it to read the card as opposed to the integrated one?

---

### Post by lidex on 2011-03-22
> **unbuntunewb said:**
> I notice that when I go to the alsa settings my computer is reading my integrated sound card as opposed to the HDMI card I installed, how do I get it to read the card as opposed to the integrated one?

Go to 'Sound Preferences', the hardware tab, and select that device and choose the correct profile.

---

### Post by unbuntunewb on 2011-03-23
under hardware my device is not there to configure

---

### Post by lidex on 2011-03-23
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by oooh on 2011-03-24
Here is my alsa information:

[http://www.alsa-project.org/db/?f=b2cc7d9f68a4a80f62351e11fbac7a8719cd936a](http://www.alsa-project.org/db/?f=b2cc7d9f68a4a80f62351e11fbac7a8719cd936a)

Same problem here, HDMI is not listed in sound preferences, and not listed either in 

```
aplay -l
```

---

### Post by lidex on 2011-03-24
> **oooh said:**
> Here is my alsa information:

[http://www.alsa-project.org/db/?f=b2cc7d9f68a4a80f62351e11fbac7a8719cd936a](http://www.alsa-project.org/db/?f=b2cc7d9f68a4a80f62351e11fbac7a8719cd936a)

Same problem here, HDMI is not listed in sound preferences, and not listed either in 

```
aplay -l
```

You need at least v. 1.0.23 of alsa to make that work. Follow the alsa-upgrade link in my sig.

---

### Post by kuvanito on 2011-03-24
this solves your problem:
turn your PC on and go to the BIOS
on the advance tab disable the On Board Audio and Enable the PCIE
now reboot and check for Additional Drivers
that is it. :popcorn:

---

### Post by JohnnyC35 on 2011-03-24
> **unbuntunewb said:**
> Hello,

I just installed a nvidia 9500 gt with HDMI and I am not able to get audio out from the HDMI, how do I enable this?

thank you

I had this issue with my built in hdmi on my ion f-e board. I found the fix on xbmc's forum (don't have the link now) but here's what I did.
after installing the video driver for it I then "sudo nano /etc/asound.conf"
and added the following
```

#Tweak for HDMI sound ON
pcm.!default {
  type plug
   slave {
       pcm "hdmi"
   }
}
```

I then went into 'alsamixer' and made sure that sp/dif was unmuted

I hope that helps :)

---

### Post by unbuntunewb on 2011-03-24
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

here is my alsa info

[http://www.alsa-project.org/db/?f=bf08e3faab307dffca2119db323c48d730704de4](http://www.alsa-project.org/db/?f=bf08e3faab307dffca2119db323c48d730704de4)

also there is this

nunya@nunya-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nunya@nunya-desktop:~$

---

### Post by lidex on 2011-03-24
> **unbuntunewb said:**
> here is my alsa info

[http://www.alsa-project.org/db/?f=bf08e3faab307dffca2119db323c48d730704de4](http://www.alsa-project.org/db/?f=bf08e3faab307dffca2119db323c48d730704de4)

also there is this

nunya@nunya-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nunya@nunya-desktop:~$
You need alsa 1.0.23 + follow the thread here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by oooh on 2011-04-03
Can not install the latest "linux-alsa-driver-modules", as they are not available for my headers 2.6.32.30 

What could I be doing wrong ?

(I added the repo ppa:ubuntu-audio-dev/ppa in order to do this)

---

### Post by lidex on 2011-04-03
> **oooh said:**
> Can not install the latest "linux-alsa-driver-modules", as they are not available for my headers 2.6.32.30 

What could I be doing wrong ?

(I added the repo ppa:ubuntu-audio-dev/ppa in order to do this)
It's not available for that version. Is that the latest kernel release for your install? Other options are upgrading alsa directly (link is in my sig) or using a later kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by oooh on 2011-04-04
Ok, now running Maverick Meerkat 2.6.35-generic

Still unsolved, though I am running alsa 1.0.23, following also the instructions in:

[http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+audio&page=1](http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+audio&page=1)

Why dont I get my HDMI listed in aplay -l yet ?

---

### Post by lidex on 2011-04-05
> **oooh said:**
> Ok, now running Maverick Meerkat 2.6.35-generic

Still unsolved, though I am running alsa 1.0.23, following also the instructions in:

[http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+audio&page=1](http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+audio&page=1)

Why dont I get my HDMI listed in aplay -l yet ?

Follow the link in post #16. If you don't understand something ask for help there. TJones has a much better grasp on this.

---

