---
title: "BIOS won't let new drive boot"
date: 2012-06-16
forum: General Help
---

### Post by tomatoe on 2012-06-16
Hello!

Yesterday my hard drive died, so today I took new one and installed ubuntu 12.04 from USB on it. Installation went fine, no errors. When it said that computer must be restarted, I restarted it, but it won't get past BIOS. It shows detected hardware and doesn't go any further. I can't even open BIOS settings. If I remove hdd I can boot from USB.

Any help would be highly appreciated.
Regards

---

### Post by kc1di on 2012-06-16
Hi Sorry your having problems.
I think you problem may be solved by downloading boot repair and running it.

here the page were you can get it.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by tomatoe on 2012-06-16
Hi!
Thanks for answer.
But to fix this issue with boot repair, I need my hdd plugged in right? I can't boot even from USB if the hard drive is plugged in. Also I think it is not grub problem, since it stucks in BIOS.

---

### Post by kc1di on 2012-06-16
> **tomatoe said:**
> Hello!

Yesterday my hard drive died, so today I took new one and installed ubuntu 12.04 from USB on it. Installation went fine, no errors. When it said that computer must be restarted, I restarted it, but it won't get past BIOS. It shows detected hardware and doesn't go any further. I can't even open BIOS settings. If I remove hdd I can boot from USB.

Any help would be highly appreciated.
Regards

Is this a brand new HD?  Give us some more information about your system 
make model etc.

---

### Post by tomatoe on 2012-06-16
No, it is not new, but I'm sure that it is in good condition. 
HD is samsung SP0812N 80 GB 7200 rpm
intel pentium 2.6 gHz CPU
1.5 GB RAM
nVidia geforce 6200 GPU

---

### Post by kc1di on 2012-06-16
is it the only HD in the machine?

---

### Post by tomatoe on 2012-06-16
Yes, it is the only HD.

I plugged the hard drive in other pc and deleted all partitions and all stuff. Now it is booting from USB. I'll install ubuntu again and then will post the results.

---

### Post by tomatoe on 2012-06-16
Hello, again.
After installing ubuntu again, exactly the same problem appears. Any ideas?

---

### Post by tomatoe on 2012-06-16
Maybe this will help. 


It freezes at this position. I pressed del to open setup, but it is "loading"  the setup for about hour already.

---

### Post by kc1di on 2012-06-16
> **tomatoe said:**
> Maybe this will help. 


It freezes at this position. I pressed del to open setup, but it is "loading"  the setup for about hour already.

I Think maybe the problem is the Pentium 4 Process the minimum requirement of 12.04 is  as follows.  So I'm thinking either your Processor or your video card are not quite up to the task

Minimum requirements:
```
Recommended Minimum System Requirements
The Recommended Minimum System Requirements, here, should allow even someone fairly new to installing Ubuntu or Gnu&Linux to easily install a usable system with enough room to be comfortable. A good "rule of thumb" is that machines that could run XP, Vista, Windows 7 or x86 OS X will almost always be a lot faster with Ubuntu even if they are lower-spec than described below. Simply try Ubuntu CD as a LiveCD first to check the hardware works.

Ubuntu Desktop Edition
700 MHz processor (about Intel Celeron or better)
512 MiB RAM (system memory)
5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
VGA capable of 1024x768 screen resolution
Either a CD/DVD drive or a USB port for the installer media
```

That being said Xubuntu or lubuntu may work.

---

### Post by tomatoe on 2012-06-16
That isn't the real problem for sure. As I said, I was running ubuntu 12.04 previously on this pc with no problems, everything worked lika a charm. Only the HD has been changed.
Also my pc completes all the requirements.

---

### Post by tomatoe on 2012-06-16
I tried resetting BIOS didn't help.

Also tried booting from other HD that has 12.04 on it. it booted without any errors. So I think the problem is with this hard drive, but no errors are detected...

---

### Post by kc1di on 2012-06-16
> **tomatoe said:**
> I tried resetting BIOS didn't help.

Also tried booting from other HD that has 12.04 on it. it booted without any errors. So I think the problem is with this hard drive, but no errors are detected...

Sound like they H.D. has a problem for sure. If you can try and replace it.
Sorry it's giving you so much trouble. 

H.D. is only thing really left.
:(

---

### Post by tomatoe on 2012-06-17
hello again...

I deleted the drive and installed ubuntu again with default partition settings and it is working now. I don't know why it didn't work with my custom partitions, because I have done it before and everything worked.

Anyway, I think this is solved, thanks everyone for help!

---

### Post by kc1di on 2012-06-17
> **tomatoe said:**
> hello again...

I deleted the drive and installed ubuntu again with default partition settings and it is working now. I don't know why it didn't work with my custom partitions, because I have done it before and everything worked.

Anyway, I think this is solved, thanks everyone for help!

Glad  you got it going :)
only thing I can think of is you were trying to have more than 4 primary partitions.  Just a guess though.

---

