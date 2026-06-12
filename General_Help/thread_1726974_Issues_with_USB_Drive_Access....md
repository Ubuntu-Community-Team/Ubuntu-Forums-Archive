---
title: "Issues with USB Drive Access..."
date: 2011-04-11
forum: General Help
---

### Post by Yttrium2112 on 2011-04-11
Hello eveybody, I am as most here might call me a "noob" when it comes to working in commandline system of ubuntu.  I could truly use some of your great collective knowledge in a effort to figure out an idiot problem I am having.

Basically, I simply need to be able to read and write to/from a USB flash drive to by Ubuntu 6.10/edgy system.  I have no idea at all were to begin.  Could any one of you greace this worthless noob with you assistance?  It would be wonderfully appreciated, thanks so much!

Jeff

---

### Post by 3rdalbum on 2011-04-11
Usually you can just plug it in and it will appear on the desktop, and you'll be able to read and write it. What exactly is happening or going wrong when you try to do this?

(also, 6.10 is ancient; it contains many many bugs that have since been fixed in later versions, and most people will struggle to give relevant instructions for 6.10 because things have changed so much since then. Consider updating to the latest Ubuntu?)

---

### Post by Redblade20XX on 2011-04-12
> **Yttrium2112 said:**
> Hello eveybody, I am as most here might call me a "noob" when it comes to working in commandline system of ubuntu.  I could truly use some of your great collective knowledge in a effort to figure out an idiot problem I am having.

Basically, I simply need to be able to read and write to/from a USB flash drive to by Ubuntu 6.10/edgy system.  I have no idea at all were to begin.  Could any one of you greace this worthless noob with you assistance?  It would be wonderfully appreciated, thanks so much!

Jeff

From command line?

---

### Post by Yttrium2112 on 2011-04-12
Sorry, yes from the command line.  I just can't figure out how to find it once it is plugged in.

---

### Post by leeagt on 2011-04-12
Try 
 
cd /media/<drive number>

---

### Post by Yttrium2112 on 2011-04-12
> **leeagt said:**
> Try 
 
cd /media/<drive number>

I'm at work now, but I will try that when I get home.  How do I find out the drive number after I plug it in?

---

### Post by leeagt on 2011-04-12
> **Yttrium2112 said:**
> I'm at work now, but I will try that when I get home. How do I find out the drive number after I plug it in?
 
 
do a cd /media
then ls and your drive number will be the one listed.

---

### Post by Yttrium2112 on 2011-04-12
> **leeagt said:**
> do a cd /media
then ls and your drive number will be the one listed.

When I do that, the only this listed in the media directory are:

```
cdrom cdrom0 cdrom1 floppy floppy0
```

The USB flash drive that I plugged in isn't listed.
After I plug it in and run "dmesg | grep usb", I get

```
[43120949.570000] usb 6-2: configuration #1 chosen from 1 choice
[43120949.570000] usb-storage: device found at 8
[43120949.570000] usb-storage: waiting for device to settle before scanning
[43120949.570000] usb-storage: device scan complete
```

Does that help at all?  Once I again, I REALLY appreciate the help.  Oh and I have thought about upgrading from 6.1 but unfortunately that isn't an option at the moment.  I'm hoping I can get this access to the USB drive figured out.

Thanks,
Jeff

---

### Post by Yttrium2112 on 2011-04-13
Anyone?

---

