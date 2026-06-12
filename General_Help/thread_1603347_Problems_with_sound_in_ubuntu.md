---
title: "Problems with sound in ubuntu"
date: 2010-10-22
forum: General Help
---

### Post by MangoFett on 2010-10-22
Hi guys and gals,

**Here's some background info:** Purchased a brand new Netbook last week (Samsung n130) and thought I'd set up a dual-boot to accompany the pre-installed Windows XP SP3, and after a bit of research I decided upon installing Ubuntu as my preferred Linux OS, which I believe at the time was and still is version 10.10.

**But the problem is:** When I attempt to watch flash videos (from Youtube for example) the video streams fine, but the _audio_ is very jumpy and skips back and forth every few seconds. Occasionally there are periods of say 10-15 seconds where the audio is ok.

The problem exists on both Firefox and Chrome, and is exclusive to Ubuntu.

Keep in mind that I'm an absolute novice when it comes to Linux/Ubuntu, etc.

Any help towards solving this issue will be greatly appreciated.

---

### Post by matt_symes on 2010-10-22
Hi,

What happens when you play audio that is not streamed? Is the issue a flash issue or an audio card issue? Try playing a local audio file and see what it sounds like. This will narrow it down.

Kind regards

---

### Post by MangoFett on 2010-10-22
Hi, thanks for your reply,

Seems that the problem is indeed local, playing a saved MP3 file produced the same problem.

I also noticed some sort of static (which isn't very consistent either) noise emitting my headphones which I had noticed before.

---

### Post by matt_symes on 2010-10-22
Hi

What is your sound chip. Open a terminal and type

lspci | grep Audio

Copy and past the output and post here.

Kind regards

---

### Post by alexandari on 2010-10-22
The noise in your headphones might be caused by some of your mic's (if you have such) boosted all the way up. Check your mixer's settings,tweak it a little see if there is any improvement.

---

### Post by MangoFett on 2010-10-23
**@matt_symes**

00:1b.0 Audo device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

**@alexandari**

I've tried to interfere with the built-in mic's while playing audio, but doesn't seem to have much effect on the audio quality (although I can only seem to access 'Sound preferences' as opposed to volume control).

---

### Post by MangoFett on 2010-10-23
The problem however is significantly worse when audio is played from the browser than directly from the HDD... trying installing latest flash many times

note: that I'm having no such problems on the Windows XP SP3 partition

---

### Post by MangoFett on 2010-10-23
bump.

---

### Post by matt_symes on 2010-10-23
Hi

I am no expert with the alsa subsystem. Could be a number of things that could be causing your issue. There has been issues with pulse audio, and your sound card has been problematic.

Some people have found that changing the setting of alsa mixer (open a terminal and type alsamixer) can reduce or eliminate choppy sound. (It may or may not help)

Also this is a very long thread. It starts along time ago but is maintained and the end entries are newish.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=choppy](http://ubuntuforums.org/showthread.php?t=205449&highlight=choppy)

I have never had any issues with sound so its not something i have ever had to research. However i am looking into it and i will post a solution if i can find one. Hopefully someone with more experience with alsa and pulse can also  help.

Kind regards

---

### Post by MangoFett on 2010-10-23
Much appreciated, I've read on many threads that adjusting these settings could help resolve the issue.

**Update:** Increasing pulseaudio priority to -20 (max) and Disabling hardware acceleration on flash seems to have significantly improved both local and browser audio output respectively... however I wouldn't go as far to say its a fix?

---

