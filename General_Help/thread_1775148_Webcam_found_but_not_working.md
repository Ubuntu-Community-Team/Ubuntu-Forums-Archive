---
title: "Webcam found but not working"
date: 2011-06-04
forum: General Help
---

### Post by arabuli on 2011-06-04
Hello, I have Genius Slim 311R webcam and it is not working with my Ubuntu. It has built-in microphone and it is working fine but video is not working. Cheese says: No device found. I tried to test it with gstreamer but when I click on test button it gives me this error: "Video for Linux 2 (v4l2): Could not open device "/dev/video0" for reading and writing."

I am new in Ubuntu (Linux) and I really need your help.

Thanks.

---

### Post by wgarcia on 2011-06-04
When you say "found" what do you mean? If you plug in the camera, open a terminal and enter "dmesg" and intro, can you see something related to the camera in the last lines?

---

### Post by no2498 on 2011-06-04
in the gstreamer-properties did you set it to auto find your cam
did you try v4l1 also

---

### Post by arabuli on 2011-06-04
Thanks for replies.

**wgarcia**
I mean it shows me "device recognized" and microphone is working too. 

Here is last lines of "dmesg":

[   33.831789] vboxdrv: Found 2 processor cores.
[   33.832233] vboxdrv: fAsync=0 offMin=0x1ad offMax=0x8f0
[   33.832391] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.832393] vboxdrv: Successfully loaded version 4.0.8 (interface 0x00180000).
[   35.804352] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   38.915820] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   81.499199] r8169 0000:02:00.0: eth0: link up
[   81.499430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   90.685796] r8169 0000:02:00.0: eth0: link down
[   92.320010] eth0: no IPv6 routers present
[   92.405171] r8169 0000:02:00.0: eth0: link up
[  443.128032] usb 5-2: new full speed USB device using uhci_hcd and address 2
[  443.443643] usbcore: registered new interface driver snd-usb-audio


**no2498**
I tried everything in gstreamer but it is still not working.

---

### Post by gordintoronto on 2011-06-04
What does lsusb say?

What version of Ubuntu? 10.10 has a problem; the fix is described in Issue 44 of Full Circle Magazine.

---

### Post by arabuli on 2011-06-04
Hi gordintoronto. I have Ubuntu 11.04.

Here is output of lsusb:

Bus 005 Device 002: ID 0458:704b KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by wgarcia on 2011-06-05
When you obtained the last lines of "dmesg" I presume you had unplugged and plugged the camera before, right?

If that is the case, and also according to the output of lsusb, the camera is not being recognized as such, there is nothing there telling of a camera being seen.

---

### Post by no2498 on 2011-06-05
on some lap tops you need to push the fn+f10 bottons to turn on the cam

---

### Post by arabuli on 2011-06-06
**wgarcia**

Yes I unplugged and plugged and dmesg gives me this:

[   32.649266] vesafb: framebuffer at 0xfb000000, mapped to 0xf8580000, using 1216k, total 1216k
[   32.649270] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   32.649271] vesafb: scrolling: redraw
[   32.649273] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   32.649766] Console: switching to colour frame buffer device 80x30
[   32.662244] fb0: VESA VGA frame buffer device
[   32.762588] r8169 0000:02:00.0: eth0: link up
[   32.763501] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.216052] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   41.382874] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   43.120021] eth0: no IPv6 routers present
[ 1592.509019] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 4007.520785] ptrace of non-child pid 24589 was attempted by: opera-next (pid 25534)
[ 4017.712375] do_general_protection: 12 callbacks suppressed
[ 4017.712382] opera-next[24589] general protection ip:8db9b19 sp:bff9eda0 error:0 in opera-next[8048000+1021000]
[ 4208.480051] usb 5-1: USB disconnect, address 2
[ 4210.836030] usb 5-1: new full speed USB device using uhci_hcd and address 3.

**no2498**
Thanks for reply but I have desktop computer.

---

### Post by wgarcia on 2011-06-06
The camera is not seen by your system, according to the dmesg output. It seems that your camera is a Sonix SN9C201 camera, according to this post:

[http://www.linuxquestions.org/questions/linux-hardware-18/webcam-support-genius-slim-311r-703967/](http://www.linuxquestions.org/questions/linux-hardware-18/webcam-support-genius-slim-311r-703967/)

and it seems badly supported for Linux. There is some talk of some drivers but I haven't seen any report of anybody being able to use this camera properly under linux.

---

### Post by arabuli on 2011-06-06
**wgarcia**
Thanks for replays. I have Genius Slim 311R. That means that my camera will not work on Linux?

---

### Post by no2498 on 2011-06-07
[http://www.linuxquestions.org/questions/linux-hardware-18/webcam-support-genius-slim-311r-703967/](http://www.linuxquestions.org/questions/linux-hardware-18/webcam-support-genius-slim-311r-703967/)


on there they say some got it working

---

### Post by arabuli on 2011-06-08
**no2498**

I am an absolute newbie and I don't know how to do that. Thanks anyway.

---

