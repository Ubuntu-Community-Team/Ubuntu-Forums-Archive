---
title: "Is this a case of hardware failure?"
date: 2011-03-29
forum: General Help
---

### Post by Slick908 on 2011-03-29
Okay, so I have this computer that was purchased with Windows Vista on it. It stayed that way for a few years now, but recently it started freezing on what appeared to be a random schedule. However, soon the problem became much less random. It would freeze only minutes after boot-up. Now when I mean freeze, I mean more of a complete lock up. The screen elements like the clock, and even the mouse cursor would stop functioning altogether. Ctrl + Alt + Delete would not work either. 

My solution to this problem was to simply boot-up an Ubuntu live CD, backup my stuff, and then reformat and clean install Windows via the recovery disks. All of this worked without a hitch until after the Windows Vista first time setup wizard (where you choose your timezone, create a user account, etc.). It was then when I realized this freezing problem persists. During the "optimizing system for your hardware" phase the computer froze.

I knew It was frozen by the way that little shine effect in the progress bar was halted (that doesn't normally happen). However, to rule out the fact that the computer was just taking an unnecessarily long amount of time I left it to run overnight. In the morning -- no progress. It was at this point I started to consider hardware failure. To test this I plopped my freshly created Ubuntu 10.04 live CD into the drive to see how long that could run before freezing. I thought that if Ubuntu could go on without freezing then maybe it might be another issue.

Oddly enough, I ran Ubuntu off the live CD for almost a week without freezes. So then I figured that I should just install it on the hard drive just in case that I was missing something. Two weeks later and Ubuntu is still working perfectly. Therefore, what I want to know is if this is really a hardware issue, or some other thing I'm not seeing. 

Also, during this time I have run hardware diagnostic tests like Memtest86+, and the S.M.A.R.T hard drive tests (both short and extended). They all passed.

---

### Post by lithopsian on 2011-03-29
Might be a hardware issue but more one of compatibility than failure.  If every aspect of Ubuntu works flawlessly then most likely Windows is at fault, not your hardware.  Possibly there is some obscure (broken) bit of hardware that isn't being used under Ubuntu, but who cares if it works.

---

### Post by Slick908 on 2011-03-29
Could this obscure piece of hardware really do that? Also, as I have stated the computer was purchased pre-loaded with Windows Vista. It doesn't make sense that It would just stop working for no reason. And I can't leave Ubuntu on this machine forever, because it is not mine. I just offered to fix it for the family member who does own it. Slabbing Linux on the machine with no idea as to why it's working over windows and calling it a day is a bit lazy. In addition, this particular family member requires access to certain software applications not available on Linux.

---

### Post by lithopsian on 2011-03-29
Might not make sense, but that's what happened.  Maybe your video card is playing up and Windows wants to use some fancy function on there that Ubuntu doesn't bother with.  That's just an example, there's loads of stuff going on inside these things.  I have no clue what you might have updated in Windows or how you are reinstalling it, and I'm not really interested (or capable!) in debugging Windows.  All I'm saying is that if Ubuntu runs smoothly then there is nothing major wrong with the hardware.  Maybe one day you'll install something and find a glitch, but until then you might have more luck diagnosing the problem at a Windows forum.

---

### Post by Hedgehog1 on 2011-03-29
I had an issue like this that was caused by an updated video driver (for an ATI Card) in XP.  Until I reverted to a ***much older*** version of the video driver, it acted up.  With the a 6 month older driver, the older ATI card was happy again and the issue stopped.

Just a thought -

***The Hedge***

:KS

p.s. I think the Ubuntu running fine does indicates the hardware is sound.

---

### Post by bdoe on 2011-03-30
Windows Vista (and 7) use a compositing engine that makes pretty heavy use of the graphics card. Ubuntu also uses a compositing engine (Compiz), but by default, this is turned off. If Vista can't install or boot without locking up, this may well be a graphics card issue. You can enable compositing on Ubuntu by going to System > Preferences > Appearance, then going to the Visual Effects tab and clicking "Extra" (Note: This may require proprietary drivers, depending on your graphics card). This is a good way to test to see if placing your graphics card under load causes your problem or not.

If you determine your graphics card is to blame, it might be worth opening up your computer and blowing out or vacuuming out all the dust and debris in it. Pay particular attention to your CPU heatsink/fan, and the heatsink/fan on your graphics card.

---

### Post by Duncan Williams on 2011-03-30
It could be a number of things:

Definitely carefully vacumn and toothbrush all components and cards etc in the box. (inc the motherboard)

Check your dram settings (ram speed) are correct in the bios. (any incorrect settings will cause crashes and lock-ups)

Check all your main drivers (use driverscan or similar - only update from manufacturers site)

If you have fully formatted your drive before re-installing - ok
If not then it may be malware - 
run some scanners - [http://my.opera.com/internetsecurity/](http://my.opera.com/internetsecurity/)

As stated you may have a malfunctioning component that ubuntu is not using.

If you have to give the machine back with windows - XP (sp3) is the most stable, anyway.

---

### Post by Mark Phelps on 2011-03-30
Freezing up in Windows could definitely be a heat issue -- and the recommended cleaning approach should take care of that.

However,  it's also generally true that Windows OSs (especially Vista) become degraded over time due to a variety of issues -- disk fragmentation, Windows Updates, malware of various kinds.

If you have the means to restore this machine to its original state, then I would do that.  You will then likely be ASTOUNDED by how quickly it runs and how reliable it becomes.

---

### Post by Duncan Williams on 2011-03-30
If you want to clean up windows, try a few utilities.
as in:
ccleaner
wipe
baku
eusing registry cleaner
windows registry repair
diskmax

Run all of them:
available [here]("http://my.opera.com/internetsecurity/blog/2011/02/23/free-anti-malware-and-other-applications")

---

