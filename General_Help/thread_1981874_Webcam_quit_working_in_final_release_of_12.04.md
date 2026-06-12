---
title: "Webcam quit working in final release of 12.04"
date: 2012-05-17
forum: General Help
---

### Post by irv on 2012-05-17
For some reason my webcam is not being recognized in 12.04. It was working when I was beta testing 12.04 but now it is not. I tried it with cheese and  guvcview with the same results. In guvcview the error is 
> Guvcview error:

Unable to open device
Please make sure the camera is connected
and that the correct driver is installed.

What changed from the beta to the final release? I am running the 64 bit version.
Anyone have an idea on what I can try?
Thanks

---

### Post by philinux on 2012-05-17
> **irv said:**
> For some reason my webcam is not being recognized in 12.04. It was working when I was beta testing 12.04 but now it is not. I tried it with cheese and  guvcview with the same results. In guvcview the error is 


What changed from the beta to the final release? I am running the 64 bit version.
Anyone have an idea on what I can try?
Thanks

Does the old lsusb show it.

---

### Post by irv on 2012-05-17
This was a problem on and off with the Alpha/beta releases up to the final release of 12.04. I know it was a problem in the 64bit version, but I don't know if it was in the 32bit version because I didn't Alpha/beta test that. Here is a link to the thread I had going when testing.
[http://ubuntuforums.org/showthread.php?t=1891429&page=2]("http://ubuntuforums.org/showthread.php?t=1891429&page=2")
Was wondering if any one else was dealing with this problem?
Output from lsusb
```
Bus 001 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
```
I am using a Dell inspiron 1521 laptop.

---

### Post by irv on 2012-05-18
I marked this solved because it is working again. I have no idea whats going on but it just started working again. I did not reboot or anything, all I did was change locations. When I move around I just put my laptop in suspend mode. The cam was not working yesterday at the coffee shop, but now that I am home again it is working. Maybe I have a bad wire in my laptop lid and when I open and close it works and does not work.

---

