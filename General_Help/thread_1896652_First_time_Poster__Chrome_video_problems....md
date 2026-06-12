---
title: "First time Poster:  Chrome video problems..."
date: 2011-12-17
forum: General Help
---

### Post by Mycophiles on 2011-12-17
I've had this issue since installing ubuntu (3 months).  I am a ubuntu/linux newb and have been learning as I go.  While I've done some research I can't figure out what is going on with this issue and how to solve it.

When I installed ubuntu all the drivers for my system were installed.  I didn't need to go install any drivers.

(My system is brand new. I3 w/ latest ASUS MB.  Using on-board graphics.)

here's a pic of what's going on.  It happens when I scroll through web pages.

[IMG]http://i257.photobucket.com/albums/hh206/1234Mycophiles4321/Screenshot.png[/IMG]

I greatly appreciate any help in advance.

---

### Post by fragos on 2011-12-18
Default driver supports all videos without 3D acceleration. I suggest you open the System Settings and select Additional Drivers. It will search your system to see if any special drivers are available and give you the opportunity to activate if available. System Settings is available when you click the gear icon in the upper right hand corner of the screen. There may be multiple choices, select the one marker [Recommended]. That is the first thing I would try.

---

### Post by Mycophiles on 2011-12-18
> **fragos said:**
> Default driver supports all videos without 3D acceleration. I suggest you open the System Settings and select Additional Drivers. It will search your system to see if any special drivers are available and give you the opportunity to activate if available. System Settings is available when you click the gear icon in the upper right hand corner of the screen. There may be multiple choices, select the one marker [Recommended]. That is the first thing I would try.

Thanks for the response.  This was was I was leading to when I said I didn't need to install any drivers.  I just didn't remember the 'additional drivers' name.

When i go to additional drivers I have no choices after it does the search.  It just says that there are no proprietary drivers for the system.

---

### Post by fragos on 2011-12-18
I'm not sure what I'm looking at. Is your image two screen dumps put in one image or is that what you see? The image would be more helpful if it was an attachment so we could see what you see. If we zoom in on your image to see detail it's all lost. Does it look OK before you scrolled it?

---

### Post by Mycophiles on 2011-12-18
> **fragos said:**
> I'm not sure what I'm looking at. Is your image two screen dumps put in one image or is that what you see? The image would be more helpful if it was an attachment so we could see what you see. If we zoom in on your image to see detail it's all lost. Does it look OK before you scrolled it?

It's dual monitors there sorry.  The red line across the left image in Chrome is the problem.  And YES the image is fine before I scroll, it is when I scroll that the problems occur within Chrome.

I'd take another picture if I thought it would help but that's a pretty good representation of what happens.  (in the picture (within chrome)  that red line is not supposed to be there.)

---

### Post by fragos on 2011-12-18
Only Chrome? That is strange. I've been a chrome user for a very long long time and a computer engineer since the 60's. I don't believe I've ever seen anything quite like this, particularly tied to a single application. Am I mistaken that this only happens in Chrome? I would think this kind of problem would have nothing to do with an application and indeed if software, related to the driver. Could you please give me the output of the following command in a terminal window?

lspci |grep VGA

---

### Post by Mycophiles on 2011-12-19
Here you go:
0:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by fragos on 2011-12-19
There doesn't seem to be much available relating to an i3 with built in video. As a rule Intel stuff works well because they provide open source drivers for their VGA and WiFi chip sets. The only thing I found that even remotely related was the following link. I found it by searching for "i3" on that site.

[http://askubuntu.com/questions/84786/where-can-i-download-intel-hd-vga-driver-for-my-dell-inspiron-n5010](http://askubuntu.com/questions/84786/where-can-i-download-intel-hd-vga-driver-for-my-dell-inspiron-n5010)

Other than this forum AskUbuntu is the best place for information. I follow both. At this time I can't think of anything else that may help you. Best of luck.

---

### Post by Mycophiles on 2011-12-19
I appreciate your effort.

FYI: for future users.  This does not fix the problem for me.



> PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:53 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)


> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
 afterwards

BTW: this computer is dual monitors.  One VGA one HDMI.  Both using on-board video of an ASUS P8H67-M EVO 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131710](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131710)


To note:  Chromium works great.  Chrome; however, does not. ;-)

---

### Post by Mycophiles on 2011-12-24
I was wrong... chromium doesn't work.

[IMG]http://i257.photobucket.com/albums/hh206/1234Mycophiles4321/Screenshot-1.png[/IMG]

---

### Post by fragos on 2011-12-24
Just curious, what happens if only one monitor is connected?

---

