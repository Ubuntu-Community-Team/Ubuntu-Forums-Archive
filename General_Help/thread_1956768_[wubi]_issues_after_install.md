---
title: "[wubi] issues after install"
date: 2012-04-11
forum: General Help
---

### Post by Sepheara on 2012-04-11
Hello All (long time reader, first time poster),
 
My husband and I build and upgrade our own machines, I don't think I've owned a "pre-built" pc since middle school. I have an interesting hard drive set up that has noit changed. I have a 1 terabyte raid0 that I use for my games. I have a 1 terabyte external hard drive for mostly media, art, and my website design stuff. I think have a 1 terabyte hard drive that I partitioned (mostly) in half. On one haf I was running Windows 7 and any critical/importent windows related porograms. and on the other half I was running Kubuntu. I had a lot of trouble installing Kubuntu initially so I ended up using Wubi and was very happy with it. Everything was all like, peaches and cream. 
then we upgraded:
 
Old Machine
ASUS M3N72-D AM2+/AM2 NVIDIA nForce 750a SLI HDMI ATX
AMD Phenom 8450 Toliman 2.1GHz Socket AM2+ 95W Triple-Core Processor 
8gig of G SKILL 240 pin DDR2 RAM
NVIDIA GEFORCE 8800 GTs/ NVIDIA GEFORCE 220 SERIES
---------------------------------------------------
New Machine:
ASUS Sabertooth 990FX AM3+ AMD 990FX SATA 6 Gb/s USB 3.0 ATX AMD mobo with UEFI BIOS
AMD FX-8120 ZAMBEZI 3.1 socket AM3+ 125W Eight-Core processor
8gig G SKILL SNIPER SERIES 240 pin DDR3 RAM
NVIDIA GEFORCE 220 SERIES / NVIDIA GEFORCE 400 SERIES
 
After the upgrade I had to reinstall windows, so when I did, the partition remained, and I simply reformated the partition that had Kubuntu, re-downloaded Wubi, and set about installing it all over again. When it got to the part to re-start my pc I did, and selected "Kubuntu" off my boot manager, watched the pretty splash screen, and then nothing. I got a black screen. I kinda waited and /poked at it, and nothing happened. So I went to google and basicly what I thought the problem was, was this:
 
all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts, but on some cards this doesnt work properly and you end up with a black screen. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. Especially NVIDIA Cards loading a non-propriatery driver. So I tried the reccomended solution of booting and editing to add the "nomodeset". However I still get a black screen. 
 
Both before and after the nomodeset I would see the splash screen (and after the nomodeset I could see the difference!) but the screen would go black indefinitly after the splash either way. If I hit ctrl+alt+del the screen would come back on and show all the stop process/log off status text. So I really think it's with my video card but I'm not sure what I can do about it. I really loved doing everything in Kubuntu and only having to use windows for gaming :( 
 
I work as tech support so I tried to include relevent details, but if I missed anything (actually maybe I wrote too much 0.0 ) please just ask or let me know. I would consider myself between a beginner and a novice level (been playing around with various bootable version of linux on my netbook for awhile, and learning a lot) but I'm not super amazing yet.
 
Thanks again.

---

