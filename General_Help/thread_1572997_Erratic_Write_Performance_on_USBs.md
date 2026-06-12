---
title: "Erratic Write Performance on USBs"
date: 2010-09-12
forum: General Help
---

### Post by rdnetto on 2010-09-12
Hi,
I've been having some problems copying files to USBs. If I'm copying a large (100MB+) amount of data, at random points the transfer will just stop for 30+ seconds before continuing. Sometimes it doesn't start up again at all. Consequently, the write speed drops to less than 1MB/sec, sometimes as low as 100 KB/sec. I do not have these problems on Windows 7, where I achieve speeds of ~16 MB/sec easily. I have had the same results with several USBs (2-32 GB) on several file systems (fat32, ext2) with several different computers running fully patched versions of Ubuntu 10.04, which suggests the problem is related to the way the OS accesses the hardware.
If you have any ideas on how I can fix this, I would appreciate them.

---

### Post by timgood on 2010-09-12
I would also like to see this issue addressed - and for me the killer is getting to 99% of the file transfer and then having to wait for 5 minutes for the process to complete and safe removal allowed. I find it impossible to get USB 2 speeds on almost any data transfer to and from USB devices - with speed dropping as you say < 1MB sec. Any ideas?

---

### Post by timgood on 2010-09-21
Bump! Any ideas on this?

---

### Post by timgood on 2010-09-22
After some experimentation I can confirm that this only happens if you copy using Nautilus. If you use the command line, data transfer rates remain constant and the process is much quicker. Bug in Nautilus?

---

### Post by rdnetto on 2010-09-23
That's odd, I still have the same problem in the terminal. The speed dropped an order of magnitude in under a minute. (Watched the speed by using 'scp `whoami`@localhost:/path/file /media/MyUSB/').
It's possible we have different problems - looking at Launchpad seems to indicate that there are heaps of different bugs with these symptoms, and no one wants to fix them since it could be any number of things, right down to the kernel.

---

### Post by teh_dude on 2010-10-21
I got the same problem since I did a clean install of Ubuntu 10.10 Maverick.

Very slow usb drive speed. When I copy a 700 MB file using nautilus, a copy dialog shows up, saying 130.1 MB has already been copied (impossible), no indication of copy speed.
Then, after 30 seconds or so, the 130.1 increases slowly to, let's say 145 MB. Now the copy dialog says the transfer is like 3 MB/s. Then the copying 'pauses' again. Then, after another 30 seconds, it resumes, and so on. It took me **2 hours** to copy the entire file. At the end the transfer speed dropped all the way down to 100 KB/s.

Also trying to copy from usb to hard disk pauses at unpredictable moments + very low performance.

I have kernel version 2.6.35. This might be a kernel problem since copying with shell command cp also goes wrong. Something with the usb drivers or whathever, I don't know much about this.

[LEFT]Hope the problem will be solved in 2.6.36...
[/LEFT]

---

### Post by rdnetto on 2010-10-21
I've found a workaround:
```
dd if=/myfile of=/media/MyUSB/myfile bs=100M
```
If you use dd with a very large block size then this problem doesn't occur. It seems like lots of individual writes slow it down, but a few large ones don't. Could be a multi-threading issue. 
Unfortunately I have no where near the expertise needed to actually fix this, so I hope someone who does comes across this.

---

