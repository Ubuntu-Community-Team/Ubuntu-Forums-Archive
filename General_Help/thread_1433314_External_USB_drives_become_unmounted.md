---
title: "External USB drives become unmounted"
date: 2010-03-18
forum: General Help
---

### Post by gatordude on 2010-03-18
Hello,

I have recently put a new system together that I installed 9.10 on and I am having an issue where my external USB drives (both HD and flash drives) become unmounted.

The first time I installed one  external drive I got this 
```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

I have not got that again. I checked the drives on my windows machine and there doesnt appear to be a problem.

Now on initial power up my external drives are mounted and then after a few minutes they unmount with no explanation.

Any ideas?

---

### Post by gatordude on 2010-03-20
OK, just wanted to add a few things.
The two external drives I need to have connected worked fine and work fine with 9.04 (9.04 is on my laptop and they come up just fine when I connect my USB hub to it).
These are my data drives and they have all of the files one collects over the years.

I have scanned them with windows (using the laptop) (AVG and the one that comes with Google desktop) and there are no infections on them. I have moved all executables into folders so there should not be any conflicts with a program trying to run when the system boots up. I have also scanned with clam on the laptop (9.04) and it does not detect anything.

Every time when I boot (on my new quad system) 9.10 both drives are mounted, then poof after a few minutes they are gone. I can either be poking around in them or  the system can be idle. No difference.

Any advice?

---

### Post by gatordude on 2010-03-22
Ok,
Well after lots of reading and searching on my own it seems that there are lots of people having external USB drive issues.

I checked my BIOS to see where my USB settings were and I changed my USB Reset Delay from 20 sec's to 30 sec's.

Also, when I checked the connecting power plugs I noticed that both drives power modules were plugged into the same power strip in a "transformer coupled" outlet. I read somewhere that could cause fluctuations in devices that are connected to them.

Anyway, short story long, my drives have been holding and not "unmounting".

Hope this helps

---

