---
title: "Ubuntu Graphics problem ... Major Problem"
date: 2011-02-06
forum: General Help
---

### Post by janpansa on 2011-02-06
System specs:

[Hp nx6110 intel centrino , 512mb ram , ubuntu 10.04 lucid , intel 915 gfx]

Hey guys , I might be, what they call a "noob" , when it comes to ubuntu , but heres the problem. Let me tell you the whole story in short. I recently installed minecraft on my notebook and everything went well , except that it lagged. I checked that my cpu wasnt maxed but my ram was running kinda high , obviously , because I only have 512mb ram. Anycase , I was still running the driver configuration that ubuntu configured for me , so I figured that , maybe I can play around with the settings to improve minecrafts performance. Alright , so I have an Intel 915 display device in my notebook and I read up that xorg is kinda the only way to go , so I installed xorg , following wiki instructions. Well , all was still working except minecraft had texture issues. The tutorial also said I should upgrade the kernel , so I did , ... I went from 32 to 37 . After that , **** became real and ubuntu decided to throw out the one graphics error after the other. First of all , the resolution wasnt quite right. Most of the time I have a black bar at the bottom , "indicating" that the screen shifted about 20pixels upward. Also , sometimes when I restart ubuntu , it goes into low graphics mode and I have to temporatily login like that. Also , I cannot run compiz at all. When I go to hardware drivers , there is absolutely no trace of any intel device or driver. Alright , now , heres what I have tried so far to fix the problem and all of the times I have failed epicly. 

- I have completely removed xorg several times. (full remove including xserver and core files.)
- I have configerd the xorg.conf file several times , each time , trying something different that someone suggested for the 915 graphics or intel chipset.
- I have also edited the xorg.conf file to stadard generic settings with no luck.
- I have reconfigured xorg through the terminal.
- I have added the sources for intel drivers , updated and installed the latest drivers , and it shows in synaptic that the latest intel drivers are installed.i9xx ....
- I have upgraded and downgraded from kernels to see if that was the problem. (from 32 to 38 to 37 back to 32 again at the moment.)
- other - my ubuntu is fully upgraded.
           - I cannot run compiz effects , however , It was running smoothly before...
           - compiz says , searching for available drivers --> could not enable desktop effects.

Thats about it... I really dont want to re-install a fresh ubuntu. (However this seems like the only option I have left *sigh*)

Any help would be much appreciated.

---

### Post by I&#9829;HTML5 on 2011-02-06
Try checking for proprietary drivers: System | Administration | Additional Drivers

---

### Post by janpansa on 2011-02-07
> **I&#9829 said:**
> Try checking for proprietary drivers: System | Administration | Additional Drivers

Hi there and thank you for responding. I don't have that option in my ubuntu. Only option is Hardware Drivers , and when I click on that , it says No proprietary drivers are in use on this system , however , I think it should say that because intel's drivers are open source and gets installed with ubuntu ...?

Any help would be great , thx !

---

### Post by Mark Phelps on 2011-02-07
Sigh ... I wish folks would read the details before responding ...

The Hardware Drivers option only works for ATI/NVIDIA restricted video drivers and some Wireless drivers.  It does NOT work for Intel video drivers.

You've made so many changes to core items in your setup that it's going to be virtually impossible to get it back into working order simply by restoring individual packages or the kernel.

Only a complete reinstall is likely to get you back to a working condition.

In future, if you're going to "hack around" like this, explore using CloneZilla, rsync, or remastersys (or other options) to image off, or otherwise backup, your system before making these kinds of changes.  That will vastly simplify the process of restoring a working system.

---

### Post by janpansa on 2011-02-07
> **Mark Phelps said:**
> Sigh ... I wish folks would read the details before responding ...

The Hardware Drivers option only works for ATI/NVIDIA restricted video drivers and some Wireless drivers.  It does NOT work for Intel video drivers.

You've made so many changes to core items in your setup that it's going to be virtually impossible to get it back into working order simply by restoring individual packages or the kernel.

Only a complete reinstall is likely to get you back to a working condition.

In future, if you're going to "hack around" like this, explore using CloneZilla, rsync, or remastersys (or other options) to image off, or otherwise backup, your system before making these kinds of changes.  That will vastly simplify the process of restoring a working system.

thx , sounds like a fine idea.

---

### Post by I&#9829;HTML5 on 2011-02-08
Mark Phelps: Sorry, I couldn't remember what drivers were restricted. I didn't mean to annoy.

---

