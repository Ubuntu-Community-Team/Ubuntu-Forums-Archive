---
title: "What's wrong with this computer?"
date: 2012-06-11
forum: General Help
---

### Post by LifeTheHound on 2012-06-11
Computer crashes randomly with multicolored screen (usually a garbled, finely tiled mess of repeating pixels that were on the screen before the crash). Happens regardless of OS (that means Windows and Ubuntu). 

It's an AMD motherboard with NVIDIA 6150SE graphics, 3GB DDR2-669 ram, AMD Athlon 64 X2 6000+ CPU. What's wrong with the computer? Here are the tests I've performed:

1. Swapped monitors. 
2. Reformatted hard drive and installed fresh OS (multiple)
3. Ran memtest86+ 4.20 for nearly 3 passes (took hours)
4. Ran prime95 stress test in 64-bit, hi-ram SMP torture mode: about an hour
5. Changed BIOS settings to failsafe preset, disabled cool'n'quiet, SMART drive, acpi, all speed tweaks, and then locked fans to max, etc -- then did the reverse and redid all tests
6. Booted from SD card with acpi=off and video=vesafb vga=792 (to bypass all gfx acceleration and nvidia module loading; I can't remove the onboard GeForce chip)

All tests come out clean but spontaneous hard-freezes persisted, with the screen either glitching out with tons of random tiled colors (or pixel repeats) or freezing to black. No responses or interrupts were accepted at this point -- if the fans weren't set to max in the bios, they'd stop, too. Occurs regardless of activity or idle.

At first it seemed to me that it was a VRAM corruption problem in the GPU -- I've seen it before. Or perhaps a RAM problem, but all tests checked out. Temperatures stayed under 70C during use (including testing when they shot up from 40-ish). No overclocking was ever performed on this computer -- in fact, hearing terrible things about the nvidia chipset, I actually had applied a limiter to the GPU core freq (this limiter was accidentally removed around the time the crashes dramatically increased in frequency about 8 months ago -- but could be coincidence). 

No new hardware installed. Here are my next best guesses, but they're kind of random and some insight into whether the other components could still be going bad is appreciated.

1. motherboard (aww, #@!^$ -- please no!)
2. PSU (which would be odd since it also happens when idle with acpi on and low fan)
3. Flow joints and/or thermal jelly around CPU/GPU
4. ...RAM or GPU, still, because my tests were inadequate. 

Any suggestions or input? I really wanna know what to do with the poor rig, considering it was $700 new just a few years back and still races through its tasks... before it freezes.

---

### Post by Redblade20XX on 2012-06-11
From the sound of it, it looks like a gpu problem. Did you clean out the inside of the system?

-Red

---

### Post by LifeTheHound on 2012-06-11
> **Redblade20XX said:**
> From the sound of it, it looks like a gpu problem.

-Red

Since I removed the nouveau modules entirely and booted via framebuffer vesa via kernel string, KMS or modesetting couldn't possibly be occurring through the GPU, could they? The GPU was reportedly offline the whole time, from initrd before boot all the way to the freeze.

---

### Post by Redblade20XX on 2012-06-11
> **LifeTheHound said:**
> Since I removed the nouveau modules entirely and booted via framebuffer vesa via kernel string, KMS or modesetting couldn't possibly be occurring through the GPU, could they? The GPU was reportedly offline the whole time, from initrd before boot all the way to the freeze.

Sorry about the nomodeset part, thinking a little to quickly!

---

### Post by LifeTheHound on 2012-06-11
> **Redblade20XX said:**
> Sorry about the nomodeset part, thinking a little to quickly!

Haha, no problem; I like quick thinking! :) 

The inside of the system is dusty. I blew on it a bit (nearly choked, haha) -- how extensively do you mean? I've never seen a system produce such a...strange response in the presence of dust before. Usually the symptom of dustiness is overheating or, in extreme cases, failure to boot. I'll give 'er a shot, though. If it's not the dust, though, what hardware component is most likely faulty?

---

### Post by Redblade20XX on 2012-06-11
> **LifeTheHound said:**
> Haha, no problem; I like quick thinking! :) 

The inside of the system is dusty. I blew on it a bit (nearly choked, haha) -- how extensively do you mean? I've never seen a system produce such a...strange response in the presence of dust before. Usually the symptom of dustiness is overheating or, in extreme cases, failure to boot. I'll give 'er a shot, though. If it's not the dust, though, what hardware component is most likely faulty?

If you can, get an air can or something that will blow the dust away without moisture. I have a NVIDA 6150LE and dust caused the gpu to go crazy.
The dust cause heat build up on the on board gpu.

-Red

---

### Post by gn0m3boy on 2012-06-11
There seems to be an issue when installing Ubuntu and people usually click the install restricted extras option and *viola!* We end up with the garbled colors and freeze-up issue...

In fact this issue with nvidia is not uncommon as a quick Google search turned up these references:

[[COLOR="Blue"]Nvidia driver freezes my computer - nV News Forums[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=130431")

*The Problem is that randomly, once or twice a day maybe, my computer just freezes with a white,black,multi-colored screen that is all distorted, I have an on board Nvidia 6150SE Graphics Card.*

This is from 2009!!

And more recently in [[COLOR="Blue"]Ubuntu Forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1965820"):

*It wanted to install the Nvidia drivers (geforce 6100) like in the past. This time after install the log in screen comes up I log in then the screen goes black! I've had trouble with Nvidia drivers for the past five years and its always the same...*

Finally the best answer is in [[COLOR="Blue"]Ask Ubuntu[/COLOR]]("http://askubuntu.com/questions/106686/nvidia-geforce-6150-unity-3d-wont-work/106784#106784")
 
*Nvidia geforce 6150-unity 3d won't work..*

There seems to be 2 schools of thought going on here...either totally remove the proprietary drivers OR install them and add the  X-swat PPA to software sources and upgrade the drivers to see if that works...whatever you decide, let us know the results   
Thanks in advance...

---

### Post by UltimateCat on 2012-06-11
A long time ago I had to do a zero fill because I had such a bad virus on my hard drive.

I am not saying that you have a virus but it is possible.

I read a excellent book written by a very intelligent man-
" Upgrading And Repairing Pc's " By: Scott Mueller

Until I read a few chapters I was in the dark but this book may help

Best Regards

---

### Post by gn0m3boy on 2012-06-11
Almost forgot...Quick search on LaunchPad brought this up as well:

[[COLOR="Blue"]Partial screen corruption and poor performance on GeForce 6150[/COLOR]]("https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/764379")

This bug is from last year and is still as of 2012-02-03 22:34:19 being listed as 'incomplete'

The basic work around was not loading the proprietary drivers from nvidia...If at all possible I would get a different graphics card and not use the on-board graphics at all

---

### Post by LifeTheHound on 2012-06-12
> issue when installing Ubuntu and people usually click the install restricted extras option
> Nvidia driver freezes my computer
> The basic work around was not loading the proprietary drivers from nvidia

As I mentioned in the OP, the problem occured in Windows and in Ubuntu in vesa (all modules that spin up the card, including neuveau, are blacklisted and the PC boots in 1024x768 vga mode 792) without any video drivers aside from framebuffer. I have no proprietary NVIDIA driver on my system anymore, nor do I have neuveau. Happens even when I use vesafb. And Windows in safe mode.

It's odd that the descriptions of the symptoms you linked are uncannily similar to the ones I'm having even without any drivers loaded. ***Is it possible for these same symptoms to appear regardless of OS even if no graphics drivers are loaded (framebuffer)?*** If so, we may have our answer. Would buying a new card give me a new place to plug the monitor without going through the onboard v/out? 

> A long time ago I had to do a zero fill because I had such a bad virus on my hard drive.
Woah, a virus that rears up both in Windows and Linux even when booted entirely from USB pen drive? I did access a few video files on the main drive after mounting, but...

---

### Post by CatKiller on 2012-06-12
Problems in multiple OSs implies hardware. It could be a problem with the card, or elsewhere. The likely candidates to my mind are, in no particular order, faulty graphics RAM, blown capacitor, intermittent short or voltage spike. Check all over for blown caps (they'll look domed, cracked or have goo coming out of them) and check your motherboard stand-offs (the bits that keep the motherboard appropriately electrically connected to the case). Give it a good clean with compressed air in case you've got something conductive in there (using screws on cheap cases can fill the computer with little metallic ribbons which can cause all sorts of havoc. If you have a spare PSU you can swap in then that will help identify a potential cause.

---

### Post by LifeTheHound on 2012-06-25
Strangely enough, it appears to have been a usb wifi adapter. I thought I'd had everything screened or at least run without the peripherals, but confoundedly this wasn't the case until now. ;-)

Unless the problem recurs, I'll have to chalk it up to... none other than a silly USB wifi adapter. How is it the mobo completely locks up (regardless of OS) when the adapter goes down? The humanity!

Cheers,
Gabe

---

