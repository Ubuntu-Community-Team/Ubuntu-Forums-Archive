---
title: "boot problem with karmic 9.10"
date: 2009-11-02
forum: General Help
---

### Post by charonred on 2009-11-02
I'm still using Hardy 8.04 32 bit, but have installed 9.10 64 bit as I'm in the process of moving over to it.

I boot different OS's but the PC isn't set-up to 'multi boot' as such. Each OS is on it's own drive and was installed with all other drives disconnected so the entire grub boot loader is on the relevant drive.

Currently I have BIOS set to boot 9.10 as first drive; if I want another drive/OS to boot, I just hit F12 when booting the PC, and then choose which drives loads - easy, been doing this for a few years now.

Trouble is after I go into Hardy (which is often), when I reboot to 9.10, it loads but after the initial logo displays, the screen just goes blank, so I have to reset the PC 2 or 3 times before it loads properly ?? Occasional I get a brief message about something fails to load blah blah blah before it goes to a black screen.

However, once it has loaded properly, then Karmic behaves itself on each subsequent reboot; but if I elect to boot Hardy, and then go back to Karmic, the story repeats itself - what gives ?

---

### Post by nemiux on 2009-11-02
Do you also have windows system? You can try to set multiboot,  computer-->properities -->advanced --> startup and recovery -->
Press to edit boot.ini, it should look something like this
[boot loader]
timeout=8
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"
I think you should be able to boot it now

---

### Post by Kyle.Gant on 2009-11-02
hello! i am haveing a very similar problem to this, except that i didnt need to boot into my other OS (win xp) before i had the exact same error, and now i cant get into 9.10 AT ALL. also, i'm a bit slower with computer stuff, so please help!

---

### Post by charonred on 2009-11-02
nah Nemiux, I don't have a multi-boot system; I just have different OS's complete with their own bootloader on their own hard disk - thanks for instructions (I'll keep for reference, some friends are still using Windows), but the last thing I'd want to do is rely on Windows to handle booting of Linux OS's.

The disk with 9.10 on it is the disk set to load by default, but if I hit F12 key, I can then choose another disk to load from - it saves all the complications of partitioning drives and having one disk with a bootloader (grub, ntloader or whatever) on it that points to other disks/partitions - if one OS dies, it doesn't affect any other disk or OS. 

I'm just want to know why 9.10 has such a hard time loading after the PC has used another OS on another disk. I never had the problem with Jaunty; I could default boot the disk with Hardy on it, or choose the disk with Jaunty, or the disk with XP (not used much); and when finished, I simply reboot to another disk and OS.

and Kyle.Gant, do persevere with Ubuntu, it's a steep learning curve compared to Windows cause you can do more customising and repairs yourself -  I've been at it for a year now, and very glad I finally made the change from Windows - most of these little bugs/gliches do get fixed by either updates from the developers, or by some scripting help from other users.

---

### Post by GordonPMartin on 2009-11-02
I'm experiencing almost the exact same problem!

When I shutdown 9.10, I will occasionally get to boot normally afterward, but usually it doesn't.  Instead, I get my grub menu, then the Ubuntu logo for 10 seconds, then a black screen.  Sometimes text will flicker before the black screen, but too quickly to read a word.

The interesting part is the **3 attempt** thing!  If I turn off the computer and retry the boot, on the third attempt I will get into my operating system - always on the third attempt!

I have a clean 9.10 install from this weekend.  It is an HP Pavilion tx2000 (tx2605ca) with ATI video.  The only things I did to it after the default install (before I noticed failed boots):
   - install Wine 
   - configure desktop to span to second monitor (not mirrored)
   - install HP printer driver

Any ideas?

---

### Post by charonred on 2009-11-02
GordonPMartin, yep I get the same symptoms as you; and thinking about it, it does take 3 reboots to get it working - did it again last night after working in Hardy. There's a message occasionally about device not loading in etc/fstab .... (about all I can read cause the message only displays for a second or 2). 

First thing Friday I did a clean install of 9.10 64bit, and immediately installed ATI restricted drivers, and I set desktop to span 2 monitors (not mirror or clone), then dropped in Wine, Virtualbox, a few other apps and rebooted no probs; only after booting to Hardy later and back again did this boot problem appear.

So I'm thinking this problem may be with Grub2; hopefully it'll get sorted quickly as it caused me a bit of concern - had some unexpected PC problems in the last few days and wasn't sure if they were related or not (I suspect just a run of bad luck);
[LIST]
[*]first I installed additional 4GB (1066MHz) of Kingston HyperX memory, identical to existing 4GB, but Memtest showed 2 errors then PC froze completely; swapped into different slots with old and new, mix n match, but ended up returning them for warranty replacement

[*]next had all this 9.10 boot problems

[*]and finally shut PC down Sunday morning, went for ride, and when I got back in afternoon, the PC wouldn't boot - power, lights and fans came on, but no post, no display, no reset ... nothing, had to use power switch to kill. Swapped in another power supply, graphics card, memory (previous 800MHz), and previous dual-core CPU; but same result ... mainboard was dead ??
[/LIST]

I bought the m/board in March '08, and so it's out of 12 month return to base exchange and I was looking at a 3 - 4 week turn around for repair/replacement via Gigabyte; so I was looking at having to buy a new board & DDR3 memory to suit cause PC is necessary for my business :sad: Luckily my PC shop had 1 still in stock (a replaced one) and decided to do a swap for me as it was a discontinued model now, and cause I've built a couple of dozen PCs in the last 2 years for friends, and got all parts from the same shop.

Result is by Monday afternoon I had a functional board and just had to plug everything back in; first using dual core CPU to update BIOS to latest version so it would recognise 945 quad core which I put in next ... all working again :grin:

But back to Karmic, from what I've seen of it over the past few days, it's good, I like it (pat on the back to all Karmic developers); especially Software Centre - that's a real step in the right direction for migrating Windows users... so hope this boot thing gets sorted quickly, cause that'll scare off migrating Windows users quicker than anything.

---

### Post by charonred on 2009-11-04
Well, I went over a friends last night to install a 1TB drive (replaced under warranty), and then install 9.10 64 bit on it.

He has Win7 on a 500GB, and another 1TB with a 9.04 install which is unbootable because a so called IT specialist installed Win7 on that drive as well, instead of the 500GB (I ended up getting it onto the 500) ...

Anyhow, I installed Karmic 64 bit on the new drive, then booted into it once, 2nd time it went to boot options, then after that a dozen attempts plus would not boot, and only displayed the following message, and then hang;
[I]Grub
error 'something' disk
grub rescue>[/I]

What a pain !!!

Nuked it and installed Karmic 32 bit, not a problem, booted correctly each time, even after reconnecting other 2 sata drives.

When Karmic 64 bit showed boot options it displayed *Grub 1.97 (beta)*, ... since when is Grub 1.97(beta) = Grub2 ?

With a new release of Ubuntu you'd at least expect the boot loader to a stable version, not a beta ... maybe this is the reason behind my 64 bit boot problems ?

I left my friends place about midnight with his PC running so it would copy 500 GB+ of files from his unbootable Jaunty install to the new Karmic install; I'll go back another day and show him how to install various apps etc.

I still like Karmic, but not impressed with Grub2 (aka 1.97) .. 

IMHO Ubuntu should stuck with Grub 0.97 till the new one works properly, not a good way to launch Karmic.

---

### Post by charonred on 2009-11-13
Well it's been over a week now since last post to this thread, Grub has undergone an update, but the problem still exists - takes 3 boots to get 64 bit running. 

Karmic looks like it has the goods, but the experience is totally let down by Grub's failure to boot this system successfully- I just can't be bothered; I want to turn the PC on, select the drive I want to boot, go get a cuppa, and come back to a ready n waiting desktop.

More than a little disappointed; I think I'll try the 32 bit version and see how that goes, but it looks like I'll be sticking with 8.04.3 32 bit as my main OS till 10.4 LTS is released ... hopefully that works 'out of the box', and I can finally take full advantage of the 8GB of RAM and my new CPU.

I know that for something that is free, one shouldn't really complain; my move to Ubuntu from Windows hasn't been pain-free, but it has been worth it, and I'm now more inclined to pay for an OS like Ubuntu that I would for another Windows OS - but it has to start!

---

