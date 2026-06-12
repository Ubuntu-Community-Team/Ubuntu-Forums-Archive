---
title: "Error creating moint point: No such file or directory."
date: 2011-04-19
forum: General Help
---

### Post by mountainmanmark on 2011-04-19
I just bought a USB flash drive. Whenever i click it to open its contents it gives me the error " Unable to mount USB20FD " then  under that it says "Error creating moint point: No such file or directory " (btw it does say moint point and not mount point, which is kind of weird. Anyways, I'm wondering if anyone knows how to solve this problem so that i can use the flash drive i just bought.

---

### Post by mountainmanmark on 2011-04-19
So, i just plugged in a USB Flash drive to my computer. For some reason when i click it, it gives me the error " Unable to mount " and then under that it says "Error creating moint point: No such file or directory". I know that this is not a problem with the USB Flash drive itself as i have used it on a live cd with linux mint. I also get this same error whenever i plug in any storage medias through the USB ports. Does anyone have an idea as to what is causing this error?

---

### Post by garvinrick4 on 2011-04-19
> **mountainmanmark said:**
> So, i just plugged in a USB Flash drive to my computer. For some reason when i click it, it gives me the error " Unable to mount " and then under that it says "Error creating moint point: No such file or directory". I know that this is not a problem with the USB Flash drive itself as i have used it on a live cd with linux mint. I also get this same error whenever i plug in any storage medias through the USB ports. Does anyone have an idea as to what is causing this error? Did you remove the drive while it was still mounted at one time. Reformat is salution I do believe.
One mans opinion.

---

### Post by mountainmanmark on 2011-04-19
> **garvinrick4 said:**
> Did you remove the drive while it was still mounted at one time. Reformat is salution I do believe.
One mans opinion.

I Tried reformatting it. No go.. Earlier when i couldn't get it to work with ubuntu, i loaded up a live cd of linux mint and it did work with that. But when i try to open it with ubuntu it gives me an error.

---

### Post by varunendra on 2011-04-20
Not sure why it happens sometimes, but you may try pmount or usbmount. These are in default repositories, and are intended as convenient solutions to this problem.

A hint for preference:
> USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.

---

### Post by cariboo on 2011-04-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by celsdogg on 2011-04-20
you might want to dd the device. I once had a problem with a tdrive where I couldnt get it to work properly. after troubleshooting for some time, i dd'ed it, formatted it, and it has worked properly ever since. i wrote zeros to it btw.

dd if=/dev/zero of=/dev/<usb device name>

---

