---
title: "Ubuntu 10.10 not installing"
date: 2011-02-14
forum: General Help
---

### Post by blown262 on 2011-02-14
Hello all!
This is my very first attempt at messing with any linux platforms and from the get-go, I seem to be having issues. First off, since I know these are very important, system specs:
 
eVGA x58 SLI3 USB3 SATA 3.0 socket 1366 motherboard
Intel Core i7 950 processor
Patriot Sector 5 DDR3 PC3 12800 dual channel RAM
(2x)eVGA GTX460 cards
Intel 40GB solid state
WD Caviar Black 500 GB SATA
LG DVD R/W drive
Processor is underclocked to 2.83GHz
RAM is underclocked to 1333MHz and all timings are stock
 
So first off, I rented the Ubuntu bible from the library as it seemed to be the best thing to read up before I started, and this came with an Ubuntu LiveCD. I read through the first few chapters to see how to go about installing with the LiveCD it came with. I want to run a dual boo with Windows 7 Ultimate. So I defrag my secondary drive (WD) like the book says and reboot with the CD in the tray. When the BIOS loads, I switch everything around to load from CD first. Finish that and I get MS_DOS-looking screen with mono-spaced typing that goes really quick and I can't see what it says. Then I get the Ubuntu logo and hear the CD drive spin up and figure everything is working fine. The screen flashes a few times but everything seems to be trucking forward. Then after about 30-40 seconds, the DOS-looking screen pops up again and it says something with a $ sign and a few random letters and ubuntu all in one word with a flashing typing ticker next to it. I can type whatever I want, tried typing boot, says I need parameters; tried typing help: gives me a whole list of weird commands I've never seen before; try typing just random things to get it to do anything and I get nothing. If I type exit, it just erases everything and gives me the flashing ticker again. After a few minutes of this, my screen went all haywire and went black (but did not shut off) and everything became completely unresponsive. I hard restart the system and the same exact thing happens. I choose to load HDD first and everything runs as normal. I downloaded Ubuntu 10.10 and burned the .iso to DVD and I get a different load screen (this time it looks like a HDD icon and either a star or a guy standing there (cant really tell with the horrible 8 bit looking graphics lol) and then the exact same MS_DOS-looking terminal screen that becomes unresponsive after a few minutes. So Next was to install inside Windows. I run the 10.10 .iso DVD and it seems to install ok. I restart and there is a boot selection for Windows and for Ubuntu (YAY!!!) I highlight ubuntu and hit enter and, low and behold, it is EXACTLY the same as previously mentioned. I have tried every combination of booting this OS including safe graphics mode, normal mode, really annoyed Windows-user mode, etc....Please help! I'd really like to start learning to program and all the top-notch programmers I've spoken to say start with learning Linux. So that's what I want to do, but I must be doing something wrong somewhere along the lines. Any help at all will be greatly appreciated.
Thanks
Chris

---

### Post by YesWeCan on 2011-02-14
Nice system...:)

Dont worry, getting Ubuntu to install is often a pain. Usually due to graphics card non support by the kernel.

I don't know what this book is but you should visit the Ubuntu hme page and download the latest from there and burn to CD or USB.

A lot of graphics teething troubles are remedied by booting with the 'nomodeset' kernel option.

The Ubuntu 'alternate install' iso may have better success rather than the 'live' iso.

---

### Post by blown262 on 2011-02-14
Thanks for the reply. I downloaded 10.10 from the homepage but I can't recall if it was the liveCD or the alternate. I shall download the alternate and burn that just in case and keep you updated.

---

### Post by Mark Phelps on 2011-02-15
If I understand what you said, you have two physical drives, the second of which is a WD.  If that is true, you would do best as follows:
1) Have ONLY the WD drive connected to your PC; do NOT have the Win7 drive connected.
2) Have the WD drive free of partitions.  Ubuntu won't install to MS Windows partitions, so if there are any present, that will prevent the installation.
3) Boot from the Ubuntu CD and install to the WD drive. 

When done, boot from the machine -- STILL with only the WD drive connected.

Don't reconnect the Win7 drive until AFTER you have Ubuntu up and running.  Why? Because with two drives connected, it's real easy to make a mistake and corrupt or overwrite the Win7 stuff.

---

### Post by YesWeCan on 2011-02-15
Agree with Mark.

Once you have Ubuntu booting on its own, you can reconnect the Windows disk and then reboot into Ubuntu and run 'sudo update-grub' to give you a boot menu with choice of Ubuntu or Windows.

---

### Post by blown262 on 2011-02-15
Thanks for the replies. Update as of now, I downloaded and burned Ubuntu 10.04 alternate and it seemed to install fine for about a half hour or so. But once it got to installing software, specifically nVidia components, it would say installation failed, and send me to a list where I could choose any number of options. I tried installing software again and the same message appeared. I skipped the software and went to install GRUB instead as it was next on the list. It gave me a choice between GRUB 2 or GRUB legacy. I tried both and both failed and it gave me a message saying that the OS would not boot without GRUB installed. This is turning into a major headache. I wish I would have started with this sort of thing sooner in life haha. I am very affluent in Windows and have minimal problems with software and whatnot as I understand the windows platform, but Linux is kicking my *** so far. Are there any noob linux courses to take because all the books I have just assume that Ubuntu installed just fine and don't give me any installation troubleshooting guides.

Thanks for the replies
Chris

P.S. I did take the W7 drive and left just the WD in and that's when I got the failed install on the nVidia drivers and GRUB

---

### Post by YesWeCan on 2011-02-16
> **blown262 said:**
> I wish I would have started with this sort of thing sooner in life haha.
You mean you may not live long enough to get Ubuntu installed? :p
That may be true. Installing Ubuntu seems to be either easy or very difficult, and as you will find, linux software is optimised for when things work. When things fail you usually get unhelpful "information" that requires an hour of Googling to translate into something actionable. It is not easy like Windows.

Well, you want Grub2.
But your issues seem to be related to your graphics card. If you browse through the installation section of this forum two things come up more than anything else: graphics problems and dual boot problems. The Ubuntu installer has improved over the years but it still needs to improve a lot more. Not a great first impression for new users.

One thing I would try is to boot off the live CD. I have not used the 10.10 live CD. You should get a list of languages to choose and then a menu offering things like "install" and "try without installing" and "check memory". If all you see is the curious icons at the bottom of a pink screen then try pressing the space bar. I have a feeling if you don't press a key it will automatically start trying to boot (which is really dumb!). In the menu section, after you choose a language, you should be able to press a function key for options. Select the "nomodeset" option and then "try without installing".

If that doesn't boot then I am out of ideas. You may need to search for something like "GTX460 Ubuntu installation".

---

### Post by blown262 on 2011-02-16
Thanks all for all the tips. I took a little of everything that was said and was finally able to get Ubuntu 10.10 64 bit installed and I am currently running it right now! It was the space bar and nomodeset along with manually running grub 2 that it finally loaded. Thanks again to all the input and I will DEFINITELY be posting more on this site. 

Thanks again
Chris (blown262)

---

