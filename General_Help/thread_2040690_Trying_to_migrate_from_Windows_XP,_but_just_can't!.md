---
title: "Trying to migrate from Windows XP, but just can't!"
date: 2012-08-11
forum: General Help
---

### Post by oslub on 2012-08-11
Each time I have less reasons to stick with Windows XP on my Pentium IV desktop, it is old, gets slow in about three weeks of usage, even running several cleaning and defrag applications frequently and given the limitations of this machine, software is not that much of a problem, apart from MSOffice, I really only use it to everyday stuff, browse the web, edit documents, edit images. Even Microsoft doesn't want us to use it anymore, as demonstrated with Skydrive Desktop. So there aren't any reasons to stick to it when there are some really lightweight distribuitions that can give this machine a new life.

That is in theory, at least. Because in pratice, I just can't find the right distro/desktop environment for this computer. I've tried many, and so far the ones that have a tolerable performance are Lubuntu and Linux Mint MATE 32-bit. XFCE didn't perform well. 

The thing is both Lubuntu 12.04 and Linux Mint MATE as an Operative System, are much, much superior to Windows XP, boot fast, load programs fast, navigating and opening files and folders is fast and responsive, less CPU and memory usage, but when it comes to videos and web browsing, it is a real pain.

To start, Firefox is always crashing, much more frequently than on Windows, even with no addons. Chromium also crashes a lot and displays the "aw snap" sign. Then, I can only have a very limited amount of tabs opened, about 5, even with all the CPU-saving addons enabled - Adblock Plus, Flashblock, NoScript, Ghostery. This really is a major drawback, because I can still browse with a lot of tabs opened on Windows XP with Firefox, several panorama groups, eventually it also crashes but only when the number of tabs is over 30 or 40.

Also, everything video-related is very poor on both distribuitions, I am very limited on GPU resources but streaming the video on a player such as SMPlayer or VLC allows me to watch videos without any lag on Windows XP, while on the referred distros, there is always lag, no matter what quality the video is displayed (I don't even try flash anymore, only play it on VLC or SMPlayer).

Also LibreOffice is much slower than MSOffice when opening and saving files and takes too much CPU when information included on those files increase. But apart of some waiting periods and some rare crashes, I manage to live with that.

These problems are preventing me from having a complete daily experience and forcing me to split my work between Windows and Linux constantly, because the Nautilus file manager is so much productive and fast than Windows XP Explorer and the system itself is much faster, responsive and resource-saver, but then if I want to browse the Internet comfortably, edit documents without waiting so long for saving or opening them, I need to make use of XP and its faulty, counter-productive and crashy Explorer... and consequently, I need to constantly clean and defrag it, update individually each application when new updates are available, which are some of the very annoying reasons why I want to abandon Windows XP completely.

Do you have any tips to help me improve the performance of web browsing and multimedia playing on Lubuntu or even Mint?

---

### Post by dino99 on 2012-08-11
Lubuntu does not use FF as default because it needs too much cpu/ram. That said dont try to use apps needing huge resources, except if your video card has a lot of ram; or install a ssd (there is ssd's pcie card)

---

### Post by asmoore82 on 2012-08-11
I would test that machine for bad RAM.

Firefox crashing on my Linux machines is exceedingly rare. It is possible for one OS to live happily on bad RAM for years and another to fail early and often, due to different RAM allocation strategies.

Use memtest86+ from any Linux Live CD (Ubuntu, Fedora, SystemRescueCD, Clonezilla, etc.). If there is a problem there, it will find it *fast*!

---

### Post by cwsnyder on 2012-08-11
I would like to comment that the 'cpu-saving' add-ons you list may save the cpu, but consume memory which could be used for other tabs.

Second comment: Windows XP can function with 128M RAM, Lubuntu also can function with 128M RAM, but Flash and video want more, and Linux Mint MATE officially requires 512M RAM.  You also **need** at least double your RAM space in a swap partition on your hard drive if you have less than 2G RAM in your system.

If your RAM that you have is good, you may simply need at least 512M RAM to function properly.

As for LibreOffice, if you have less than 1G RAM, stay with Abiword/Gnumeric and away from LibreOffice unless you are required to do more than work with a word processor and spreadsheet.

---

### Post by RedRat on 2012-08-11
I would suggest that you increase your RAM to perhaps 4Gb if you are running 32-bit Linux and maybe 6-8GB if you run 64-bit Linux. However, this can be throwing good money after bad if your cpu is not up to snuff. You do not say how old your computer might be. Keep in mind that multimedia does require memory resources and cpu cycles.

---

### Post by oslub on 2012-08-11
> **asmoore82 said:**
> I would test that machine for bad RAM.

Firefox crashing on my Linux machines is exceedingly rare. It is possible for one OS to live happily on bad RAM for years and another to fail early and often, due to different RAM allocation strategies.

Use memtest86+ from any Linux Live CD (Ubuntu, Fedora, SystemRescueCD, Clonezilla, etc.). If there is a problem there, it will find it *fast*!

I will run memtest as soon as possible, I believe this may be a plausible explanation for the random and frequent crashes I usually have, although until now I didnt know why they happen more often on Linux.

---

### Post by oslub on 2012-08-11
> **cwsnyder said:**
> I would like to comment that the 'cpu-saving' add-ons you list may save the cpu, but consume memory which could be used for other tabs.

Second comment: Windows XP can function with 128M RAM, Lubuntu also can function with 128M RAM, but Flash and video want more, and Linux Mint MATE officially requires 512M RAM.  You also **need** at least double your RAM space in a swap partition on your hard drive if you have less than 2G RAM in your system.

If your RAM that you have is good, you may simply need at least 512M RAM to function properly.

As for LibreOffice, if you have less than 1G RAM, stay with Abiword/Gnumeric and away from LibreOffice unless you are required to do more than work with a word processor and spreadsheet.

Yes you're right about the addons, I try to block all flash banners and scripts but the addons themselves slow Firefox down and eventually contribute for it to crash, for example when using Ghostery the difference is noticeable. 

About the swap partition, I have it on both Lubuntu and Mint and as I said, the system itself runs fast and responsive but not anything related to multimedia or internet browsing. It gives me the impression that web technologies, such as flash, are more compatible with Windows than with Linux. But I may have bad RAM as asmoore82 pointed out, I'll check that...

---

### Post by oslub on 2012-08-11
> **RedRat said:**
> I would suggest that you increase your RAM to perhaps 4Gb if you are running 32-bit Linux and maybe 6-8GB if you run 64-bit Linux. However, this can be throwing good money after bad if your cpu is not up to snuff. You do not say how old your computer might be. Keep in mind that multimedia does require memory resources and cpu cycles.

Yes I think it is a waste to upgrade this Desktop, if I recall correctly it is 6 years old, GPU is only 96MB, processor is single-core, it would require a complete upgrade. I still didn't just buy another because my professional tasks require a portable device and I am saving what I can to buy an ultrabook with much more satisfatory autonomy and lighter than my almost 3kg laptop. 

Yes I am aware that multimedia requires a lot from PC resources, I can skip watching videos whenever possible, I really just want to be able to have a browser running fine with some tabs opened and without crashing constantly. However the main point of my thread is that despite multimedia demands high resources and my PC is old, I can have a comfortable browsing session and watch videos without lag on Windows XP and not on those distributions, so I am wondering if there are any configurations or adaptations which could be made to have the same results in Lubuntu.

---

### Post by sienile on 2012-08-11
I agree with the other posters that bad RAM may be the problem. Also, I've always heard it's best practice to have a 2GB swap partition.

But aside from that, I wonder why you are choosing to run the more limited Ubuntu variants instead of just plain Ubuntu. Personally I've had issues with Lubuntu having intermittent crashes. It just didn't appear to like any of the programs I preferred. Regular Ubuntu doesn't crash at all.

How much RAM do you have? If it's more than the 512MB minimum requirements, I'd give it a shot.

---

### Post by lykwydchykyn on 2012-08-11
In my opinion, many of the problems you describe are symptomatic of poor video hardware with bad Linux support.  Chromium and (I think) Firefox try to use GPU acceleration for HTML5 video and animation, Flash uses GPU acceleration by default.  This can cause crashes and sluggishness if your video hardware is badly supported.

So this leaves the questions:

 - What is your video hardware?
 - Have you tried disabling GPU acceleration in flash and your browsers?

---

### Post by Greggyboy on 2012-08-12
> **oslub said:**
> streaming the video on a player such as SMPlayer or VLC allows me to watch videos without any lag on Windows XP, while on the referred distros, there is always lag, no matter what quality the video is displayed

Just through the browsers? Do video's play fine off the hdd?

Btw, XP has been around for a VERY LONG TIME and its faster than any modern regular linux distro regardless of the fud you read. But XP crashes more, its not very secure and MS can backdoor you anytime they like plus you have to agree to their terms just to use it (grrr...) but it is a very fast OS so you have to expect a small loss in speed when you switch.

I'm currently using Xubuntu 12.04 on both my lappy's (Compaq C700, Dell XPS 17) and it runs well enough to have replaced XP on my C700. Not quite as fast but more secure and no MS nonsence!!!

---

### Post by coldraven on 2012-08-12
My neighbours PC works fine with Ubuntu 8.04 but later versions just crash. I think it is because the Intel video chipset.
Some hardware just does not play nicely under Linux. I would hang around the local re-cycling yard for a free PC, it's amazing what people throw out.

---

### Post by oslub on 2012-08-14
> **sienile said:**
> I agree with the other posters that bad RAM may be the problem. Also, I've always heard it's best practice to have a 2GB swap partition.

But aside from that, I wonder why you are choosing to run the more limited Ubuntu variants instead of just plain Ubuntu. Personally I've had issues with Lubuntu having intermittent crashes. It just didn't appear to like any of the programs I preferred. Regular Ubuntu doesn't crash at all.

How much RAM do you have? If it's more than the 512MB minimum requirements, I'd give it a shot.

I have 1GB of RAM, I've tried default Ubuntu 12.04, which I would love to use, but even with Unity 2D, it gets too slow, so I had to look for other suitable variants...

---

### Post by oslub on 2012-08-14
Well I ran memtest86 test to check for RAM errors and indeed they have been found. So this may be in fact the main cause for a not so smooth experience with various Linux distros. I probably won't upgrade this PC any further, because it has other issues such as poor ventilation and media drives malfunctioning, plus an outdated single-core processor, so instead I'll deal with it until the end of the year, saving money to buy a new laptop, and when I do I'll replace this old desktop with my current laptop.

---

