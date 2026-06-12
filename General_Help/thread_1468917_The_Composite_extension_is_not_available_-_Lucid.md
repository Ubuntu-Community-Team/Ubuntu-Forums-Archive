---
title: "The Composite extension is not available - Lucid"
date: 2010-05-01
forum: General Help
---

### Post by Pingster on 2010-05-01
I know this topic has been beaten to death, but some solutions don't work and I don't understand the rest.

I did a clean install of Ubuntu 10.04 except for the /home partition.  I have two monitors.
I can't get the setup I had on 9.10 where the second monitor was an extension of the first, and extra visual effects were enabled.

There are two drivers available for my video card, NVIDIA accelerated graphics driver (version 173) and NVIDIA accelerated graphics driver (version current) [Recommended].  I've tried both.
I backed up my /etc/X11/xorg.conf, blanked the current one, and run
```
sudo nvida-settings
```I set the each monitor to be a separate X screen, enable Xinerama (I think that's what I need for the extended display), and clicked Save to X Configuration File.  Sometimes I merge it with the existing file.  At this point I restart and the error, "The Composite extension is not available" is displayed when I try to enable extra visual effects.

What am I doing wrong?

---

### Post by Homer on 2010-05-02
Hi,

I have the exact same problem.

Was using Ubuntu 8.10 with 2 screens.  I made a clean reinstall of Ubuntu 10.04 but I kept my /home partition.

Until I activate my second screen with nvidia-settings, I was able to get desktop effect. 

No idea how to enable them now... I get "The Composite extension is not available"...

---

### Post by Homer on 2010-05-02
I found this bug : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/558875](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/558875)

Disabling Xinerama "fix" the problem...

---

### Post by Pingster on 2010-05-03
That's a good idea, but interestingly, it prevents interaction of any sort between the two monitors.  That almost defeats the purpose of my having two monitors.  I do like the fact that without Xinamera I get a panel on each screen.

---

### Post by Pingster on 2010-07-06
This is still a problem and I've done all kinds of reinstallations, clearing xorg.conf, disabling and re-enabling of drivers, etc. and I still have no desktop effects.
In addition, the Monitors applet in System > Preferences gives 

Could not get screen information
RANDR extension is not present

It looks like the composite extension bussiness, anyway, is the same as in this bug filing: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/231697](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/231697)

If this is kernel bug or an NVIDIA failure is there some other work-around such as free drivers that allow composite + Xinerama?
I had this setup last year so I know it's not my hardware that's the problem.

---

### Post by jweaver28 on 2010-07-21
I also have a dual monitor setup, between Ubuntu 10.04 and Windows 7. When I first got Ubuntu working from within Win7 (WUBI after severe problems setting up the dual boot via the 10.04 cd as reported elsewhere), I was annoyed that dual screen was disabled, hence worked more in Win7 than Ubuntu. About a month or 6 weeks ago, I got the second monitor working in 10.04, and figured out that the mouse wasn't tracking properly between the two screens because ubuntu for some strange reason thought they were katty korner rather than vertically arranged (or even horizontally arranged as is the Win7 default). The dual display worked until about two weeks ago, when the bizarre tracking resumed. Ubuntu again thinks the monitors are arranged vertically with about a one screen offset (katty korner).

I can't get into System/Monitors to change it like I did before. All I get today is the message: "could not get screen information: RANDR is not present." Checking synaptic, LIBXRANDR2 is present, as is x11-xerver-utils (7.5+1ubuntu2) and totem. Trying to get the dual display working, I added through synaptic 8 RANDR affiliated packages, including libxcb-randr0, gnome-randr-applet, and lxrandr (0.1.1-2). No packages were removed by synaptic during that installation. And I did not try to add the developer and debugging packages because I don't have that technical expertise. 

FYI, I have been installing the normal ubuntu updates using update manager, though this AM wasn't able to get a ubuntu screen beyond the flash screen until I went into corrective mode and checked for and installed broken packages (8 installed/corrected before the 8 installations apparently involved in the RANDR attempt). FYI, this machine has an Athlon 4 core processor, Biostar MB and a GeForce 9400 video card. I'll try to file a bug report as well--the other links with this error message involve xinerama, and I don't even know what that is.

---

### Post by hoptimusPrime on 2010-08-06
please help

i go to enable desktop effects and click extra, and it gives me the "composite extension is not available" error as well.

i am using driver version 195.36.24

when i first installed the new driver, it was a nightmare.. i feel like i am so close now... maybe i have to change smeting in System>Admin>Hardware Drivers?   maybe it's because of the double rainbow?

i am also using AWN and compiz, so right now my desktop looks like a pile of poo without desktop effects enabled.  there is also a big fat ugly grey bar at the bottom of my screen beneath my AWN dock...

honestly, i haven't searched much on this, but can someone please tell me whats wrong?  what does this mean?  am i maybe using the wrong nvidia driver version?  this is pissing me off

sorry if this doesn't make sense..  too much beer, but why wont thiings just work the way i want

---

### Post by octane70 on 2010-08-15
I disabled Xinerama made sure i was using Twinview in nvidia settings, then restarted my computer.
Worked perfect for me.

---

### Post by akxiii on 2010-08-20
> **octane70 said:**
> I disabled Xinerama made sure i was using Twinview in nvidia settings, then restarted my computer.
Worked perfect for me.

Sweet, this worked for me.

Cheers, mate.
I love it when Ubuntu kicks ***, even if it takes a little hunting.

For reference I'm running Ubuntu 10.04 64bit, Nvidia driver 195.36.24 (current), GeForce 7600 GS

---

### Post by hoptimusPrime on 2010-08-21
> **octane70 said:**
> I disabled Xinerama made sure i was using Twinview in nvidia settings, then restarted my computer.
Worked perfect for me.

yeah thanks!  everything works great.  I have dual monitor, compiz, AWN and VNC all working great.  ubuntu rocks

---

### Post by Elep.Repu on 2010-12-18
Are you kidding me?
The original problem isn't solved. And Twinview is a useless 
alternative to actually having two separate screens rather than spreading it all out and calling it good. Twinview is retarded and not Good enough to settle for just because it "works."

---

### Post by .::welemski::. on 2011-01-21
Yes completely retarded... these guys doesn't seem to know what the real problem is. Just be cause they labeled it as "It worked for me" that doesn't mean it's the solution for everyone else. Completely retarded.

@Elep.Repu

I know exactly what you mean... These gusy doesn't seem to know the difference between Xinerama and twinview.

This problem is still remains a problem. Compositing only works for Twinview / SeparateX not in Xinerama.

I think think these guys meant.. is that they're happy having a twin view as long as they have compositing ( which in my opinion really defeats the purpose of buying an extra monitor ).

---

### Post by windphere on 2011-03-25
Same here.  I do not think these people have more than one screen.  I have three and could have four monitors.  I just want it to work with a little bling.  But could live without.  Someone needs to contact NVIDIA to let them know that there driver only works half way if you have more than one monitor.  I guess the more you have the less you get only if that was the case in the real world. I am just happy I am not using Windows.

---

### Post by yogiman.uk on 2012-03-08
Hi

Did this problem ever get resolved, I am suffering from it and at present I don't want to upgrade from 10.04LTS to that naff Unity desktop.

Any help appreciated.

Thanks


Yogiman!

---

