---
title: "How to switch graphics adapter(ATI Mobility Radeon 5450-&gt; Intel GMA) in 10.10"
date: 2010-10-19
forum: General Help
---

### Post by rdf07 on 2010-10-19
Hi all,

Installed Ubuntu 10.10 on fresh HP dm4-1050so laptop and encountered problems, this is one of them..

Noticed that ATI card is heating heavely with default installation and I would like disable it and switch to use Intel's GMA. Also tested ATI proprietary fglrx driver through Administration->Additional Drivers, after booting got empty screen so I switched back. Afterwards read from documentation that 5450 is not supported, so no wonder.

So what is the simplest way of disabling ATI and using only Intel's gma? 

Here's what I got with lspci -v:
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1469
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4050 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1469
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at c4400000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at c4440000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

```

---

### Post by neotrix on 2010-11-11
Any solution yet? I have exactly same situation.

---

### Post by rodrigosavage on 2010-12-20
Ha, I have the same problem any solution yet?

is this thread abandoned?!?!

---

### Post by Sonicrulz12 on 2010-12-20
So you want to switch graphics cards just go to System-Administration-Additional Drivers and the drivers should appear

---

### Post by Sonicrulz12 on 2010-12-20
oh i see you've already tried it well sorry im kind-of a newbie too

---

### Post by Mark Phelps on 2010-12-21
Is this a dual-boot laptop with a Windows version running as well? If so, that could pose some problems.

I believe that what you will have to do on the Ubuntu side is the following:
1) Go into the BIOS and disable the ATI graphics card
2) Boot into Ubuntu, but get into the GRUB menu and choose the option to give you only a command line
3) Once in the CLI, enter the following "sudo dpkg-reconfigure xserver-xorg"  This should walk you through the options of setting up your display using the Intel onboard graphics.

When you reboot into Ubuntu, you should be using the Intel graphics.

Problem that I've read about on these machines, is that if you later re-enable your ATI graphics (to use in Windows), when you reboot Ubuntu, it will choose that by default, and since you will have Intel drivers installed, you will get no video.

---

### Post by Dr. D on 2011-03-29
I have the same laptop/problem and my BIOS won't give me any option related to video settings, any idea?

---

