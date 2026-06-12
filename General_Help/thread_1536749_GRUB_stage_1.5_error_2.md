---
title: "GRUB stage 1.5 error 2"
date: 2010-07-22
forum: General Help
---

### Post by mina299 on 2010-07-22
Hi, all. I've been searching all over the Internet for an answer for this problem, but with every single thread I go to, their problem is similar, but it's not mine: I'm not trying to install Ubuntu. I've been running it for well over a year, now.
 
My laptop has been overheating quite a lot and has crashed a few times because of it. I can't watch anime beacuse the picture lags and all I can hear is the sound of their foreign voices and goofy sound effects. I know that this is due to the heat. While I am taking steps to cool down the laptop, I can't help but wonder if it had something to do with my problem. Perhaps it is possible that the heat has damaged some of my hard drive, or some other hardware?
 
At any rate, I boot up my laptop, and I get the Toshiba screen with the option to hit F2 or F12, then I immediately see a blank, black screen with white letters. It says:
 
GRUB system1.5.
 
GRUB loading, please wait...
Error 2
 
And that's all it says. I have hit CTRL+ALT+DEL and hit F12 and F2 (obviously in rotation) and I poked around, but left without saving since I really have no idea what I am doing in there. I don't think there can be a problem with GRUB itself, since I have never screwed with it, so loading from a disk to begin screwing with it is probably a waste of my time. Does anyone out there know what the problem could be? Thanks for any advice. If this is covered and solved somewhere else, I appologize that I could not find it (I have been to so many different threads that were unhelpful and all dealt with OS installation), and I would appreciate a link to it if possible.
 
Thanks for your help!!

---

### Post by WorMzy on 2010-07-22
Error 2 is: "Selected disk doesn't exist", which leads me to believe that you have Grub installed to the MBR of a different disk to which you have Ubuntu installed; grub is being loaded by the boot process, and the first stage is failing to find the disk you've installed the other parts of grub to (where you've installed Ubuntu to).

Possible reasons for this: 1) you have your disks set up in a RAID array, and grub can't detect it, 2) you have removed the disk with Ubuntu installed on it, 3) the disk with Ubuntu on it has died, and isn't spinning, 4) one (or more) of the cables to the disk has become loose.

If it's none of the above, then boot into a liveCD and run the boot info script, then post the output file here, surrounded by code (# button/ [CODE[COLOR="Black"]][/COLOR]...[/CODE]) tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by mina299 on 2010-07-23
Thank you for your help!  I will take my lappy to the shop tomorrow for them to investigate for possible hardware failure.  I have a warrenty with stupid stickers on the back of the notebook, so I can't exactly remove them without voiding it... so I will make them check for me!  Then if that's what's wrong, then it's a good thing I randomly decided to backup everything on my laptop yesterday.  I can't imagine the panic I would be in right now if I hadn't.  What a coincidence!!!  Thanks for your help!  If this proves to be the problem, I will update as soon as I know!  It might be a few days before I see my laptop again.
 
Thanks again!
(I knew it was a possible hardware thing- it doesn't make sense otherwise!  I didn't tamper with anything that stores data.  I didn't tamper with anything at all!)
 
-The Mina

---

### Post by WorMzy on 2010-07-23
Does the place you're taking it to know how to use Linux, or are they mindless drones that don't actually know anything about computers, and think that reinstalling Windows is the best solution to every problem under the sky? :P

Before you resort to that, I urge you to try booting from the LiveCD (or USB) and running the boot script; failed hardware is only *one* possible cause after all, the others may be solved relatively easily, and, most importantly, with no extra cost to yourself!

---

