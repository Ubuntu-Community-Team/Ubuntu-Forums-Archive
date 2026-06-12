---
title: "Sound Settings. [9.10]"
date: 2009-11-08
forum: General Help
---

### Post by Vijfhonden on 2009-11-08
I am used to the Sound Menu on Windows 7.
you know it has the Enhancements thing
with
-Bass Boost
-Virtual Surround Sound
-Room Calibration
-Loudness Equalizer
-24-bit/96000hz

I was wondering if there was anything like that on Ubuntu?
I use Last.Fm so i can't really get a plug-in.

And I know that my Sound Blaster X-Fi Notebook Card does not work with Linux... [or i need to check on that]
But for the most part..is there anything like that on Ubuntu..or am I stuck with the Default Sound thing...?

---

### Post by kostkon on 2009-11-08
Install the
```
linux-backports-modules-alsa-karmic
```
package for some extra audio drivers and reboot. Your X-Fi should work after that.

---

### Post by Vijfhonden on 2009-11-08
> **kostkon said:**
> Install the
```
linux-backports-modules-alsa-karmic
```package for some extra audio drivers and reboot. Your X-Fi should work after that.

```
sudo apt-get install linux-backports-modules-alsa-karmic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-alsa-karmic

```

---

### Post by aniruddh12 on 2009-11-08
hi all...i am new to Kubuntu.....my problem is ...whenever i speak thru the mic ..i am able to hear my voice back again thru the speaker...i want to avoid this situation as it cause a lot of problem during tele-chat .....and worse i am not table to record my own voice :((....i tried various options thru alsa settings...but nothing happend....

bottom line is : How to stop the mic to speaker loopbacks ?

---

### Post by Scooter89 on 2009-11-18
Try doing a quick search within the Synaptic Package Manager.

---

