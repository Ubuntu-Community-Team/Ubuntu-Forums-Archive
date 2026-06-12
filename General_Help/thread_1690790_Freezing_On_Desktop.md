---
title: "Freezing On Desktop"
date: 2011-02-19
forum: General Help
---

### Post by Konfusi0n on 2011-02-19
I was trying to install Ubuntu over Windows XP 64-bit and the installation kept freezing, I decided to use the alternate installer and it worked. My only problem now is that I can't run Ubuntu for more that 2 minutes without it freezing on my and the only way to fix it is by holding my power button on my computer to shut it off. Sometimes it just restarts without freezing so I would be doing something and then my screen would turn black and reboot my PC.

I think Ubuntu is cool and I am fairly new to it. I would like to keep using it but I have to use recovery mode to be able to use it without crashing. (Low Graphics Mode or W/E it is called.) I have no idea what is causing these freezes. I have installed the Linux drivers and updated everything and it still happens to crash while I am using it outside of Recovery mode.

Any help please?

---

### Post by fabricator4 on 2011-02-19
Did the live cd run alright?  If you've got plenty of memory (512 MB) then the normal installer and live cd will work fine if it's going to work at all.

You didn't say what version, or what specs the machine is. It also seems to be related to your graphics card so we need to know what that is also.

Since you're having problems it might be good idea to start with the 32 bit 10.04 LTS.  Run Live CD, do the install, and work from there.

Chris

---

### Post by Konfusi0n on 2011-02-19
**                                                                                                                                       Computer Specs**:
[CENTER] **- Processor:** AMD Athlon&#8482; 64 X2 Dual Core Processor 4200+ 2.20 GHz
**- RAM:** 3.5GB
**- Hard Drive:** 300GB HDD
**- Graphics Card:** NVIDIA GeForce 450 GTS 1.7GB GDDR5
**- Motherboard:** MCP61PM-HM (Nettle)
**- Computer:** HP Pavilion a6042n

I am currently running Ubuntu 10.10 64bit AMD and I have my graphics card drivers installed already on here.


[/CENTER]

---

### Post by Konfusi0n on 2011-02-19
Another question, what does it mean by long term support and how is it different from what I have currently?

---

### Post by fabricator4 on 2011-02-19
> **Konfusi0n said:**
> Another question, what does it mean by long term support and how is it different from what I have currently?

A normal release is supported with critical updates, other updates etc for 18 months. Generally the release immediately after the LTS release is the most problematic, because the developers have to take the opportunity to add as many new features and devices as they can.  The objective is to get as much fine tuned for the next LTS release as possible.

LTS releases are supported with critical updates etc for three years.  Every 24 months the release is an LTS release, in April.  While a new release may get substantial updates in the first few months they do tend to dwindle over time.  I can tell you that the number of updates for my 10.04 machines is very few now, though if you load from the 10.04 Live CD and update you'll get several hundred MB of updates; the cumulative updates of everything that is current.  The next LTS release will be 12.04

Because of the way the release cycle works, the LTS releases are the most stable and mature.  It's what I recommend for new users who haven't run Ubuntu or Linux before, or those just wanting the most stable machine. The exception would be if there's better hardware support in a newer release that the LTS doesn't have.  This occurred in 9.04 with better support for wireless networks and bluetooth etc (I believe - my memory may be faulty). 

The 32 bit versions also seem to get faster bug fixes and updates, possibly because more is reported faster.  Eventually the 64 bit versions will be the mainstream, but I don't believe that has happened yet, and won't for a while.  64 bit users may jump on me for this statement if they wish :-)

So yes, if you're having problems I'd say try the 10.04 LTS in 32 bit flavour and see if that works better for you.  If it does, you have a working baseline to investigate problems with the 64 bit and later releases.

Now, I do know the NVidia Geforce cards have had some problems.  I don't run one so I can't actually say if the main problems have been fixed in 10.04 but there will be work-arounds.  Usually, you can run a low-res SVGA mode while you get it working, and if so 10.04 may set this by default.

Try the i386 10.04 Live CD and see if it boots and runs OK.  Only then would I go ahead and install it.  The alternate CD is good if you want to do a minimal install, do unattended installs on lots of machines, or if it's the only way to do an install with a view to fixing problems afterwards.

Chris

---

### Post by Konfusi0n on 2011-02-19
I solved it, I realized that my mouse wasn't compatible so that it wouldn't work when no apic was enabled so I found another one that worked when no apic was enabled and no more crashes or freezes!

---

### Post by fabricator4 on 2011-02-19
Ah well.  Mark the thread solved then. :-)

C

---

