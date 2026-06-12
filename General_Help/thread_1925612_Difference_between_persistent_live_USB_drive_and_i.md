---
title: "Difference between persistent live USB drive and installing to USB drive"
date: 2012-02-14
forum: General Help
---

### Post by ziritrion on 2012-02-14
Hi everyone,

I wasn't sure whether this was the correct sub forum, but I guess "general help" would be de default one.

I'm a developer and right now my work involves modifying the Android source code. I work 70% of the time at home; I have a desktop PC running Windows and a Macbook Air (13" 2011). I usually just run Ubuntu from VirtualBox whenever I need to use Linux but it has its shortcomings, and compiling Android from MacOSX Lion is very messy, so I need a native Ubuntu to get work done. I have a spare USB HDD that I could run Ubuntu from, so I'd be able to work either at home on my desktop PC and on the road with my MBA.

My first thought was just to boot from the Ubuntu Live CD, plug in the USB HDD and install Ubuntu on it, but then I realized that it may not work on my MBA, which would be critical. I've never used a persistent live USB drive, so I have no idea if it's any different from using a regular Ubuntu install from a USB drive.

I need to be able to use Vim, Eclipse, the Sun JDK and all the other Android related tools. I've googled around but it seems that making a Mac bootable live USB drive is very troublesome. I was planning to use 10.04 TLS since it's Google's recommended distro, but I've seen that the daily 12.04 builds have Mac specific images, which I guess are already prepared to deal with this stuff.

So, what should I do to have a portable Ubuntu that will work both on PC and Macs? Persistent live USB drive or regular install? Any tips?

Thank you all in advance and please excuse me if this has been already asked before; I'm not able to find any related threads.

---

### Post by dcstar on 2012-02-15
> **ziritrion said:**
> 
..........
So, what should I do to have a portable Ubuntu that will work both on PC and Macs? Persistent live USB drive or regular install? Any tips?

Thank you all in advance and please excuse me if this has been already asked before; I'm not able to find any related threads.

A "Live USB" will do extra things like detecting hardware on every boot and also using RAM for temp files so it does not wear out USB  "Stick" drives, a normal install is always intended to run on the hardware it was installed onto.

Ubuntu distros are totally different for different hardware platforms, you cannot have one system that will work on different hardware.

---

### Post by ziritrion on 2012-02-15
Thank you; in that case, I'll go for a live USB drive.

FYI: last night while I was typing the first post I was already installing Ubuntu 10.10 to the USB HDD, then it came to me the live USB issue. I was doing this on my desktop PC. To my surprise, when I plugged in the HDD on the MBA, it booted fine and I was running Ubuntu normally, albeit without wifi. I'm going to try a few things with the set up I already got, and if it works alright then I'll probably leave things as they are, but I'll keep this thread at hand.

If I tried to make a presistent live USB compatible with Mac, though, I think I wouldn't know what to do. I've found this guide to make a Mac compatible live USB:

[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

It involves making 2 partitions. On the other hand, I've found the following tutorial about making a persistent Live USB:

[http://shallowsky.com/blog/linux/install/ubuntu-persistent-live-cd.html](http://shallowsky.com/blog/linux/install/ubuntu-persistent-live-cd.html)

And finally, there's the Ubuntu Documentation page regarding my MBA:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

They all seem quite different, so I'm not quite sure of what I should do: should I try making a mac compatible live USB following the first method? Will the resulting live USB work on a regular PC? Should I add the casper-rw partition as a file (as mentioned in the second tutorial) afterwards?

---

### Post by Cheesehead on 2012-02-15
I roll-my-own live media using [Debian Live]("http://live.debian.net/"), the debian tool for the purpose.

All the hard work has already been done. Just add your custom list of packages, specify a persistent partition, and let it worry about the rest.

---

### Post by holycow131415 on 2012-02-15
Persistence just means LiveCD with the ability to save documents. Cannt create users and ive found installing updates crashes the install.

---

### Post by ziritrion on 2012-02-15
Last night the Ubuntu install on the external HDD was working fine but this morning wasn't working at all. I've spent a few hours trying to reinstall Ubuntu to no avail and also tried to make a casper-rw partition and booting the live CD in persistent mode, without results.

I've finally managed to reinstall Ubuntu again on the HDD; turns out the HDD just won't boot when plugged to an USB 3 port (the HDD is USB 3), even though GRUB is working fine and displaying the OS list. When I plug the HDD to a USB 2 port it works fine, but I'd like to take advantage of the added speed USB3 provides. Are there any workarounds?

---

