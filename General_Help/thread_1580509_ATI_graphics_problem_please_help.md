---
title: "ATI graphics problem please help"
date: 2010-09-23
forum: General Help
---

### Post by Opperkip on 2010-09-23
After i installed my ati grapics driver (the ati driver from the ati website) my ubuntu has this weird problem.
when loading there is a line that cought my attention:
Running DKMS auto installation service for kernel 2.6.34: fglrx (8.543)...Failed

I think that has something todo with the other error i get which is:
Primary device is not PCI
(EE No devices detected)

Fatal server error
no screens found
giving up.

Is there anyone who could help me with this problem?
I have an ATI 5650 Radeon mobile grapics card By the way.

---

### Post by Mark Phelps on 2010-09-23
Sorry, don't have the specifics, but there have been a bunch of recent posts dealing with ATI driver problems and apparently, AMD is working on a patch to fix this.

I believe it already is available, but you have to enable a ppa -- and not having a supported ATI card, I don't have those details.

You could try a search either in this forum, or in the Video forum.  You might then turn up those threads and get the details of the patch and when they expect it to be available.

---

### Post by dirt_diver on 2010-09-23
Had the same problem but this helped me:
 
> Re: FGLRX wont install
I also stumbled upon the same problem today..
So what I ended up doing was:

1) removed the 32-24 kernel:
Code:
sudo apt-get remove --purge linux-headers-2.6.32-24 linux-headers-2.6.32-24-generic
2) removed the manually installed, but broken fglrx drivers:
Code:
sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-dev
3) installed the old kernel:
Code:
sudo apt-get install linux-headers-2.6.32-23 linux-headers-2.6.32-23-generic
4) installed fglrx from the repos (which installed with no problem on 32-23):
Code:
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev
5) and finally, activated the proprietary drivers from "hardware drivers" and rebooted

This works fine, but not under 32-24, cause as soon as I install linux-headers-2.6.32-24 and boot into it, the proprietary drivers get broken again. So I guess I'll just have to wait until they fix the compilation bug under 32-24

Hope it helps.

Regards,
progre55 
 
Hope it helps...

---

### Post by Opperkip on 2010-09-23
I don't wanna be mean. But none of those commands work for me.
It might be worth noting that im using linux version Backtrack.
Becaused its based on ubuntu i figured that you guys might be able to help.
Anyone else a thought?

---

### Post by schnelle on 2010-09-23
This ppa has updated drivers : [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I updated my ati card with driver from this ppa and everything works quite good.

To add this repository to your system type in Terminal: ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

Then ```
sudo aptitude update
sudo aptitude safe-upgrade
```

When you finish these steps you will have the latest ati driver installed.

If you have removed ati proprietary driver go to Hardware Drivers and enable it. Then reboot your system and you should have the latest driver installed and working.

---

### Post by Opperkip on 2010-09-23
my terminal tells me that apt-add-repository: Command not found
any ideas why that would be?

---

### Post by schnelle on 2010-09-23
Which version of Ubuntu do you use? Command apt-add-repository is added in 9.10 (Karmic Koala). 

Because your ati card is quite new (5xxx series) i advise you to install latest Ubuntu/Kubuntu (10.04) and then do steps from my previous post.

---

### Post by osmorphyus on 2010-09-23
i have an ATI radeon 2650, 256Mb video card.  i can't get beyond 1024x768 for resolution, as well, there is a slight overscan to the far right of the screen.

what can i do to get a higher res. out of this card?

---

### Post by economath on 2010-09-24
I have a similar problem. I have an ATI Radeon HD 5600 and am using Ubuntu 10.04 on a Dell Studio 17. I hope to be able to use the cube. Half way through downloading and installing the ATI/AMD proprietary FGLRX graphics driver (i.e. activating it), I got the message: 

> SystemError: installArchives() failedSo, I tried schnelle's suggestion up to the point of 

> If you have removed ati proprietary driver go to Hardware Drivers and enable it.
I am not sure how to remove the ati proprietary driver; I then went to try and enable the driver again but am getting the same error message.

Can anyone suggest possible solutions?

Thanks in advance!

---

### Post by schnelle on 2010-09-24
@economath

Other people had the same problem. Look at these threads and see if something helps:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1450040&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1450040&page=3)

[http://ubuntuforums.org/showthread.php?t=1425993](http://ubuntuforums.org/showthread.php?t=1425993)

---

### Post by coffeecat on 2010-09-24
> **Opperkip said:**
> my terminal tells me that apt-add-repository: Command not found
any ideas why that would be?

Because you're not using Ubuntu. Backtrack might be Ubuntu-based but it's highly reconfigured.

From the [BackTrack hompage]("http://www.backtrack-linux.org/"):

> BackTrack has been customized down to every package, kernel  configuration, script and patch solely for the purpose of the  penetration tester. Note the kernel configuration. Fixes that work on Ubuntu may not work on BackTrack. You might be better off in the BackTrack forum.

Why are you using BackTrack?

---

### Post by economath on 2010-09-24
Thanks for the links, but unfortunately, no success. I had tried (most of) the suggested solutions in those pages already, but they did not work for me. 

I am informed that reinstalling Lucid Lynx has solved the problem. Is there another way? Short of reinstalling Lucid Lynx, I uninstalled all the packages that  fglrx needs based on a reinstallation of Lucid Lynx. When I attempted to  reinstall fglrx via Synaptic, I encountered the same package error.

The problem is that the fglrx driver is failing to install.

                     p { margin-bottom: 0.08in; }> E: fglrx: subprocess installed post-installation script returned error exit status 10 
 E: fglrx-amdcccle: dependency problems - leaving unconfigured 
 One caveat is that when I tried the following code, I wasn't sure what "kernel", "source" and "driver" referred to or whether they needed to be replaced by numbers, etc.
[http://ubuntuforums.org/showpost.php?p=9062521&postcount=158](http://ubuntuforums.org/showpost.php?p=9062521&postcount=158) 
> 
sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-devAny suggestions?

---

### Post by Opperkip on 2010-09-25
I am using Backtrack because it contains a lot of apps i need to have for my schoolwork.
I'll also try the Backtrack forum. Thx anyways.

---

