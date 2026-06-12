---
title: "External hard drive slows computer"
date: 2012-05-21
forum: General Help
---

### Post by todaymueller on 2012-05-21
I am currently running Lucid Lynx and have recently found that when I switch on my external hard drive my computer slows to a crawl, even the mouse pointer becomes slugish. Transferring files is impossible. I have tried a different usb port and cable but that has made no difference. Any ideas on what the problem is?

---

### Post by Tamlynmac on 2012-05-21
This was actually reported [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624510") as a bug. The fix was to upgrade your kernel. I'm using 2.6.32-41-generic and have had zero issues with transfer (read/write) speeds since installing that kernel.

What kernel version are you using? You can check it real quick by opening: "system/administration/system monitor/system tab". I'd try updating prior to just installing the kernel. The update should have the newest kernel available that has been approved for release.

Good Luck & hope this helps

---

### Post by dcstar on 2012-05-22
> **todaymueller said:**
> I am currently running Lucid Lynx and have recently found that when I switch on my external hard drive my computer slows to a crawl, even the mouse pointer becomes slugish. Transferring files is impossible. I have tried a different usb port and cable but that has made no difference. Any ideas on what the problem is?

If the drive/enclosure has gone faulty it may be flooding the USB port with rubbish which will kill your system as it tries to service this bad data.

---

### Post by todaymueller on 2012-05-26
Thanks for the replies guys, I will have to test the external drive on another computer to see if that is the problem. :p

---

