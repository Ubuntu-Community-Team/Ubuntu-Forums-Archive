---
title: "Why does X do this? :)"
date: 2010-11-19
forum: General Help
---

### Post by Mmmbopdowedop on 2010-11-19
I've seen this happen many a times, I think it's X, but it'll randomly freeze or just throw a patchwork style image of my history on the screen as the image shows (sorry for the blur, Blackberry camera sucks on my phone);

[[IMG]http://img258.imageshack.us/img258/2695/img00019201011162140.th.jpg[/IMG]](http://img258.imageshack.us/i/img00019201011162140.jpg/)

I just don't understand why/how it's showing my Windows 7 Desktop in chunks when it's on a completely seperate partition, is it just throwing out random memory addreses from the video card? Isn't it good practice to clear that before using it or even at boot? :)

I don't know, it just seems odd and sometimes scares me. :)

---

### Post by NightwishFan on 2010-11-19
I would downclock or replace your graphics hardware. That is not normal. If it is normal I am wrong however I have never seen X do that. It might be a hardware issue.

---

### Post by tgalati4 on 2010-11-19
Yes, X can misbehave.  What type of video card?  In a terminal post the output of:

lspci | grep VGA

Too much gaming on the Windows side perhaps?

Try running a few benchmarks and see if it's bus problem:

sudo apt-get install phoronix-test-suite

---

### Post by Joeb454 on 2010-11-19
I agree with NightwishFan - it sounds like it might be a hardware issue.

Have you overclocked the GPU, or altered it in any way since you purchased it?

**Edit:** Moved to General Help

---

### Post by Mmmbopdowedop on 2010-11-19
I haven't touched my Graphics card's settings at all; it happened with my previous one which was an 8500GT, my current is a;

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

I thought it was normal, it used to happen all the time when Compiz would crash back in the day. :o

And I doubt it's because of over-gaming, I barely play with my wobbly windows and that's about it aha. :P

---

### Post by Decatf on 2010-11-19
I don't think it's a hardware issue. This used to happen with the open source ATI driver during boot.

---

### Post by dcstar on 2010-11-19
> **Pey Tudor said:**
> 
...........
I just don't understand why/how it's showing my Windows 7 Desktop in chunks when it's on a completely seperate partition, is it just throwing out random memory addreses from the video card? Isn't it good practice to clear that before using it or even at boot? :)


If you had used Win 7 before booting Ubuntu - without a power off - then Win 7 may have set things in the video card that were not fully reset before Ubuntu tried to use it.

If this is the case then it is probably a Linux driver issue that is not resetting/initialising your video card correctly at Linux boot (so you see old Windows screens etc), and since those Nvidia drivers are supplied by Nvidia there may not be a lot that you can do except try to manually install the latest one that is compatible with your hardware.

---

### Post by NightwishFan on 2010-11-19
Actually that may be likely. I was a bit disturbed because it showed windows, which may have been an odd bug from overheating.

---

### Post by asmoore82 on 2010-11-19
If this is not an issue that you can reliably reproduce or "trigger"
I would guess that it is bad/failing video RAM.

---

