---
title: "New laptop, Advice on running Ubuntu and Windows"
date: 2010-08-11
forum: General Help
---

### Post by jagoodjee on 2010-08-11
[COLOR=#1f497d][FONT=&quot][COLOR=Black]I am due to start Uni in a couple of months, Electronic Engineering at the University of Surrey. I have asked the Uni for advice on what operating system to run. 

This was the reply: 
[/COLOR][/FONT][/COLOR][FONT=Arial][SIZE=2][COLOR=#000080][COLOR=#1f497d][FONT=Calibri][COLOR=navy][FONT=Calibri]Linux does have the advantage of improving your programming  skills but your Windows, and MS office, is more compatible overall.  Also,  If you can run VMware on Linux you are able to obtain the Windows  desktop[/FONT][/COLOR][/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[COLOR=#1f497d][FONT=&quot][COLOR=Blue]It is possible for you to run two operating systems at the same time.  You can have Linux as the main system and knowledge of Linux is useful as many of the terminal servers use a linux/unix command structure.  However you can also put on something called emulation software, such as VMware, which gives the appearance of windows.  It has all the functionality of windows and allows the running of MS office etc it is just that you are actually running another program on top of linux.  I believe that VMware is free.[/COLOR]
[COLOR=Black]
Having researched Ubuntu, I am unsure on whether to partition the hardrive to run Windows and Linux or whether to do what is suggested above and install VMware on a Linux system. What do you suggest?

I have found a site with information on installing both OS as I am a novice in computing, 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Does this look like a good guide to you or would you suggest I get it done by someone who knows what they are doing?

In anticipation to your responses I really appreciate your help 
[/COLOR][/FONT][/COLOR]

---

### Post by howefield on 2010-08-11
> **jagoodjee said:**
> Having researched Ubuntu, I am unsure on whether to partition the hardrive to run Windows and Linux or whether to do what is suggested above and install VMware on a Linux system. What do you suggest?

I'd dual boot with Windows and Ubuntu on separate partitions, unless you plan on frequently switching between them, in which case virtualising would be the more useful, (assuming you have the hardware capable of running two operating systems simultaneously). 

Incidentally, nothing to stop you dual booting and virtualising. 

> I have found a site with information on installing both OS as I am a novice in computing,

That particular  
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Does this look like a good guide to you or would you suggest I get it done by someone who knows what they are doing?

The guide looks fine, it is easy enough but only you can know whether or not you are up to it or not. You should get plenty of help here if required.

Virtualbox is an alternative to VMWare, and have some short but good video tutorials on their website.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

If you go with Virtualbox, you have the choice between the OSE and PUEL versions. Differences explained here...

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by TBABill on 2010-08-11
If you will need access to both simultaneously you may be best with one of them in VMWare or Virtualbox. Reviews are available in many places on advantages of both. Your specific needs will determine the best course of whether to run virtual or to dual boot. Both are not difficult and have their advantages, but if you are still unsure you can list your specific needs and ask for further advice to get the best setup so you can focus on school and not your machine.

---

### Post by HermanAB on 2010-08-11
Howdy,

Dual booting is so 20th century... ;)

With VMware Player or Virtualbox, you can run Windows in a window, where it belongs.

---

### Post by brokenromeo on 2010-08-11
Nothing wrong with dual booting...chances are any computer you buy is already going to come with windows and no traditional install disks, so installing a vm image becomes more complicated. Before you do anything, run Ubuntu or your distribution choice from a live cd or bootable usb drive to make sure you are not going to have hardware issues with your particular laptop. If all works, download and learn how to use Clonezilla, so you can then make an image of your hard drive, this makes reinstalling Windows/linux much easier should something get screwed up...

---

### Post by KdotJ on 2010-08-11
I dual boot. It works great for me as a solution. 
Don't get me wrong, I also have windows in a
VM under ubuntu which is great for stuff like using office, iTunes and other bits and pieces. However if you want my honest opinion, performance wise, dual boot is your best bet. However as stated my other users above, if you need to use windows feature at the same time as Linux, switching between the two is not the answer.  In such case a VM is the way. 

Or, just try to learn the open source equivilents such as open office

---

### Post by Zorgoth on 2010-08-11
It depends.  If you only want Windows for compatibility purposes, MS Office, etc. use Virtualbox/VMware.  It is much more convenient than shutting down and restarting.

If you need to use 3D games or Windows-specific high-performance computing (I would expect that that will not be an issue - most scientific programs have linux versions, including commercial products like Matlab), you will need to dual-boot.

In my opinion, dual-booting creates a more unstable system overall, so if you do not need 3D windows games or are willing to try to run them with wine/crossover, I would recommend a virtual machine - as a note, as long as you have a graphics card that supports OpenGL 2.0+ under Linux, my experience with 3D games under wine is very positive; I am a gamer and do not have a Windows installation on my laptop (in sig).

---

### Post by jagoodjee on 2010-08-11
> **Zorgoth said:**
> It depends.  If you only want Windows for compatibility purposes, MS Office, etc. use Virtualbox/VMware.  It is much more convenient than shutting down and restarting.

If you need to use 3D games or Windows-specific high-performance computing (I would expect that that will not be an issue - most scientific programs have linux versions, including commercial products like Matlab), you will need to dual-boot.

In my opinion, dual-booting creates a more unstable system overall, so if you do not need 3D windows games or are willing to try to run them with wine/crossover, I would recommend a virtual machine - as a note, as long as you have a graphics card that supports OpenGL 2.0+ under Linux, my experience with 3D games under wine is very positive; I am a gamer and do not have a Windows installation on my laptop (in sig).


Thanks for the advice. I have a desktop to play games on, the laptop will be primarily for Uni work, so from what you are saying and what my Uni suggested to run Virtualbox/VMware on a Linux system would be best.

---

### Post by jagoodjee on 2010-08-11
> **howefield said:**
> I'd dual boot with Windows and Ubuntu on separate partitions, unless you plan on frequently switching between them, in which case virtualising would be the more useful, (assuming you have the hardware capable of running two operating systems simultaneously). 

Incidentally, nothing to stop you dual booting and virtualising. 



The guide looks fine, it is easy enough but only you can know whether or not you are up to it or not. You should get plenty of help here if required.

Virtualbox is an alternative to VMWare, and have some short but good video tutorials on their website.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

If you go with Virtualbox, you have the choice between the OSE and PUEL versions. Differences explained here...

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)


I think i'll try virtualising and if it does not work out i can always dual partition at a later date. Thanks for the links about virtualbox, very helpful

---

### Post by jagoodjee on 2010-08-11
Thanks for the advice guys (and maybe girls) I will take all your advice into consideration, I think Ubuntu with a Virtualiser is my best bet for now and maybe dual partition at a later date. I'm thinking of getting a laptop from pcspecialist.co.uk which is where my desktop is from. I like the look of the Enigma i7

Processor: Intel i7 2.66GHz
RAM: 4GB
Graphics card: 1GB ATI Radeon
Hard drive: 500GB (partitioned into two 250GB incase of dual OS)
Price: £940
OS: No OS, will boot Ubuntu from Disc

What do you think of that?

Will I need to purchase Windows 7 and MS office to download onto the Virtualiser? And will I still need an antivirus such as Norton?

---

### Post by mendhak on 2010-08-11
> **jagoodjee said:**
> I think i'll try virtualising and if it does not work out i can always dual partition at a later date. Thanks for the links about virtualbox, very helpful
For simple work, yes, you'll be fine with Windows in a VirtualBox, but remember to give it a decent image size to hold the OS on.

Also, remember that you will be able to share your ~/home folder with your Virtual Windows over a UNC path (such as \\virtualbox\), you could map it to a drive letter.  The advantage is that the files will sit in your Ubuntu but also be available within the guest OS, so you don't have synchronization problems.  

**But**, if you plan on using Visual Studio, then ASP.NET won't work on the mapped drive, and you'll need to keep it within the guest OS.

---

### Post by howefield on 2010-08-11
> **jagoodjee said:**
> Will I need to purchase Windows 7 and MS office to download onto the Virtualiser? And will I still need an antivirus such as Norton?

You need all the licensing guff that goes with a "normal" installation of Windows and this also goes for protecting it, you'll need Norton or whatever other protection you would usually have.

Treat it like a normal install. It will behave like one.

---

### Post by Zorgoth on 2010-08-11
Looking at the laptop you are buying, that looks like a very good buy spec/weight wise, and has full HD screen resolution which is imo an extremely important feature for technical work.  One thing is the i7-720QM is cheaper than the processor you selected and is considerably better; it says 1.6 GHz, but that is *4* 1.6 GHz cores instead of 2 2.66 GHz cores, and turboboost means that if only one core is running it can go at 2.8GHz, and I doubt you will be running such a powerful serialized process anyway.

Either get the i7-720QM or the i7-840QM.  Personally I would go for the 840 because I love CPU, but you decide based on your priorities.  Also be sure to choose a 7,200 RPM hard drive; makes a big difference as hard drive I/O is the bottleneck for many processes.

If I had known about that computer I would have gotten it over my Studio 15, and that was at US prices...

Given that you have a desktop for games and processing, yes, definitely go for virtualization.  Regarding MS Windows, I don't know whether you are allowed to use the factory-installed license for a virtual machine, but if I were you I would be safe rather than sorry, avoid bloatware, and considering that the company charges £79 for Windows, not pay a very different amount of money, and get yourself your own copy of Windows 7.

(and then you'd also be supporting companies that don't force an OS upon you :) )

---

### Post by DeanMc on 2010-08-11
My original plan was to simply duel boot as I am completely new to Linux and worried about what programs run and what don't. To my surprise for most of my applications there is a good selection of free alternatives. Once you get over the fact that they are more functional than pretty you realise that most if not all of your work can be done with Linux alone. 

I do have one caveat that made me need at least a virtual pc to run Windows on and that is that I purchase all of my music via iTunes and like it for that purpose. So to date the only software my windows VM contains is iTunes until Apple release a Linux based version.

---

### Post by jagoodjee on 2010-08-12
Once again, I am very grateful for the heads up everyone

---

### Post by jagoodjee on 2010-08-12
> **Zorgoth said:**
> Looking at the laptop you are buying, that looks like a very good buy spec/weight wise, and has full HD screen resolution which is imo an extremely important feature for technical work.  One thing is the i7-720QM is cheaper than the processor you selected and is considerably better; it says 1.6 GHz, but that is *4* 1.6 GHz cores instead of 2 2.66 GHz cores, and turboboost means that if only one core is running it can go at 2.8GHz, and I doubt you will be running such a powerful serialized process anyway.

Either get the i7-720QM or the i7-840QM.  Personally I would go for the 840 because I love CPU, but you decide based on your priorities.  Also be sure to choose a 7,200 RPM hard drive; makes a big difference as hard drive I/O is the bottleneck for many processes.

If I had known about that computer I would have gotten it over my Studio 15, and that was at US prices...

Given that you have a desktop for games and processing, yes, definitely go for virtualization.  Regarding MS Windows, I don't know whether you are allowed to use the factory-installed license for a virtual machine, but if I were you I would be safe rather than sorry, avoid bloatware, and considering that the company charges £79 for Windows, not pay a very different amount of money, and get yourself your own copy of Windows 7.

(and then you'd also be supporting companies that don't force an OS upon you :) )

Some good advice there, do you reccommend one 4GB RAM or 2 x 2GB?

---

### Post by Zorgoth on 2010-08-12
For 15 pounds or whatever they're charging,m get 4x1 and then you can upgrade your memory later, unless you are sure 4 GB is all you will ever want.

If you have a desktop with, say, a 3.2 GHz dual core i5 (or equivalent c2d, that will have a higher required clock rate, google it to figure it out, I'm in a hurry) or better, and if that desktop's motherboard is upgradeable to 8GB, you won't need a laptop with more than 4 for any heavy processing you need to do.

If your university says you will need to do heavy numerical processing, 
I would plan on 8 GB eventually on some machine, but my guess is you won't strictly need it as a student.  I think it should noticably increase performance when doing certain intensive activities or multitasking.  Running Windows in a VM is another thing that will use a lot of memory, so that will bring you close to wanting an upgrade.

---

