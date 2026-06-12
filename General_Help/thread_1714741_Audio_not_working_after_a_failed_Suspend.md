---
title: "Audio not working after a failed Suspend"
date: 2011-03-25
forum: General Help
---

### Post by gnawingonfoot on 2011-03-25
EDIT: I found my problem--the box next to headphone box had been unticked, and I feel like a total doof for not having found that during my first two hours of trying to fix this.  But I could still use some help figuring out my suspend problems issue--I've heard constantly turning a compy on and off is bad for it somehow.


A couple days ago I attempted to put my computer into suspend mode.  When I used regular Ubuntu, this seldom worked.  My hard drive would continue spinning, and the computer would not come out of this state until I cut the power and restarted.  I thought it might be worth giving a try in Xubuntu, but I ran into the same problems, only this time, the audio would not work when I booted up.

I'm using the 64-bit version of Xubuntu, and this is a relatively fresh install (within the past two weeks) from the version 10.10 DVD, so I haven't had too much time to fudge up the settings yet, so I think it might not be entirely my fault.  (:  I've checked the hardware, and everything is plugged in and turned on, and I'm getting sound when I boot up Windows.

I may have done something afterwards, though.  My first attempt at fixing the problem was to follow [_these instructions_](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate), but I really didn't understand entirely what I was doing.  I tried fiddling around with the alsa mixer, but that didn't help me at all, and now it has even disappeared from the upper right-hand corner of my screen--on the toolbar. (If there's a way I could get that back and restore the default settings, I'd appreciate that, too.) [EDIT: I found alsamixer in the applications menu.]

I'd like to have audio working again, but I'm not really sure what's wrong or how to fix it.  I'm still reading through *Introduction to the Command Line*, but as my previous attempt to solve this issue shows, I'm not smart enough to be afraid of entering commands in that I completely do not understand (yet).  (:  I got a little bit of system information below, and if there's anything else relevant, I can provide that as well.  Many thanks for the help!

Processor: 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Audio Adapter: HDA-Intel - HDA NVidia

---

### Post by 3177 on 2011-03-25
in your system monitor, (I don't know where it is in xubuntu) go to processes and find alsa if your using it, but its probably pulse-audio. kill the process, then restart it. Hope this helps.

---

