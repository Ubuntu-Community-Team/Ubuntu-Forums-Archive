---
title: "Skype on ubuntu"
date: 2009-12-26
forum: General Help
---

### Post by cdneve on 2009-12-26
Hello everyone, I don't really know whether this is a question on ubuntu or Skype, but the fact is that Skype doesn't work 'correctly' when I use it... I can see and hear the person I'm talking to, but he can't see me, however he can hear me.
Am I doing something wrong ? Or is it normal and easy to solve ? :confused:

... Thanks

---

### Post by spiderbatdad on 2009-12-26
can you tell us what hardware setup you have, what sound card, and what version of skype?
So, what type computer? What result from terminal command ```
 aplay -l 
```
And skype version with something like:
```
apt-show-versions skype
or
dpkg -l skype

```

---

### Post by cdneve on 2009-12-26
My type of computer is hp < COMPAQ < Evo N410c

My result from terminal command to : aplay -l  is :

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And my skype version is (I hope this is the right answer...)

SkypeTM 2.1 (Beta) for Linux


:p

---

### Post by spiderbatdad on 2009-12-26
start by making sure capture is up in alsamixer...something like this:
```
alsamixer
#Then hit tab key. Right arrow to move to capture. Up arrow.
#ESC to exit
```
Try test call. Report back if error.

---

### Post by abhiramcr on 2009-12-27
Hi!

I've only been using Linux for about a week now, and installed skype today. When i try the test call, i get an error saying there's a "problem with audio playback".

Running the command
**$ aplay -l**
the output is
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the Skype version i found using the command
**$ dpkg -l skype**
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version                Description
+++-======================-======================-
============================================================
ii  skype                  2.0.0.72-1             Skype - Take a deep breath

I checked around the forum for a while, and found some help on the alsamixer settings and tried them. However, this does not seem to fix the problem either.:(

any help to get on with the problem will be greatly appreciated.

-Abhi

---

