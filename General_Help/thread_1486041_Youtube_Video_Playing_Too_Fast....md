---
title: "Youtube Video Playing Too Fast..."
date: 2010-05-17
forum: General Help
---

### Post by lekozza on 2010-05-17
So, I've recently installed Kubuntu 10.04 on my Fujitsu Amilo laptop. Everything is working fine (after some manual intervention). Internet/Wifi is working, sound, video (youtube) all OK.

I then decided to install/compile the latest Kernel (2.6.34). I made no additional changes to the kernel, I just copied my current .config to the new kernel directory and started the full compile from there.

Booting into 2.6.34 initially appears to be OK - everything starts up the same, I still have wifi/internet access. But when I go to Youtube (or any other site with video) the video will play too fast, there is also sound distortion when there is disk access (moving mouse, loading other web pages, etc - all results in interference to the music/audio that is currently playing.)

I've gone back to the ubuntu kernel for now, but it would be nice to be able to use (and make changes) to the most recent kernel as long as this video/sound issue could be resolved. I did the same thing on my PC, but that works OK with the new, compiled 2.6.34 kernel. So the problem must be a sound/graphics driver problem with the laptop.

Anyone had the same problem?

L.

---

### Post by erjoalgo on 2010-07-21
Its a pulseaudio problem, I had the same issue. Try messing around with the sound options, in system->preferences->sound

---

### Post by casrenooij on 2010-12-07
> **erjoalgo said:**
> Its a pulseaudio problem, I had the same issue. Try messing around with the sound options, in system->preferences->sound

I had the same problem. On the output tab, if I select the HDMI device for sound output, youtube runs too fast. Putting it back to analog output solved it...

---

### Post by vonfreeware on 2010-12-07
> **erjoalgo said:**
> Its a pulseaudio problem, I had the same issue. Try messing around with the sound options, in system->preferences->sound

I have ubuntu 10.10 and I tried this advice.  Didn't know what I was doing just changed the first option I found and it worked.  Quickest fix I've ever had lmao!:D  **solved**

---

### Post by S13silvia on 2010-12-26
> **vonfreeware said:**
> I have ubuntu 10.10 and I tried this advice.  Didn't know what I was doing just changed the first option I found and it worked.  Quickest fix I've ever had lmao!:D  **solved**

Thanks for this!  Had the same problem, this fixed it immediately.  :o

---

