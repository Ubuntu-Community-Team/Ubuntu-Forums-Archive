---
title: "USB devices not detected nor mounted"
date: 2012-09-20
forum: General Help
---

### Post by jesuisbenjamin on 2012-09-20
Hello,

Kubuntu 12.04 on Acer Aspire One used to mount USB devices and suddenly they seem not to be detected nor mounted.

The same occurs with a USB flash memory disk and a Nokia mobile phone.

When running lsusb, the USB devices is listed, but it is not seen in the file browser nor in the device notifier.

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 003 Device 003: ID 19d2:fff1 ZTE WCDMA Technologies MSM 
Bus 003 Device 006: ID 0421:08bc Nokia Mobile Phones 

```

Can you help fix this? Thank you.

---

### Post by jesuisbenjamin on 2012-09-30
Hey friends! Is there no one to help me on this case? :,(

---

### Post by drmrgd on 2012-10-01
If you click the little USB icon (Device Notifier) in the task manager, can you see the device(s) listed? If they do show up in there, you'll see a little picture of a hard drive, with a little black square at the corner.  If the square has a diagonal line, that means it's not mounted, and you need to click the plug icon on the right to mount it.  

You can also change the behavior of how USB devices are mounted when they are plugged into the system in System Settings -> Removable Devices.  I think by default the "Enable automatic mounting of removable media" is disabled, and I'm wondering if an update or something has changed the behavior of this on you system so that things are not automounting now.  You can play with these settings to get devices to mount as you like.

---

### Post by jesuisbenjamin on 2012-10-01
The devices are not listed.
The same devices were listed before, they suddenly stopped being listed and mounted.
I will see these options but since i haven't changed them and it worked before, i doubt it would be the cause.

Thanks.

---

### Post by drmrgd on 2012-10-01
I was afraid that was going to be the case.  It was the most simple thing to check first, though. 

I'm not entirely sure how the automount protocol works to be honest.  The only other thing I would check is dmesg after you've plugged the device in to see if it's associating it with a /dev location.  

Maybe someone with a little more knowledge of how the automounting system works can chime in.

---

