---
title: "kernel lock with usb mass storage device"
date: 2010-02-02
forum: General Help
---

### Post by thoromyr on 2010-02-02
I just discovered that inserting any USB drive causes an immediate hang of the system. The keyboard caps lock and scroll lock lights blink. Only recourse is to power cycle the system. This is after installing Kubuntu 9.10 in January, I don't believe I had occasion to insert a USB drive until tonight. 100% reliable. No entries in logs, presumably because it hangs the kernel when it happens. The /var/log/kern.log file has been corrupted due to file system damage (1+ sectors of some other file inserted into chain) and probably other files as well.

I've not had occasion to report other bugs, but I've found no way to report anything other than application bugs. I tried using "ubuntu-bug kernel" which helpfully said there was no such application as 'kernel' and has been busy "collecting problem information" for the last half hour or more. Somehow I don't think its ever going to finish.

The crash only happens when booted into Kubuntu 9.10. If I boot off of 9.04 then USB drives work fine. Both USB drives I've tried reliably produce the crash. One is a random cheap USB thumb drive (imprinted "Cisco"), the other is a 16GB Corsair Voyager.

Any thoughts on what I could do to provide information helpful to debugging? Due to the file system corruption I'll be reinstalling, but that won't be immediately. At this point I don't think it'll be Kubuntu 9.10...

---

### Post by infecticide on 2010-02-06
I have exactly the same issue, it started a long while ago and then I reinstalled from scratch and it magically solved itself for about 6 months.

Now its happening again.   I have an "All-in-one" memory card reader as well as a 32GB run of the mill USB flash drive.

Both of them worked until last weekend.

Both of them cause the same issue, I don't even have to have any cards plugged into the reader to cause the problem.

My font isn't small enough in the console to see the beginning of the kernel dump when it happens so that hasn't helped any thus far.

Hopefully somebody knows whats up.

---

### Post by infecticide on 2010-02-10
I tried to see if this is Kernel, Hardware or Software related and it appears to be software related.   I booted in Recovery Mode and I can plug whatever I want into the machine and it sees the usb device fine without crashing.

Now its a process of elimination to figure out which software is causing it.

I have ruled out BOINC and Xorg already.   It also appears that in Recovery Mode the kernel modules are all loaded so it would not appear to be one of them at fault, ie Nvidia driver.

---

