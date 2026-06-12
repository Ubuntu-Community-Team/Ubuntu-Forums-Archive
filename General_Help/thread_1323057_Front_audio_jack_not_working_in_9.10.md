---
title: "Front audio jack not working in 9.10"
date: 2009-11-11
forum: General Help
---

### Post by varunmagical on 2009-11-11
Hi,My front audio jack is not working.
It used to work in all previous versions of ubuntu. I thought it was a bug in beta of karmic, But now I have installed fresh new version, still it isnt working.
I tried booting from live CD of 9.04 & its working fine!

---

### Post by varunmagical on 2009-11-11
help please!

---

### Post by varunmagical on 2009-11-25
I have downgraded to Jaunty Now the problem is with karmic!
Is anybody here having same problem?

---

### Post by juliobahar on 2009-11-28
I've just recently discovered this issue after a couple of weeks of not using my front headphone jacks which was working so fine even after upgrading from Jaunty to Karmic. 

It is just because I'm moving my place I sent my home theatre that was connected to the back jacks of my computer to the my new home. Yet back here for not having any speaker but a headphone I realized that they aren't working as they were before on front jack. No issues with back jacks though

I tried to fiddle around with pulseaudio and alsa, but a still can't find where the problem is exactly.

I also would appreciate anybody's help.

---

### Post by Vaphell on 2009-11-28
Some details about hardware would be a nice start. There is no substance in the posts above.

---

### Post by juliobahar on 2009-12-03
> **Vaphell said:**
> Some details about hardware would be a nice start. There is no substance in the posts above.

This is my hardware info
```

xxxxxxxxxx@xxxxx-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Vaphell on 2009-12-03
searching 'vt1708b' on the net would be a good way to go

try to read this, maybe there will be some clues
[http://ubuntuforums.org/showthread.php?t=1291112&highlight=vt1708b](http://ubuntuforums.org/showthread.php?t=1291112&highlight=vt1708b)

---

### Post by juliobahar on 2009-12-04
> **Vaphell said:**
> searching 'vt1708b' on the net would be a good way to go

try to read this, maybe there will be some clues
[http://ubuntuforums.org/showthread.php?t=1291112&highlight=vt1708b](http://ubuntuforums.org/showthread.php?t=1291112&highlight=vt1708b)

Thanks pal this solved my problem. Independent HP was off. I was able to switch it back on again using alsamixer through terminal. But could do it through gnome-alsamixer.

Wonderful work.

---

### Post by dreaswar on 2009-12-05
Hi, 

I have the same problem in my DESKTOP

Speaker works well from back jack
Head phones do not work out of front jack, neither does the microphone in the head phone

Head phones were working fine till i upgraded to Jaunty a few days back from 9.04. 

I did'nt understand what is meant by enabling independent HP, there seems to be no option by that name under the volume controls. 

I have also tried editing the modprobe.d/alsa.conf files and also adjusting the controls in alsa mixer through the terminal.. to no avail

please find below the aplay -l

```
dreaswar@dreaswar-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


Please help.. 

Thanks in advance..

---

### Post by dreaswar on 2009-12-05
> **juliobahar said:**
> Thanks pal this solved my problem. Independent HP was off. I was able to switch it back on again using alsamixer through terminal. But could do it through gnome-alsamixer.

Wonderful work.

Hi, What do you mean by enabling Independent HP ? 

i could not find such an option under the volume control in my Karmic

Please refer to my post above for the aplay -l

Thanks for the help :D

---

### Post by shivankgandhi on 2010-04-01
I downloaded ALSA Mixer and did upgrade ALSA script 
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137). Worked for me ;).

---

