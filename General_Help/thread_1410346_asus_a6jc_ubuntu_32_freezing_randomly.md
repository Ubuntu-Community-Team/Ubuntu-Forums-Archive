---
title: "asus a6jc ubuntu 32 freezing randomly"
date: 2010-02-18
forum: General Help
---

### Post by ripper88 on 2010-02-18
I have a problem after the installation of ubuntu 9.10 on my laptop a6jc (32bit). It randomly freeze for some seconds even if the cpu isn't at 100% working.
I check the hard disk status and attached you can find the log.
During the freeze the shell show the following text

[24968.000087] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[24968.000191]               cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[24968.000194]               cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[24968.000196]               res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[24968.000405] ata1.00: status { DRDY }

Could you help me please??? What can I do to find what the problem is??

Thank you!

---

### Post by jpl888 on 2010-02-18
Looks like either a hard-drive, hard-drive controller or motherboard problem.

Would it be possible for you to try the hard drive in another machine to isolate the problem?

---

### Post by ripper88 on 2010-02-22
No, I have no other machine to test it and I'm not so able with the hardware of laptops...any other possibility?? Windows works well, I don't think that would be an hardware problem...

---

### Post by mcduck on 2010-02-22
that definitely looks like failing hardware.. Even more so with all the errors in the SMART report.

It sure isn't any type of compatibility problem, I have Asus A6Ja laptop which is pretty much exactly the same machine, only with Ati graphics card instead of the nVidia one that A6Jc has. 

The fact that you don't have problems in Windows is not that strange, Linux tends to stop working immediatelly when it encounters hardware problems, while Windows keeps on running without telling you anything, but at the same time slowly corrupting your data.. So on a broken system Linux will be the fist one to stop working. Still, if you want to, just run a SMART check in Windows as well (not that it should make any difference since the SMART data coems from the hard drive itself and whatever OS you are running shouldn't make affect that).

---

### Post by jpl888 on 2010-02-22
Yes and the reason I say it is probably hardware is that I had a HP DX2200 that the motherboard went strange on. Even when installing a new SATA controller I got similar errors and the machine was sloooooowwwwww. I think it was the IOAPIC that had gone foobar anyway a new mb sorted it out, though I'm not necessarily saying that is definitely your problem.

---

### Post by ripper88 on 2010-02-22
ok, thank you, so I couldn't do anything except to try a new hardware, but I think that the cheapest solution would be to buy a new laptop :popcorn:

---

### Post by jpl888 on 2010-02-22
Yes well I suppose your options for changing hardware with a laptop are limited. You would have to be fairly hardware savvy to change the motherboard and then it could still turn out to be the hard drive that's at fault. So for restful nights a new laptop might be the easiest solution (unless of course you still have warranty).

---

### Post by mcduck on 2010-02-22
> **ripper88 said:**
> ok, thank you, so I couldn't do anything except to try a new hardware, but I think that the cheapest solution would be to buy a new laptop :popcorn:

if its just the hard drive that's failing (like the SMART errors would suggest) then you don't need a new laptop, just a new hard drive. And replacing the drive on Asus A6 laptops is really, really easy to do. :)

edit: you might want Hitachi's own bootable drive check tool: [http://www.hitachigst.com/hdd/support/download.htm#DFT]("http://www.hitachigst.com/hdd/support/download.htm#DFT"). That would tell you pretty reliably if the problem is in the hard drive or somewhere else...

---

### Post by jpl888 on 2010-02-22
Yes I approached that from the wrong angle not taking into account the smart errors, hard drives are so cheap it would definitely be worth trying to change the hard drive first.

---

### Post by mcduck on 2010-02-22
> **jpl888 said:**
> Yes I approached that from the wrong angle not taking into account the smart errors, hard drives are so cheap it would definitely be worth trying to change the hard drive first.

...not to mention that the default hard drive is pretty small and crappy anyway, I've actually been planning replacing it with some nice silent 500GB drive with reasonable cache size myself. :)

---

### Post by ripper88 on 2010-02-22
If the problem is the hard drive yes I can easly change it, because I have done that already once. Thank you for the suggest and I hope that the problem wouldn't have anything to do with the motherboard!! :D:D

---

### Post by mcduck on 2010-02-22
> **ripper88 said:**
> If the problem is the hard drive yes I can easly change it, because I have done that already once. Thank you for the suggest and I hope that the problem wouldn't have anything to do with the motherboard!! :D:D

Good luck with that, as I assume your laptop's guarantee is already over so replacing the motherboard would be pretty much out of the question.. 

(but try your hard drive manufacturer's test software first before you buy a new drive, pretty much every manufacturer has a bootable SMART check tool for their drives available for free.. )

---

### Post by ripper88 on 2010-02-23
I did the test of the hard disk provided by hitachi with no bad results :( and so where is the problem? Should I try a new hard drive anyway?

---

### Post by jpl888 on 2010-02-23
Well you said you wanted to put a bigger hard drive in anyway so no harm if you do change it.

---

### Post by mcduck on 2010-02-23
> **ripper88 said:**
> I did the test of the hard disk provided by hitachi with no bad results :( and so where is the problem? Should I try a new hard drive anyway?

Sorry to tell you, but in that case it sounds a lot more like the problem is with the motherboard..

---

### Post by ripper88 on 2010-02-25
I tried to find out a program to test my motherboard and all of its components but I had no results. Could you suggest one to me? 
Thank you!

---

### Post by ripper88 on 2010-03-04
- SOLUTION -
With an empty cd into the cd-reader the computer doesn't freeze anymore...
It is such a bug of ubuntu I think

---

