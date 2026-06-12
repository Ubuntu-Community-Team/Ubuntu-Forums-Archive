---
title: "System constantly crashing"
date: 2009-09-15
forum: General Help
---

### Post by umanzor on 2009-09-15
Hello everyone, 

Long time Ubuntu user here. I'm having a problem that I cannot find the cause. My system has been randomly crashing for a while now. It began a few months ago and at first I thought it was caused due to failing hard drive.

Around a month ago my system crashed and I wasn't able to boot back in. I got a few I/O errors and was dropped into the initramfs every time. I was at the time working on some projects so I had no time to reinstall Ubuntu and went back to my Windows Seven installation I had in another hard drive. (btw Windows Seven is simply the best OS MS has ever released, I loved it). 

Project over, I had some free time and I was missing messing around with Linux (plus I needed a simple Scheme interpreter) so I decided to reinstall Ubuntu. Still having issues.

1. System seems to crash whenever their is heavy disk activity. I am unable to reproduce this though.
2. I ran memtest today while I was at work. It ran for some good 12 hours with no issues. I guess we can rule out memory with that. Also, my system was running at 53'C (highest temp I've ever seen) and it was running fine as well. It didn't crash until I attempted to do an update. I was able to do the update fine after rebooting.
3. It also crashed while I was converting some videos. It happened this way twice.

I have a few logs from the other day that I found the PC completely locked up after I left to work. There is a whole of some hours in the log, but there is definitely nothing useful in there, or I am not looking at the right place.


hey guys, I really need help on this one, any extra information I can provide?

---

### Post by P4man on 2009-09-16
Coud be an ACPI/Bios problem.
You could try booting the kernel with one of the following parameters:

noapic
nolapic
acpi=off

(the last one turning off acpi support, which also has some side effects, or may not even boot).

To try these settings for just 1 boot, have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by cumanzor on 2009-09-19
> **P4man said:**
> Coud be an ACPI/Bios problem.
You could try booting the kernel with one of the following parameters:

noapic
nolapic
acpi=off

(the last one turning off acpi support, which also has some side effects, or may not even boot).

To try these settings for just 1 boot, have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

Thanks. First I tried setting my FSB speed back to defaults (I was overclocking a little) to see if this would solve the problem. It didn't work, system still crashes and I'm almost completely sure it happens when I try to move/copy files, not always though.

I've set those three options, and I'll let you know how it works out. I added them to the kernel line during boot, is there any way to confirm they actually worked? Or would the bootloader send a message regarding incorrect boot options?

---

### Post by P4man on 2009-09-20
> **cumanzor said:**
> 
I've set those three options, and I'll let you know how it works out. I added them to the kernel line during boot, is there any way to confirm they actually worked? Or would the bootloader send a message regarding incorrect boot options?

There is no feedback, and Im not sure how to check at least the first 2. I suppose dmesg will print it somewhere if you know where to look, but those settings do work.

---

### Post by pcjunkie on 2009-09-20
Other reasons,,

RAM do a ram test (have time for coffee and lunch)
The Chip is failing
The BIOS is corrupt. flash it!
Corrupt / failing drive.
Disk check on boot does not and should not do a thorough check as this can cause errors on a mounted drive. Pop in the Ubuntu disk and run disk check from there. You will soon find out. If it cleans errors and the thing still plays up (loading a default profile and weird stuff like that) copy the install to a fresh drive and bin the one you are using.

---

