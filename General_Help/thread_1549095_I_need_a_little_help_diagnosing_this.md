---
title: "I need a little help diagnosing this :/"
date: 2010-08-09
forum: General Help
---

### Post by DerRosaElefant on 2010-08-09
Hello again everyone!

I'm having a bit of an odd issue. I have been having it since I first installed 10.04, I can't say if it existed in previous versions of Ubuntu as I never had them on this laptop. But I can't quite diagnose what is causing this, even after multiple searches through the forums and google. 

After a fresh install, everything works great for the first day or so. But after that, whether the computer has been turned off, put to sleep and woke, or even just left on for a few hours, this issue pops up, and I've found no way to resolve it but to reinstall, and obviously, I can't install once a day. After about 30 seconds idle, if I move the mouse, there is a major stutter. At first I thought it was just the mouse/cursor itself.I did numerous searches, finally finding some people with that issue. Though apparently the cause and fix were not a match for me. But last night, watching a video in VLC, I noticed that the video stuttered as well, so it's not just the mouse, but the display as a whole. As long as I keep the mouse moving, it will not stutter, but if it stops for that length of time, every time, it does it.

I've searched and come up with several completely unrelated but similarly described, problems. But I have yet to find a fix, and am completely clueless as to where to even begin looking for a cause and a fix. Restarting it does nothing, it happens regardless if the computer is running no programs, or multiple programs. The audio doesn't stutter even when the video seems to. As I said, the only thing that seems to stop it (and it's only temporary) is to completely wipe and reinstall. I'd appreciate any help that anyone can offer! :)

Edit: 
Also, if it helps/matters at all, this is an Acer Aspire 7740 Laptop running Ubuntu 10.04 64bit
Intel i3 2.13Ghz 
upgraded to 8gb of RAM
320GB

---

### Post by corrytonapple on 2010-08-09
Maybe a cable is loose on the inside connecting to the monitor. You could try installing 9.10 and see if that works.

---

### Post by DerRosaElefant on 2010-08-09
Thanks for the reply! :) 

Sorry, I guess I should have mentioned, this problem only exists in Ubuntu, also. In Windows, everything works 100% perfect. So I know it's not a hardware issue at all. (well, it might be hardware in the sense of how it relates to Ubuntu, but there are no failed/damaged components)

I'll give 9.10 a try if I reinstall again today/can't find any other possible way of fixing it :) (it will be really hard to force myself to downgrade that much :P )

---

### Post by bergfly on 2010-08-09
I would start to look into the graphics card. What model card are you running? That is a good spec machine otherwise, so you really should not see any performance issues. 

Also, if you turn off enhance desktop effects, does it improve things?

---

### Post by corrytonapple on 2010-08-09
You are only downgrading one version. It should still have support for about two more years.
> **bergfly said:**
> I would start to look into the graphics card. What model card are you running? That is a good spec machine otherwise, so you really should not see any performance issues. 

Also, if you turn off enhance desktop effects, does it improve things?
Please note the previous post.

---

### Post by JazzTrmpter on 2010-08-09
I had a similar problem... However, I was on a desktop pc and running Windows XP.  I upgraded my computer with more RAM and a new hard drive, and was having problems with the entire computer freezing for a split second, each couple of seconds.  The mouse, audio, and CPU locked up for a split second.  

The problem was my power supply.  I know you said it is most likely not a hardware issue, and it probably is not if everything works fine in Windows.  However, my power supply was not enough to have two hard drives and all the other drives as well.

---

### Post by DerRosaElefant on 2010-08-09
Yes, I know I'm only downgrading one version, I just meant losing some of the features of 10.04, and all. But it is worth it if nothing else to just try to see if it's related to 10.04 alone. I'll try this as soon as I can.

As for the graphics card, I can't find any more details other than "Intel Graphics Media Accelerator HD 1754MB DVMT" I'm not sure what Ubuntu requires or which cards are best, though as far as I know changing display adapters in a laptop is virtually (if not) impossible? Turning off desktop effects makes no difference.

And thank you for that suggestion as well! I guess upgrading RAM might have done something, though I did try going back to the factory 4GB and it seemed to make no difference either. And as far as the power supply, is that even possible to change in a laptop? But yes, it works fine in Windows 7, so I'm not necessarily in a rush to get the laptop working in Ubuntu... Though I don't want to use Windows :P 

Thanks again guys! :)

---

### Post by corrytonapple on 2010-08-09
No significant features are lost if you just email and browse the web. Also, congratulations on spilling the beans. Now pick them back up so they can be measured and roasted.:p

---

### Post by DerRosaElefant on 2010-08-10
Just an update/bump :)

9.10 has the same issue, though 10.10 alpha, the issue does not exist (and also, the sound issues I had in 10.04/9.10 and had to go through quite an ordeal to fix, are working properly out of a fresh install of 10.10) so I guess they have updated some drivers with 10.10

I guess I can wait until 10.10 is released for this to be fixed, though if anyone has any ideas, I'd really love to get this working right before then :P 

Appreciate any help and all the help already offered! :)

(lol and thanks for the congratulations on spilling the beans :P )

---

### Post by sydbat on 2010-08-10
Just a quick question - how have you installed Ubuntu? Via wubi (installed as a program inside Windows)? Or as a separate install in it's own partition (booting from the CD)?

Regardless, it is likely because of the Intel video not having a compatible "proprietary driver" (which would be found under System > Administration > Hardware Drivers).

---

### Post by ed-koala on 2010-08-10
This may not be your problem, but I have heard that Intel graphics have some issues in Ubuntu ... but exactly which Intel drivers I'm not sure.

You may want to look this up and see if it could be what's causing your troubles.  I did a quick look but didn't find it, but I know a more thorough search would.

VERY strange though that a full computer restart doesn't fix things.  That means, to me, some setting is being saved that is causing the problem(s).

---

### Post by DerRosaElefant on 2010-08-10
Booted from the CD and it's installed on it's own partition.

Thanks for the info on the intel adapters! I'll do some searching for that more specifically when I can. And yeah, it is very strange that a restart doesn't fix it :/

---

### Post by ed-koala on 2010-08-10
I almost bet money this is what is happening ... On a fresh install XXXX is the default driver/setting for something.  Once you run things once, it changes XXXX to something specific to your PC ... graphics driver or setting is most likely ... so even when you reboot, it reads the problem setting and it never changes from there on, causing a reinstall to fix.

If you ever do another reinstall, here's a way to check something.  Do NOT do any upgrades after reinstalling.  Reboot right away, maybe 2 or 3 times, before doing upgrades, and see if the problem returns only after doing updates.  If you always did the upgrades before rebooting THAT may be where the issue is, narrowing things down a little.

---

