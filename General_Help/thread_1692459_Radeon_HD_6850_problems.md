---
title: "Radeon HD 6850 problems"
date: 2011-02-21
forum: General Help
---

### Post by Rawe on 2011-02-21
Howdy all! New to the forums. New to Linux, actually. I just got myself a completely new rig a week ago and decided I'd go with Ubuntu, tired of Windows. Never used Linux before.

Now I've been battling with this issue for days. I've got the ATI Radeon HD6850 graphics card, and, obviously it has some serious compatibility issues with Ubuntu 10.10.

This is like, the 5th time I'm doing a reinstall. Everytime I activate the closed / additional fglrx driver that's offered, it completely renders my computer unbootable and unusable (hence the reinstalls). It works fine out of the box with the standard drivers but the lousy 1280x1024 resolution and default desktop view just don't cut it.

I see some have it working with the use of this PPA [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")  but I don't understand how to use software of it? Am I supposed to get the driver from that PPA? I took it to use and then activated the closed driver with the same results as any other time I tried to do anything regarding 3D-drivers; unusable Ubuntu.

I really would dislike to go back to use of Windows XP or any other Windows OS for that matter. This just seems too hard to get the graphics card working on Ubuntu 10.10 and is forcing to me quit trying (that thought already crossed my mind a couple of times). I KNOW people have gotten the 3D-drivers to work on Meerkat with HD6850 or 6870, I just don't understand HOW and why it will NOT work for me?

PLEASE help me figure out what to do with this? I'm a completely n00bie when it comes to Linux, so please keep the steps simple if anyone feels comfortable to answer to this thread :)

Thanks in advance.

---

### Post by Rawe on 2011-02-21
Whoaaaaaah!! Nevermind.

I was able to get it working with this! [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

I'm so psyched. Way cooool. Hope this helps for others. Consider this resolved! :)

---

### Post by seawolf167 on 2011-02-21
I have the 6870s in Crossfire mode and haven't run into any problems with them. Be sure to get the graphics drive suite from ATI's website for any future updates (the PPA does that automatically, under the hood essentially all its doing is installing the below driver suite after any prereq packages)

The download link:

[http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run)

or, [here is your card,]("http://www.amd.com/US/PRODUCTS/DESKTOP/GRAPHICS/AMD-RADEON-HD-6000/HD-6850/Pages/amd-radeon-hd-6850-overview.aspx") click find a drive in the upper-right, then follow through the prompts

---

### Post by Insuite on 2011-02-23
Hiya all...

I just found this thread and read and did what the attached article said and Woo Hoo!!!  my new 6850 is working just fine now in Unbutu!!!

Thanks all who posted and a very big thanks you to the article writers at...
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

Cheers,
Insuite

---

