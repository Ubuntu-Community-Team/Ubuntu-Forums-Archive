---
title: "CD/DVD burning problems"
date: 2010-05-04
forum: General Help
---

### Post by Kopachris on 2010-05-04
Tried to write the Lucid x86 desktop iso to a CD (SATA "super multi burner" made by LG) with wodim on the command line with
```
$ wodim -v -V ~/Downloads/ubuntu-10.04-desktop-i386.iso
```and found this:
```

write track data: error after 1079296 bytes
wodim: The current problem looks like a buffer underrun.
wodim: It looks like 'driveropts=burnfree' does not work for this drive.
wodim: Please report.
wodim: Make sure that you are root, enable DMA and check your HW/OS set up.

```Needless to say, it didn't work out very well.  The disk mounted fine, but gives I/O errors when I try to access anything.  When I try, dmesg gives me a bunch of these:
```

[1598724.945949] Buffer I/O error on device sr0, logical block 351868
[1598724.945960] attempt to access beyond end of device
[1598724.945966] sr0: rw=0, want=1407476, limit=2116

```Output of [FONT=Courier New]sudo hdparm /dev/sr0[FONT=Verdana]:
```

/dev/sr0:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```Trying to set -d1 returns:
```

/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```I don't want to waste any more CDs.  If anyone has an alternative, please voice it.  I want to get this age-old problem solved ASAP.

And no, I can't write any other CDs or DVDs.  Essentially the same thing happens for everything.  The buffer underrun might be because I'm going from an IDE hard drive to a SATA burner.  If that's the case, is there any way to fix it short of buying a new hard drive?  Picking a slower burn speed doesn't help, either.
[/FONT][/FONT]

---

### Post by kenweill on 2010-05-04
Did you try brasero or k3b?

There's also a probability that your burner is at fault. Probably, there are dust in the lens.

---

### Post by Kopachris on 2010-05-04
> **kenweill said:**
> Did you try brasero or k3b?

There's also a probability that your burner is at fault. Probably, there are dust in the lens.
Yeah, I've tried both brasero and k3b.  They both use wodim as a backend, as far as I know.  And it's not a dusty lens; I cleaned it to be sure.

Perhaps the IDE/SATA difference could be remedied by storing most of the image in the RAM (I have 4GB) and going from RAM to SATA instead of IDE to SATA...  Does someone know of a good Python library for writing to optical drives?

---

### Post by alkach on 2010-05-05
Hi!

> **Kopachris said:**
> Yeah, I've tried both brasero and k3b.  They both use wodim as a backend, as far as I know.  And it's not a dusty lens; I cleaned it to be sure.

...


I've got a similar problem after upgrading to 10.04 from 9.10 on my laptop. Everything was OK before that. In Ubuntu 9.10 Brasero burnt disks correctly.

Does anybody have a clue how to know what/who is responsible for my laptop being unable to burn DVD without reinstalling? Is it Ubuntu 10.04 or the DVD-RW drive?  Reading DVDs is still OK.

---

### Post by anglican on 2010-05-05
> **Kopachris said:**
> Yeah, I've tried both brasero and k3b.  They both use wodim as a backend, as far as I know. 

In my experience, admittedly on different hardware, wodim may be the problem. I replaced it with the original cdrtools that wodim is a fork from and problems all went away. YMMV.

H

---

### Post by alkach on 2010-05-05
> **anglican said:**
> In my experience, admittedly on different hardware, wodim may be the problem. I replaced it with the original cdrtools that wodim is a fork from and problems all went away. YMMV.

H


I also tried building the original CDRTOOLS but with the latest CDRECORD the effect was the same unfortunately. Assuming the DVD-RW drive is OK there maybe certain faulty library or kernel module...

---

### Post by cloud3737 on 2010-05-05
My 10.04 installation was working fine (burning CD's, I mean) until I ran the Update Manager and accepted the updates today. Now I'm having issues with burning, ejecting, and even recognizing CDs.

---

### Post by alkach on 2010-05-06
> **cloud3737 said:**
> My 10.04 installation was working fine (burning CD's, I mean) until I ran the Update Manager and accepted the updates today. Now I'm having issues with burning, ejecting, and even recognizing CDs.

So... may we state a ***bug***?

---

### Post by alkach on 2010-05-06
> **alkach said:**
> So... may we state a ***bug***?

I think we may: [http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)

After upgrading to just released 10.04 I could mount DVDs correctly but when I tried to record Ubuntu 10.04 DVD image with GnomeBaker my DVD drive produced so terrible sounds that I'm afraid it might be destroyed (my pure DVD drive). After today upgrade my laptop could not even recognize DVDs and cannot open the tray. The DVD drive recognized as unknown device (application/octet-stream).

---

### Post by alkach on 2010-05-06
> **alkach said:**
> ... I tried to record Ubuntu 10.04 DVD image with GnomeBaker my DVD drive produced so terrible sounds that I'm afraid it might be destroyed (my pure DVD drive).


Yes. My DVD drive is dead. :( Drive LED even does not blink. Maybe this is just a coincide...

---

### Post by Kopachris on 2010-05-27
Upgraded from 9.10 to 10.04...  Burned just fine except that my hard drive had to remap a bad sector in the middle of the burn.  Put in a new 500 GB SATA, runs just fine.:guitar:

---

### Post by hansum_rahul on 2011-01-17
I am having burning problems too.. on a Maverick Meerkat 10.10

Brasero seems to write only Zeros instead of file contents... Any pointers?

---

