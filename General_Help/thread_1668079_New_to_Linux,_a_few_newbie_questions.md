---
title: "New to Linux, a few newbie questions"
date: 2011-01-15
forum: General Help
---

### Post by TAChimpo on 2011-01-15
Hey guys! 

After years of neglecting to get into Linux (for no real reason other than being lazy and decently content with Windows), I've not been shoved head first into the Linux world due to a Linux class I am taking. I've only been in the class for two weeks, so sorry about my lack of Linux knowledge! 

Anyway, I've downloaded and installed Ubuntu (using wubi, off of Windows 7 on a Sony Vaio VPCF1) and I'm having a few problems. 

The main problem is that I can't connect wirelessly to the internet. Using ethernet works great, but I need to be able to take my laptop to class so I need to figure out how to get this working. The only thing I've tried was to check System> Admin> Hardware (or something along those lines?) to see that it said I have no peripherals connected. I don't even know if that is the right place to start, again... sorry :p

The next problem is that the mouse-pad does not work. This is not a huge problem as I have a wireless USB one that works great, but still something I'd love to learn how to fix, if only for the knowledge of how to.

After that... is it possible to change resolution in Linux? I assume yes, how? 

And final question! Is this all something to do with wubi? Would it be better to do a dual boot with Windows 7, or would that even make much of a difference? 

Thanks in advance guys. So far I'm loving Linux and kicking myself for not getting into it sooner.

---

### Post by Smart Viking on 2011-01-15
You can change resolution in gnome-display-properties.

Your problem doesn't have anything with it being run in wubi.

---

### Post by ram2500 on 2011-01-15
Hello,

Welcome to the world of Linux! Unfortunately, your laptop seems to have an unsupported wireless module. I'm assuming that you meant the Hardware Drivers utility, and if it doesn't offer a driver for your device, then unless you want to make things really complicated, you are out of luck. 

I would invest in a $15 wireless USB dongle (it plugs into your USB port) to work around this temporarily. Perhaps you'll learn later on in your class how to deal with hardware support issues and Linux, such as writing drivers (sounds like fun:D). 

To change your resolution, go to System, Preferences, and Monitor. You can change your resolution there. Usually, Ubuntu chooses the optimum resolution, so if you have a less-than-optimum resolution, you may have a problem. 

I would try VirtualBox to try out Linux if you cannot get these issues fixed. You run Ubuntu inside a window in Windows (or another OS), and you'll need no drivers for your wireless or touchpad.

---

### Post by TAChimpo on 2011-01-15
I had a feeling that changing the resolution would be that simple. I'm away from that computer atm, but will have to check that once I get back. The resolution was terrible, hopefully there isn't a problem.

I kind of had a feeling that I had an unsupported wireless module, but I guess I was hoping otherwise :P I'll have to look into getting a dongle (or finding one that I know I have somewhere and seeing if it works). I did mean that nothing showed up in Hardware Drivers utility (literally a blank window), I just didn't have access and was going off of this morning's memory. 

How complicated are you talking? I'm willing to give it a shot if someone can help! I live for these things, and would love to learn how to do that. Plus if it is covered in class I'll have a head start :P

---

### Post by bcbc on 2011-01-15
This might help: [http://ubuntuforums.org/showpost.php?p=10290430&postcount=7](http://ubuntuforums.org/showpost.php?p=10290430&postcount=7)

---

### Post by TAChimpo on 2011-01-19
Thanks everyone for the help. The link to the post solved all of the problem (I think!). 

I reinstalled with a dual boot rather than using wubi and that fixed the wifi problem. Everything else was fixed after following those steps. 

Glad to be able to have a fully working version of Ubuntu!!

---

