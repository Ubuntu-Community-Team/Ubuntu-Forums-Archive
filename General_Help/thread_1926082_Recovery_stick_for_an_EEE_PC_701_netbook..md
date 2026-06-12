---
title: "Recovery stick for an EEE PC 701 netbook."
date: 2012-02-15
forum: General Help
---

### Post by Bramkaandorp on 2012-02-15
The situation is pretty basic. I have a netbook with Ubuntu installed, but I want to restore it to the Xandros software that was originally on there.

Now, I still have the DVDs and the manual, but the manual says nothing about how to make a recovery stick (USB) when using Ubuntu. It just mentions Windows XP.

I'm clutching at straws here.

Anyone?

Help.

P.S. the F9 command didn't work.

---

### Post by aasdfasdfg on 2012-02-15
In Ubuntu, the usb-creator-gtk utility is used to create recovery media. See [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") and [here]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") for more info.

---

### Post by Bramkaandorp on 2012-02-18
> **aasdfasdfg said:**
> In Ubuntu, the usb-creator-gtk utility is used to create recovery media. See [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") and [here]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") for more info.

That's all good and well if I had a simple ISO to work with, but sadly that's not the case.

If the DVD was simply an image that I could use, I'd have no problem. However, the DVD contains several things that are not ISO files, and only one .IMG file which seems to me to be way too small (4 MB).

So if someone knows specifically how to make a recovery stick for an EEE PC 701 in Ubuntu using he recovery DVD, I'd appreciate it.

---

### Post by Bramkaandorp on 2012-02-18
I found a page on eeeuser.com, but it was pretty vague.

If someone could explain it, I'd probably be out of trouble.

[http://wiki.eeeuser.com/howto:usbrestore]("http://wiki.eeeuser.com/howto:usbrestore")

Especially the command given puzzles me, because when I use it, the terminal simply says that my flash drive is a folder. Nothing else.

Thanks.

---

### Post by Bramkaandorp on 2012-02-19
Bump

---

### Post by Khayyam on 2012-02-19
Bram ...

I've not done this myself, but I think the problem is that your USB stick is mounted and your passing the 'mount point' and not the 'device' to 'dd'.

Insert the stick, check its not automounted, if so unmount it. Figure out what device the USB stick is asigned ('lsusb' or 'dmesg' should list /dev/sdb or /dev/sdc depending on how many disk devices you have).

'dd' the usb.img to the device.

```
dd if=/media/ASUS_701/Software/BootTool/BootTool/usb.img of=/dev/sdX
```Where 'sdX' is the device asigned to the USB Stick.

Your disk will now have the contents of usb.img on it (a filesystem). You should then mount it and copy over the remaining files as per the instructions.

HTH ...

---

### Post by Bramkaandorp on 2012-02-20
> **Khayyam said:**
> Bram ...

I've not done this myself, but I think the problem is that your USB stick is mounted and your passing the 'mount point' and not the 'device' to 'dd'.

Insert the stick, check its not automounted, if so unmount it. Figure out what device the USB stick is asigned ('lsusb' or 'dmesg' should list /dev/sdb or /dev/sdc depending on how many disk devices you have).

'dd' the usb.img to the device.

```
dd if=/media/ASUS_701/Software/BootTool/BootTool/usb.img of=/dev/sdX
```

Where 'sdX' is the device asigned to the USB Stick.

Your disk will **not how** have the contents of usb.img on it (a filesystem). You should then mount it and copy over the remaining files as per the intructions.

HTH ...

Sorry, but I didn't quite get what you meant by the part I bolded.

If you mean that it won't be on there, then you're right.

So, if this went well, then my stick is ready, and I'll try it out tomorrow.

Thanks a bunch.

---

### Post by Khayyam on 2012-02-20
> **Bramkaandorp said:**
> Sorry, but I didn't quite get what you meant by the part I bolded. If you mean that it won't be on there, then you're right.

That should have read "your USB stick will now have the contents of usb.img on it". If the 'dd' was successful you will have created a filesystem on the USB stick, and should be able to mount it and copy over the remaining files.

HTH ...

---

### Post by Bramkaandorp on 2012-02-21
> **Khayyam said:**
> That should have read "your USB stick will now have the contents of usb.img on it". If the 'dd' was successful you will have created a filesystem on the USB stick, and should be able to mount it and copy over the remaining files.

HTH ...

In that case, it didn't work, because the stick was empty after I executed the command.

No matter though, because I've decided not to use it after all. The lack of recent updates being the primary reason for not choosing it.

In any case, thanks for your help. I just wish I'd looked at the distro itself more closely before wanting to use it again. It would have saved me (and you by proxy) some time.

Cheers

---

### Post by Khayyam on 2012-02-21
> **Bramkaandorp said:**
> No matter though, because I've decided not to use it after all. The lack of recent updates being the primary reason for not choosing it.

I see. As they've moved on somewhat from the 701 I imagine they are not likely too keep on producing updates. Its now very much 'legacy'.

I run a streamlined Gentoo on mine, and though its not ideal, it serves pretty well as a light carry-round. I do wish the keyboard were a little bigger though.  

> **Bramkaandorp said:**
> In any case, thanks for your help. I just wish I'd looked at the distro itself more closely before wanting to use it again. It would have saved me (and you by proxy) some time.

Your welcome, and no problem.

best ... khay

---

### Post by Bramkaandorp on 2012-02-21
> **Khayyam said:**
> I see. As they've moved on somewhat from the 701 I imagine they are not likely too keep on producing updates. Its now very much 'legacy'.

I run a streamlined Gentoo on mine, and though its not ideal, it serves pretty well as a light carry-round. I do wish the keyboard were a little bigger though.  



Your welcome, and no problem.

best ... khay

I might look into Gentoo. I've used Ubuntu for some time now, but it's about to get a lot bigger, so maybe I should move on when the 701 is concerned.

Thanks for the suggestion.

---

### Post by Khayyam on 2012-02-21
> **Bramkaandorp said:**
> I might look into Gentoo. I've used Ubuntu for some time now, but it's about to get a lot bigger, so maybe I should move on when the 701 is concerned. Thanks for the suggestion.

Again, your welcome. If you want Gentoo on it you will need to build the image in a chroot on a seperate machine, the 701 doesn't really have the HD capacity nor the CPU for the task. I built mine on a P4 and then used tar over ssh to copy it onto the SD. If it wasn't for the fact that I wanted a very lightweight install I probably would have gone some other route.

best ... khay

---

