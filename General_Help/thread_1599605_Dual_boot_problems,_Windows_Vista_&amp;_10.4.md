---
title: "Dual boot problems, Windows Vista &amp; 10.4"
date: 2010-10-18
forum: General Help
---

### Post by Boomerkuwanger on 2010-10-18
Hey guys,

I've been using Ubuntu for about a year now on my desktop, I have a dual boot grub loader for windows vista on one hard drive (with its own partition) and Ubuntu on another HD (with its own partition). Earlier today my girlfriend noticed the computer started up really slow, so being the quicker decision, I started up Ubuntu. She didn't use the computer for anything unusual, but after she finished I did update the computer using the Update Center. After coming back to the computer after roughly 2 hours the screen was blank and nothing was happening. I manually restart the computer. I restarted with intent to boot from Windows, however, the motherboard (intel) loading screen took an unusually long amount of time to pass; then when I tried to start Windows the computer gave me an error that just read "Read Error." After trying again, I wasn't even graced with this descriptive error. The screen remained blank.

The Problem is that I cannot boot my Windows partition; I don't need any data from it so I just wish to reinstall windows (if that is the best option). I currently am on my Ubuntu partition (on the same computer) which also seems to be having trouble. Every time I boot Ubuntu I am given a long list of errors, unfortunately I do not have them written down. I fear that if I reboot my computer I won't be able to get back into either OS.

So far, I've tried to boot from a Windows installation disc, but once it "Loads Windows Files" the computer has a Windows loading screen and goes blank. 

I don't really know what to do, please help!

---

### Post by matsuzine on 2010-10-18
Are you able to access the other HD from your linux partition, or is it unable to mount?

---

### Post by Boomerkuwanger on 2010-10-18
EDIT:

I am not able to see my windows hd partition on my disk utility manager.

---

### Post by matsuzine on 2010-10-18
I have a sinking feeling that what you're seeing is a bad disk.  I had two maxtor drives fail on me almost simultaneously a few years ago, they had the "read error" message on windows boot and were unaccessible from linux.  You may want to try a utility to check for drive failure  -- maxtor had a dos utility that allowed me to verify that my drive was toast.

---

### Post by Boomerkuwanger on 2010-10-18
Some updated information:

Like I said before, my computer does not recognize my main HD. I took apart my desktop and now only have the HD that is causing problems connected.

The error given to eventually is

Intel Boot Agent GE v1.2.42
Intel Boot Agent PXE Base code (PXE-2.1 build 086)

PXE-561: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent

No Bootable device-- insert boot disc... press key.

My HD is a Western Digital
MDL: WD1600AAJS Caviar SE



Edit:
I took out my second Hard Drive with my Ubuntu partition on it because I wanted to be 100% sure my problem was due to my main HD. I started up the computer with this Hard Drive alone [given the error above] and I put my Windows Vista Boot disk in the and to my surprise it recognized that it had a previous Windows Boot loader! Where before [When both hard drives were in the computer] the screen would just go black.
[COLOR="DarkRed"]Why this is important:[/COLOR] My Ubuntu partition/second hard drive, for whatever reason, was preventing my computer from entering the Boot menu/system recovery of the Vista boot disk. This is either due to dumb luck that [this time] the Vista disk decided to become recognizable, or that the grub loader has something to do with the boot sequence of my bios.

But this is just a hypothesis, if there are any real professionals laughing at this please don't hate :D

---

