---
title: "Wubi help"
date: 2010-06-18
forum: General Help
---

### Post by adeee on 2010-06-18
I have installed ubuntu and windows using wubi. Now i want to install kubuntu without removing those OSs. Will it show all 3 OS while booting? What may be the effect of this new installation on my old installations?

If I install Fedora with wubi, what will be the side effect of this. Will they happily go side by side or will it remove other installations.

Can i install all these 4 OSs at one time, or do it allow just 2 installations at a time.

I want these 4 OSs for testing purposes.

Thanks

---

### Post by bcbc on 2010-06-18
See [https://wiki.ubuntu.com/WubiGuide#How do I install multiple distros?]("https://wiki.ubuntu.com/WubiGuide#How do I install multiple distros?")

With the above link, it's more that you're installing multiple desktop packages within a single install. You can't do another separate wubi install from windows unless you uninstall the existing one first.

I'm not aware of a wubi version that supports fedora, but I'd check fedora's support forums for more info. 

I'd recommend repartitioning your drive - then you can install as many versions/distros you want without worrying about doing it with wubi. Use an external drive if your internal drive isn't big enough.

Wubi is more for new ubuntu users who either don't know how or are nervous about partitioning their drive. In your case, running multiple versions of linux for testing purposes, it sounds like wubi isn't the right tool for you.

---

### Post by WorMzy on 2010-06-18
I think you're misunderstanding what Wubi is. It isn't dual booting, although it's very similar. You are booting into Windows, then switching into self-enclosed Ubuntu installation, hence the name "W[COLOR="Red"]ub[/COLOR]i", or Ubuntu inside Windows.

I believe that it's theoretically possible to have multiple Wubi installations on a single Windows installation, but I don't know how you'd go about achieving this.

As far as I know, it isn't possible to install Fedora in the same manner as Wubi; you will need to actually partition your disk(s) and install it as a separate operating system; this will install Grub (or possibly Lilo) to the MBR, which will give you the option to boot to Fedora or Windows; you will have to choose the Windows option to get the choice of booting to Windows or Ubuntu.

You can have as many operating systems as your disks can hold, if you set up the partitioning correctly. I currently have five: Ubuntu 10.04 and 9.10, Arch, Windows 7 and Windows XP.

---

### Post by bcbc on 2010-06-18
> **WorMzy said:**
> I think you're misunderstanding what Wubi is. It isn't dual booting, although it's very similar. You are booting into Windows, then switching into self-enclosed Ubuntu installation, hence the name "W[COLOR="Red"]ub[/COLOR]i", or Ubuntu inside Windows.


Windows-based UBuntu Installer.

---

### Post by WorMzy on 2010-06-18
Or that works too, I guess. I prefer my misinterpretation, it makes it more clear what it is. :)

---

### Post by bcbc on 2010-06-18
> **WorMzy said:**
> Or that works too, I guess. I prefer my misinterpretation, it makes it more clear what it is. :)

No, your misinterpretation fits your misinterpretation of what wubi is. e.g. the wubi-installed ubuntu doesn't need to 'boot windows' to run. Just because you make something up and it 'sounds good' doesn't make it right.

However, none of this is really relevant to the OP, if you'd like to create a new thread "what I think wubi is", I'll add my thoughts there ?

---

### Post by steveneddy on 2010-06-18
Why don't you simply partition your drive and get a real installation of Ubuntu and Fedora and stop futzing around with that buggy, annoying Wubi?

Wubi was designed for a trial only. It is recommended that you actually INSTALL Ubuntu for it to operate correctly.

From [this link]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu") in my sig:

> Wubi (Windows-based Ubuntu Installer), an officially supported dual-boot installer that allows Ubuntu to be run mounted in a virtual-disk within the Windows environment (which can cause a slight degradation in performance). Because the installation requires an intact functioning Windows system,** it is recommended to install Ubuntu in this manner for short-term evaluation purposes only**. **[COLOR="Red"]A permanent Ubuntu installation should be installed in its own partition, with its own filesystem, and should not rely on Windows[/COLOR]**.

---

### Post by bcbc on 2010-06-19
> **steveneddy said:**
> Why don't you simply partition your drive and get a real installation of Ubuntu and Fedora and stop futzing around with that buggy, annoying Wubi?

Wubi was designed for a trial only. It is recommended that you actually INSTALL Ubuntu for it to operate correctly.

From [this link]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu") in my sig:

I'm sorry you find wubi annoying. Wubi is great for what it is intended: to let windows users get to know ubuntu without having to partition their hard drive. And it does 'operate correctly' unless you consider hibernation to be a part of that.

In fact, the problem - it seems - is that it runs too well, as many users don't seem to feel the need to advance to a normal install. One user recently has a 35GB wubi install and wanted to increase it to 70GB. Obviously, wubi is not the right tool in this case.

Maybe there should be a popup that says "30 day trial coming to an end, press OK to install direct to partition". You could do this as a summer project.

In any case, you've shared your view - I've shared mine - the world's so much better for it.

Summary:
Three responses to OP. All recommend not using wubi. All have different opinions about wubi. World better place.

---

### Post by steveneddy on 2010-06-20
> **bcbc said:**
> I'm sorry you find wubi annoying. Wubi is great for what it is intended: to let windows users get to know ubuntu without having to partition their hard drive. And it does 'operate correctly' unless you consider hibernation to be a part of that.

In fact, the problem - it seems - is that it runs too well, as many users don't seem to feel the need to advance to a normal install. One user recently has a 35GB wubi install and wanted to increase it to 70GB. Obviously, wubi is not the right tool in this case.

Maybe there should be a popup that says "30 day trial coming to an end, press OK to install direct to partition". You could do this as a summer project.

In any case, you've shared your view - I've shared mine - the world's so much better for it.

Summary:
Three responses to OP. All recommend not using wubi. All have different opinions about wubi. World better place.

Thank you for evaluating my post. 

I was merely passing on the information from the link in my sig that was not created by me, but has been part of the Ubuntu Guide since the creation of Wubi.

I simply stated my opinion that I believe Wubi was annoying and buggy because I believe that it is. It relies on Windows to operate properly, and that in itself is the basis for my opinion.

Don't get the opinion that I am flaming Windows either. I use Windows in a VM **ONLY WHEN NECESSARY**. Windows has it's place, but again I must state that the primary focus of my post is that Wubi's **only** purpose is to give a Windows user a way to evaluate Ubuntu without having to educate him or herself in the simple process of partitioning the hard drive before having the ability to actually try out Ubuntu.

It is hoped that in the mean time that the Windows user, who has found that Ubuntu would be a good OS to install on the HD, would then use the tools available to themselves and partition the drive and install Ubuntu as intended.

I just find it humorous that you seemed to focus on **one word** in my post while all along seemingly missing the point I was trying to make all along, which I actually repeated and reinforced in this post.

I believe this thread may be considered hijacked if this conversation goes any farther - lol

---

### Post by bcbc on 2010-06-21
> **steveneddy said:**
> It relies on Windows to operate properly, and that in itself is the basis for my opinion.

Don't get the opinion that I am flaming Windows either.

I get the opinion that you are contradicting yourself. 

Why do you feel the need to sprout such nonsense? You are of course entitled to your opinion, but we are not obligated to have it forced down our throats. Maybe you should post this in the Community cafe or Recurring discussions and I will be happy to not participate.

---

### Post by steveneddy on 2010-06-21
> **bcbc said:**
> I get the opinion that you are contradicting yourself. 

Why do you feel the need to sprout such nonsense? You are of course entitled to your opinion, but we are not obligated to have it forced down our throats. Maybe you should post this in the Community cafe or Recurring discussions and I will be happy to not participate.

It appears as if all reason has been tossed out the window here - no pun intended.

It would be nice if every little person here wouldn't feel the need to think that if anyone posts anything remotely derogatory about the Windows operating system, then the post or thread is not even worth participating in, but always the person offended really didn't offer anything particularly interesting or helpful to the OP or to the thread in general.

Unfortunately the point that continually seems to be diverted from is the fact that Wubi is **not** stable enough for daily use and once the user determines that they can use Ubuntu and would like to learn more, **they should learn to partition the hard drive and install Ubuntu the proper way**. Using Windows separately and Ubuntu on it's own partition will make both operating systems more stable than if Wubi were used.

Referenced link here:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

Some people just don't seem to understand even when you spell it out for them in very simple to understand statements. They continually see only their particular agenda and refuse to see anything but their own point of view, refusing to accept facts no matter how simply they may be presented.

---

### Post by bcbc on 2010-06-21
> **steveneddy said:**
> It appears as if all reason has been tossed out the window here - no pun intended.

Some people just don't seem to understand even when you spell it out for them in very simple to understand statements. They continually see only their particular agenda and refuse to see anything but their own point of view, refusing to accept facts no matter how simply they may be presented.

And I thought we were never going to find some common ground... :)

Anyway... seriously this has gone on a bit too far. I'm always careful to recommend to wubi users to consider installing properly, I just get irritated when people like yourself slander what I consider to be a great product to showcase Ubuntu and don't have any rational basis for this. And that much has been shown.

Anything which can get Ubuntu onto the desktops of Windows users this easily should be supported, not shunned.

That is my last word on the matter. Apologies to the OP (if still around).

---

### Post by wilee-nilee on 2010-06-22
> **bcbc said:**
> And I thought we were never going to find some common ground... :)

Anyway... seriously this has gone on a bit too far. I'm always careful to recommend to wubi users to consider installing properly, I just get irritated when people like yourself slander what I consider to be a great product to showcase Ubuntu and don't have any rational basis for this. And that much has been shown.

Anything which can get Ubuntu onto the desktops of Windows users this easily should be supported, not shunned.


That is my last word on the matter. Apologies to the OP (if still around).


You as a person who knows how to fix the inherent problems with booting alone should know better.

trying to explain a straight fix to a user who doesn't even know how to boot a cd, or do a cli command gets very difficult when this inexperience gets mixed with a borked install of Linux inside of MS.

The fixes for a dual boot problem with grub being put into the the MS partition are fairly easy to fix, but even then if testdisk is used or even lilo it becomes a challenge, for people. Now when you compound this with Ubuntu being inside of Widows, and possibly having stuff to recover it is even more difficult.

If we can put on the noob shoes and remember are own struggles rather then the fix abilities we have now it is easier to understand the argument against wubi.

The argument that anything that can get them the desktop is confounded with things like these threads.
[http://ubuntuforums.org/showthread.php?t=1514291](http://ubuntuforums.org/showthread.php?t=1514291)

And a quote from this thread.
[http://ubuntuforums.org/showthread.php?t=1512418](http://ubuntuforums.org/showthread.php?t=1512418)
> Thank you all so much for your professional help with this problem - I can now boot Win again and access my apps - it was an intense experience with a severe learning curve - as a very new Ubuntu user, I even had to find out what commands like 'tar' meant, etc!

My first foray into the world of Ubuntu has taught me that I should not experiment with the OS and it's apps on my live system and as I cannot afford a second system, I guess that I will just have to stick with Windows.

A very nice person but it took 24 hrs alone to get the boot from the cd recognized by the user.

---

### Post by steveneddy on 2010-06-22
> **bcbc said:**
> And I thought we were never going to find some common ground... :)

Anyway... seriously this has gone on a bit too far. I'm always careful to recommend to wubi users to consider installing properly, I just get irritated when people like yourself slander what I consider to be a great product to showcase Ubuntu and don't have any rational basis for this. And that much has been shown.

Anything which can get Ubuntu onto the desktops of Windows users this easily should be supported, not shunned.

That is my last word on the matter. Apologies to the OP (if still around).

Wubi like Windows has it's place. But we don't need to encourage new users to continue to use Ubuntu in a Wubi install. We need to get good at instructing new users how to partition and install correctly - or get them to use Ubuntu in a VM - which we all know is more stable than a typical Wubi install - but this could be caused by the fact that most Windows installations are compromised somehow by the time that the new user "discovers" Ubuntu and Wubi.

I still don't like Wubi, but I do understand it's place and I never recommend a new user continue using Wubi after they decide that they actually like Ubuntu as an Operating System.

Also after re-reading your original posts I see that you were actually telling the OP the same thing I was suggesting - but you still seem stuck on the fact that I "dissed" Wubi.

As long as the OP understands that Wubi is a trial booter for Ubuntu and in order to use other OS's the proper way is to partition the hard drive or simply use a VM, then I think we are done here and we can close the thread.

---

