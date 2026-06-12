---
title: "using USB devices from a guest OS in VirtualBox"
date: 2011-06-08
forum: General Help
---

### Post by lz1dsb on 2011-06-08
After installing the latest version of VirtualBox (4.0.8) and the extension pack which goes with it I discovered that I'm able to use USB devices from the guest system. 
I tested it with a standard USB flash and it works like a charm. Now here comes the issue. 
I have an old Microchip clone programmer and debugger (clone of ICD2) and I decided that I should give it a shot. So I configured it into the filter for the guest system and than plugged it in. When I execute lsusb from the guest it shows the correct reading, but my programmer isn't recognized from the application that should be using it. 
So I'm just curious if anybody have tried this with a USB device which is different from the mass storage device type like the USB sticks. 
What I've read on the VirtualBox's site is that the sharing of the USB ports between the host and the guest system isn't direct. It goes through an abstraction layer. So I'm thinking that it might be possible that not every type of USB device is supported. 
Or maybe my Linux setup for this programmer is wrong. I'm still new to the Microchip tools running in Linux. So far I've only used them on Windows.

---

### Post by lz1dsb on 2012-01-16
I guess that this thread has died. 
Anyway. Just for the record, I wasn't able to start anything different than USB mass storage device. I guess this is a limitation of the abstraction layer that VirtualBox builds. 
I'll check it out again with the newest versions...

---

