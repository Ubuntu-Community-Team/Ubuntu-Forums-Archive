---
title: "Upgrading Ndiswrapper without internet connection"
date: 2006-03-16
forum: General Help
---

### Post by tattrat on 2006-03-16
Hi, 

I am relatively new to Linux, although I am generally quite competent. 

I have a Belkin f5d7051 usb wireless adapter. My research suggests to me that if I have the latest version of Ndiswrapper, there is a good chance that this adapter will work.

I therefore need to upgrade to the latest version of Ndiswrapper (1.10). I have read and (largely) understood the (ubuntu) howto on this subject. 

It seems that in order to do this I need to download the latest version of Ndiswrapper and make it available within my Ubuntu installation (done).

I need also to remove all traces of existing version of Ndiswrapper (done).

I next need to install the linux-headers and dependencies. What are the linux headers? Can I install the versions on the ubuntu install CD or should I use the (slightly newer) ones on the (ubuntu) repository on the web?

I will also need to install its dependencies, which the howto says are: dh-make, fakeroot, gcc-3.4 & build-essential. These are not on the (ubuntu) install CD. I will therefore need to get them from the ubuntu web repository and make available in my ubuntu installation. Now, I have noticed that these mostly have extensive dependencies of their own. So my next question is, can they be downloaded as a package of some sort, or do I have to download the individual packages and workout all the dependencies and download them too?

Then my next question would be: can I then create my own repository for use with synaptic? (and if so how)!

Any answers to these questions would be most helpful and greatly appreciated! :D

---

### Post by tattrat on 2006-04-28
Well - it has been a while, but I have now found the solution to this problem, and thought I would write it up here, incase anyone else has the same problem. The solution was to download the DVD version of Breezy. 

In the mean time, the newest version of Ndiswrapper supports my Wifi card (Belkin f5d7051uk) so I am now able to use the internet connection. One little tricky stumbling block though:

After achieving connectivity and enabling all the repositories in Synaptic, nearly 100 updates were recomended. So I installed these, and on the next reboot the wrieless would not reboot. It turns out the problem is that the kernel gets updated, so that next time round Ndiswrapper requires recompilation. The trick is to download and install the latest kernel headers before the first reboot after getting the card to work, so that Ndiswrapper can be successfully recompiled after reboot. 

Works a treat now!:-D

---

### Post by LinuxQ on 2006-08-25
I have the same device but couldn't install it.
How did u install it ?

---

### Post by tattrat on 2006-08-25
before I explain, are you wired as well as wireless? And if so are you on Broadband? Also did you install Ubuntu from CD or DVD?

---

