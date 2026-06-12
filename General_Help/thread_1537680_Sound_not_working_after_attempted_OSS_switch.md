---
title: "Sound not working after attempted OSS switch"
date: 2010-07-23
forum: General Help
---

### Post by snowmanman on 2010-07-23
I followed this guide: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) to try to switch to OSS. Now the sound doesn't work at all. How do I undo these changes and switch back to ALSA?

---

### Post by lidex on 2010-07-24
What is the output of this command:
```
dpkg -l | grep "OSS"
```
Use a Terminal="Applications->Accessories->Terminal"

---

### Post by snowmanman on 2010-07-24
> **lidex said:**
> What is the output of this command:
```
dpkg -l | grep "OSS"
```Use a Terminal="Applications->Accessories->Terminal"

This was the output:
```
alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
rc  libsdl1.2debian-oss                  1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and OSS options)
ii  linux-sound-base                     1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems

```

---

### Post by lidex on 2010-07-24
OK try this. In a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get remove libsdl1.2debian-oss
```

```
sudo apt-get install linux-sound-base alsa-base alsa-utils 

```

```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio pavucontrol paprefs

```

**Reboot**
Now run this command:
```
gstreamer-properties
```
and change your defaults to auto

---

### Post by snowmanman on 2010-07-24
I tried all of that and still nothing. I still get sound from Youtube, so I guess Firefox can somehow get sound.

According to Dell.com I have [SIZE=3] [SIZE=2]ADI 198x Integrated Audio. If that's helpful.

Thanks for helping so far.
[/SIZE][/SIZE]

---

### Post by pori.niki on 2010-07-24
Hi!!
 
I have a same problem!!

I have sony vaio VPCEA16FG laptop and also i have updated UBUNTU 10!!
but also i have no sound at all!!!
I heard some body that the drivers are new and there in no packages for them.
I am new in Linux.
is there any thing to help me!???
PLZ help Me.
tnx.

---

### Post by snowmanman on 2010-07-24
I ran
```
aplay -l
```

and it gave me this output if it's helpful:
```
aplay: device_list:223: no soundcards found...
```

Maybe I need to reinstall drivers?

---

### Post by lidex on 2010-07-24
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by pori.niki on 2010-07-31
I did What u said And now what???????;)

---

### Post by MCVenom on 2010-07-31
@pori.niki
You two don't have the same problem; OP is trying to switch to another sound API/server(?), while you are simply having problems with Ubuntu's default configuration (no sound, specifically). 

You need to start a seperate thread. When you do, please explain your problem clearly and concisely, preferably in proper English (no IM/SMS abbreviations), and without the excess punctuation.

---

