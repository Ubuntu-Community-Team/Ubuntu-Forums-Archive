---
title: "how do fix the sound problem in firefox?"
date: 2009-07-22
forum: General Help
---

### Post by chipsy on 2009-07-22
i'm only having this problem in firefox everything else work great :D
 [EDIT]
I'm using ATI radeon HD 4870 and my HD TV.
I don't no if I've done this correct but I've uploaded the image so you guys can help
[ATTACH]122191[/ATTACH]

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chipsy@chipsy-desktop:~$


```thanks ^_^

---

### Post by Greenwidth on 2009-07-22
For upgrading I would recommend Ubuntuzilla:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by chipsy on 2009-07-22
thanks for the reply but I need to know how to fix the problem with the sound ^_^

---

### Post by vishalag on 2009-07-22
Do you have sound problem only in firefox or whole ubuntu?

If it is only firefox..I think it is due to gnash which has very bad sound. If it is whole system try adjusting sound preferences.

---

### Post by lovinglinux on 2009-07-23
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

Also check the Troubleshooting section for a possible solution to your problem.

---

### Post by kostkon on 2009-07-23
Open a terminal and give this command:
```
aplay -l
```
and post the output here.

---

### Post by chipsy on 2009-07-23
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chipsy@chipsy-desktop:~$ 

```

---

