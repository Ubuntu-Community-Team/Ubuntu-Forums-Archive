---
title: "More frequent freezes in Jaunty. Downgrade kernel?"
date: 2009-11-11
forum: General Help
---

### Post by tomasterisk on 2009-11-11
I was one of those who unwisely traded a stable Jaunty for a Karmic upgrade. After many problems with Karmic I finally went back to Jaunty- a clean reinstall.

But here is my problem: Jaunty is now freezing more and more. It was quite stable for me before, at least for a couple months. But now it freezes in a variety of situations; halfway through a video in Youtube, scrolling down in my email reader, even - once - leaving the computer unattended!

I have heard of some fixing their problem by downgrade their kernel just one notch,  from 2.6.28- 16-generic to 15. How does one do that? Are there any other ideas?

---

### Post by stans on 2009-11-11
I've had the lockup problem in Jaunty and it has followed to Karmic. Doesn't seem to be a solution for it... the bug report never did get a reply. I've chased dozens of posts that dead end, and responded to many requests for more info (dmesg, lsusb, etc.) that fizzle out and dead end.

---

### Post by Claus7 on 2009-11-11
Hello,

I think that since you followed the route to upgrade then the downgrade option does not exist I'm afraid.

What you could do is download the kernel you want via web and compile it yourself, yet I do not know how easy a task that is.

Are you sure that you are not facing hardware problems that causing you your box to freeze? It might be a ridiculous solution, yet have you checked any cables or have you cleaned up a little your pc? I'm saying so because twice I faced such problems and I solved them by cleaning the memory of my pc in combination of removing and putting it back.

Other that that, I was facing lock up problems in jaunty and karmic, yet with the latest updates of karmic (way before the final release) these have ceased. 

So in order to recapitulate:
if you have time check out even a more previous version than jaunty. If all of them are causing you freeze problems, then I would suggest that something goes wrong with your hardware. 
A clean install of karmic might put aside the freeze problems as well.

Regards!

---

### Post by tomasterisk on 2009-11-11
Thanks for the input but I don't think I want to do that again, reinstalling. I don't want to go over to Karmic since I know that it is possible (I just had it two weeks ago)  to have stable Jaunty. And I know it is possible to go back to a previous kernel, though maybe it is indeed complicated.

Some possible other clues for my situation:
1. On a hunch, I tried to change to desktop effects (the lower setting) but was told that I was not able to do this. I am only able to have the basic setting.
2. My "electric fish" screensaver doesn't show fish shapes at all, but just the streaks of their trajectories, as if the graphic can't keep up.

I may also look into another brand of Linux in see if I can't have dual boot, because I have things I really want to be doing here, not using my time always looking under the hood.

---

### Post by XCan on 2009-11-11
I would try to run a stability test. You could, for example, run as many instances of Mprime as the number of cores you have. But, I have to admit, I find Orthos (which is based on Mprime iirc, to be much more handy when run through Wine.

---

### Post by PostChache on 2009-11-11
I have this same problem after downgrading from Karamic to a fresh install of Jaunty. I have done Stress testing, RAM testing and even did a test to see if my Jaunty was installed right. I freeze up occasionally for no reason as well.

---

### Post by michaelzap on 2009-11-11
I started having frequent Jaunty freezes just before my Karmic reinstall as well. I found that disabling all desktop effects made it stable again, but of course that wasn't ideal. I have a Lenovo Y530 (Core 2 Duo and integrated Intel graphics).

You can get .deb files of many different kernel versions here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Installing them is as easy as downloading, double-clicking, and selecting the new kernel on reboot. I'm running the latest 2.6.32-RC6 on Karmic, and it's made all the difference to me. You could try an older kernel if you think that might help you.

---

### Post by PostChache on 2009-11-11
> **michaelzap said:**
> I started having frequent Jaunty freezes just before my Karmic reinstall as well. I found that disabling all desktop effects made it stable again, but of course that wasn't ideal. I have a Lenovo Y530 (Core 2 Duo and integrated Intel graphics).

You can get .deb files of many different kernel versions here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Installing them is as easy as downloading, double-clicking, and selecting the new kernel on reboot. I'm running the latest 2.6.32-RC6 on Karmic, and it's made all the difference to me. You could try an older kernel if you think that might help you.

Which one do I want to download? Like once I chose which version there's a lot of options. Sorry but I don't want to mess anything up.

---

### Post by michaelzap on 2009-11-11
> **PostChache said:**
> Which one do I want to download? Like once I chose which version there's a lot of options. Sorry but I don't want to mess anything up.

I haven't tried any but the most recent RC, and I downloaded the headers-all file and the headers and kernel files for my architecture (amd64) and that was it. You definitely don't need the source. Don't worry too much, since I don't think that you can hurt anything as long as you don't install over an existing kernel (which would only be a problem if you messed it up and no longer had a bootable option).

---

### Post by tomasterisk on 2009-11-14
> **tomasterisk said:**
> Thanks for the input but I don't think I want to do that again, reinstalling. I don't want to go over to Karmic since I know that it is possible (I just had it two weeks ago)  to have stable Jaunty. And I know it is possible to go back to a previous kernel, though maybe it is indeed complicated.

Some possible other clues for my situation:
1. On a hunch, I tried to change to desktop effects (the lower setting) but was told that I was not able to do this. I am only able to have the basic setting.
2. My "electric fish" screensaver doesn't show fish shapes at all, but just the streaks of their trajectories, as if the graphic can't keep up.

I may also look into another brand of Linux in see if I can't have dual boot, because I have things I really want to be doing here, not using my time always looking under the hood.

Hooray! I solved everything.

By just going back to good old - never let me down - Hardy Heron. I went ahead and dual-booted my Ratel Value (Hardy and Jaunty). No freezes, no glitches, nothing. There are hardly any differences in the features that I need so I think I will just stick here until the next long-term version comes (and even then I'll wait some).

---

### Post by jeb800e on 2009-11-14
If you press "Esc" right before Ubuntu shows up, you should get the GRUB screen. Choose an older kernel from there and your computer should boot up okay.

---

