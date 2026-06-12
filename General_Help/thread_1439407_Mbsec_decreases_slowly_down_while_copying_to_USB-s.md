---
title: "Mb/sec decreases slowly down while copying to USB-stick..."
date: 2010-03-26
forum: General Help
---

### Post by pingu1 on 2010-03-26
I have a "DataTraveller" 16 GB - that gives me slower and slower speeds on copying files to it. It starts with 8-9 Mb/sec, and goes down all the time, until it's down to kb/sec...

Help....

---

### Post by pingu1 on 2010-03-26
Anybody experienced this before?

---

### Post by cascade9 on 2010-03-26
Not as badly as that, but UI've had slowdowns with USB sticks. Mainly when I'm trying to totally fill them up.

---

### Post by pingu1 on 2010-03-26
I now have 2 Mb/sec - which started at 7 mb/sec.... I don't understand why... but I'm a NooB...

---

### Post by philinux on 2010-03-26
Yep same here. Copying from usb to HD is fine. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762)

It's an old bug but it's still not fixed.

Please feel free to click on the "affects me" link.

---

### Post by AndyDeGroo on 2010-03-26
That may not be a problem with USB stick or drive, but a bug in way nautilus calculates the average transfer speed.
For instance: if transfer speed at beginning for short moment is reported as 10MB/s or more, then if later speed falls to 2MB/s average would slowly decrease.
that is basically common problem with common  calculation algorithms of average transfer speed in any software.

---

### Post by philinux on 2010-03-26
> **AndyDeGroo said:**
> That may not be a problem with USB stick or drive, but a bug in way nautilus calculates the average transfer speed.
For instance: if transfer speed at beginning for short moment is reported as 10MB/s or more, then if later speed falls to 2MB/s average would slowly decrease.
that is basically common problem with common  calculation algorithms of average transfer speed in any software.

It really does slow down a lot. It's obvious from the time it takes.

---

### Post by pingu1 on 2010-03-26
Yes I would agree - it's seriously slow... but then again - I'm patient.
I've used USB-sticks on my computer at home, even an external 1 TB without having this very problem.
This happened on another computer. Weird that I do not have this problem at home... ...

Hope they fix it...

---

### Post by AndyDeGroo on 2010-03-26
> **philinux said:**
> It really does slow down a lot. It's obvious from the time it takes.
Ok, I checked that bug report and I take my word back. That actually is a bug in kernel.

Before posting to that bug report please read comment #218 : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762/comments/218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197762/comments/218)

For those who have this problem and want to file bug report, I'd suggest reading following: [https://help.ubuntu.com/community/DiskPerformance](https://help.ubuntu.com/community/DiskPerformance)

---

### Post by Tricast on 2010-04-04
To have the Transmission torrent client running makes file transfers to usb a pain in the *** for me. Starts out fast but decreases in speed and eventually halts completely. If i close it and try usb transfer again speed is normal.  I am using 2.6.31-20 kernel. Tested on Sandisc Cruzer micro 4 GB.

---

