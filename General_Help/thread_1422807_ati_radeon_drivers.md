---
title: "ati radeon drivers"
date: 2010-03-05
forum: General Help
---

### Post by xpiercex on 2010-03-05
hello i have a ati radeon x300 series video card and i cant get the 3d acceleration to work
for example when i try to enable desktop effects it says searching for drivers and then visual effects could not be enabled. im sorry if this sounds like a dumb question im new to linux. i hit alt f2 and typed in compiz --replace but it just makes my screen flicker and nothing happens. please someone help me. is there anything i can do besides buying a new video card?

---

### Post by pastalavista on 2010-03-05
> **xpiercex said:**
> hello i have a ati radeon x300 series video card and i cant get the 3d acceleration to work
for example when i try to enable desktop effects it says searching for drivers and then visual effects could not be enabled. im sorry if this sounds like a dumb question im new to linux. i hit alt f2 and typed in compiz --replace but it just makes my screen flicker and nothing happens. please someone help me. is there anything i can do besides buying a new video card?

Make sure you have third-party repositories enabled in System->Administration->Software Sources

When that's done, check System->Administration->Hardware Drivers

The support for that card isn't great but it can work'

If you still have problems, post the terminal output of```
lshw -C video
```

---

### Post by xpiercex on 2010-03-06
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff(prefetchable) ioport:dc00(size=256) memory:dfde0000-dfdeffff memory:dfe00000-dfe1ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff
not exactly sure how to enable third party repositories either.
when i first installed linux everything was working correctly and then it just messed up.
im fairly new to computers and was bored with windows so io just installed linux. so i need step by step instructions kinda. i feel dumb compared to some of these people.i am amazed at how intelligent some people are.

---

### Post by coldraven on 2010-03-06
Support for older ATI cards is not very good.
I have a Radeon x1250 in this laptop and with ubuntu 9.04 I had bad screen flicker.
However with 9.10 it is very good for normal use and compiz works fine.
However 3D is very slow, as a test I installed Extreme Tux racer and only got 4fps.
(this is a 2Ghz dual core 64bit with 4GB ram)
Also programs that use Wine can have problems with overlays, Google Earth for example.
Some KDE progs like Kstars also don't display properly.

In your case I would change the video card for an Nvidia, but which one I don't know.

---

### Post by pastalavista on 2010-03-07
You can download the Linux driver for your card at the bottom of this page 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English")

I sent installation instructions via PM. Good-luck

---

### Post by 3rdalbum on 2010-03-07
> **pastalavista said:**
> You can download the Linux driver for your card at the bottom of this page 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English")

**No you can't.**

>  The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Ubuntu 9.04 was released later than that. 9.04 and above will not work with that old driver.

> All future ATI Catalyst&#8482; releases made available past the ATI Catalyst&#8482; 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

Newer ATI driver releases will not work with your card.

(Emphasis added so the OP wouldn't install the driver and cause a blank screen).

I recommend buying a newer Nvidia graphics card; their 8000 series is cheap and well-supported.

---

### Post by xpiercex on 2010-03-07
i tried installing it in terminal and it just says error and shuts down abruptly. and i just tried to run it and it opens a seperat file and then quickly shuts down. i really dont have the money to buy a new video card. and up until two days ago it was working fine. i installed linux about two weeks ago. the 3d acceleration and all the neat effects were working for a little over a week.

---

