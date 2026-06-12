---
title: "HP 2133 mini won't automatically recognise usb devices until reboot."
date: 2011-03-19
forum: General Help
---

### Post by SeeingBlue on 2011-03-19
I install Ubuntu netbook on this HP 2133, I spent all day yesterday fighting the wireless, & don't even know how it started working when I booted it up this morning, just hoping it works after I reboot..<crosses fingers> it did!

Now I have a new problem, when I plug in a USB drivce(flash drive, mouse)the computer nor disk utility will recognise it until I reboot. I have checked that media_automount & media_automount_open are checked.

Funny thing is this seem to be intermittent, this is what happened just now. I plug in a usb flash drive, doesn't work. I plug in a usb MS mouse, won't work. I unplug a usb flash drive and plug it back in.. it works now.. i try the same with the MS mouse & it don't work. I reboot & they both now work even after I unplug them and plug them back up.

How can I fix this so that they work the first time?

Thank you

---

### Post by 5149.5 on 2011-03-19
Open a terminal, enter lsusb. Paste the result in a post.

---

### Post by SeeingBlue on 2011-03-19
I would have done that but they are both working now. I have some other devices I will hunt down & try that. Althought I tried the flash drive yesterday & it wasn't working until after reboot, but stopped working at first again today, then started working again & has been working since.

I did try lsusb while the mouse was plugged in and I saw one item that read Microsoft Corporation but that was all. I now confirmed that it was my mouse. So lsusb was reading them when nothing else was.

---

### Post by RJ12 on 2011-03-19
I had this problem to, see if this command will let you use the USB device before you reboot

```
sudo modprobe usb-storage
```

For the mouse

```
sudo modprobe usbhid
```

---

### Post by SeeingBlue on 2011-03-20
Thanks for the commands, I will try them the next time I have this issue.

---

