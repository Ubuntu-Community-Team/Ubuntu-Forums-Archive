---
title: "touchpad, usb, wireless internet and cable internet not working"
date: 2011-07-13
forum: General Help
---

### Post by 42f87d89 on 2011-07-13
I recently installed ubuntu on my mom's computer but I can't get the mouse to move trough the touch pad and I suspect the USB is not working either, because I can't get anything to work trough the USB, and the Internet is not working trough the cable, and I think wireless as well. Her computer is an old acer aspire 3000. I appreciate you time.

---

### Post by ~!geek!~ on 2011-07-13
It would be good if you could check the hardware information of the system having these problems. 

I don't remember if hwinfo was there by default on my system or I installed it. You may type hwinfo in terminal to check. If system recognizes this command you will get a lot of output. You may go through this output and see which devices are being identified by your system. Look for the words touchpad usb and whatever device you are not able to see working. The whole idea is to check the devices if kernel is helping your system by identifying the devices in question or not. If hwinfo doesn't work, you may try lsusb command with some usb device connected and check the output.

I m afraid the commands I mentioned above are to be installed first to make ubuntu use them. Since your machine is unable to connect to internet, so you might have problems getting system information. In that case you may try google to know about some already installed command on ubuntu which can give you system info. A quick google search took me to a page with link: [http://cviorel.easyblog.ro/2008/02/19/get-system-information-using-the-terminal/](http://cviorel.easyblog.ro/2008/02/19/get-system-information-using-the-terminal/) See if you are able to get information regarding devices causing trouble. 
I hope after that google or this forum would be able to help you.

---

### Post by 42f87d89 on 2011-07-13
Thanks a lot! I don't know how I should get in the terminal though, is there a command on the keyboard that opens that up? My mouse is not working.

---

