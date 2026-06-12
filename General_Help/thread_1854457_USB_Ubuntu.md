---
title: "USB Ubuntu"
date: 2011-10-04
forum: General Help
---

### Post by StephanG on 2011-10-04
I just installed Ubuntu onto a USB Flash Drive, with the idea of using it between several computers.
 
Thankfully, it works as expected between my laptop and Core i7 Desktop PC.  However, the installation seems noticeably slower than the Live USB was.  Both have plenty of CPU power and RAM (it doesn't utilize any of the available Swap memory), so the only contributing factor that I can deduce is the bottle-neck that is the USB itself.

So, I was wondering, why is the Live USB so much faster?  

And also, is it possible to add a slight compression onto the flash drive, to remove some of the reading/writing load, and transfering it to memory?  I vaguely recall that NTFS had the ability to compress the entire hard drive.

And lastly, does anyone have any tips for squeezing a few extra drops of performance out of the Flash Drive.  I don't need it to be fast, just reasonably usable for basic tasks like writing documents, watching small videos, etc.

---

### Post by snowpine on 2011-10-04
USB is slower than hard drive bus so you should install to an internal hard drive for best performance.

The reason the Live USB is faster is that it is read-only. Most inexpensive flash drives have abysmal write speeds. The best way to improve performance is to avoid anything that writes to disk.

---

### Post by StephanG on 2011-10-04
> USB is slower than hard drive bus so you should install to an internal hard drive for best performance.


Thanks for the input, but I was aware of that when I started.  The reason for this project, is really more of a "Proof of Concept" for something that I might want to do a bit later.  And also, I think it's interesting and have nothing better to do.

> The reason the Live USB is faster is that it is read-only. Most inexpensive flash drives have abysmal write speeds. The best way to improve performance is to avoid anything that writes to disk. 

Ah,that would be the problem then.  I'm still busy updating the installation.  Hopefully it will be faster after that.

But, it's an interesting problem.   Is there a setting that configures the Live disk as "read only" or is it just that it never needs to read?  If it's a setting and makes a big difference, then I might be tempted to seperate the /home partition and make the / partition read-only...

---

### Post by snowpine on 2011-10-04
I think what you are looking for is called "live USB with persistence." 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by StephanG on 2011-10-04
> I think what you are looking for is called "live USB with persistence."

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Thanks, I'll definitely try that as well.  It's just that the persistence file used by the Live USB, is Ext2, so I thought a proper installation might be faster.  If not by default, then hopefully after some tweaking.

But... If this experiment doesn't yield the desired results, I'll definitely try that next.

---

### Post by snowpine on 2011-10-04
ext2 is a good choice for flash storage. Theoretically the drive will last longer because ext2 is non-journaling and therefore less disk activity.

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

---

### Post by StephanG on 2011-10-04
> ext2 is a good choice for flash storage. Theoretically the drive will last longer because ext2 is non-journaling and therefore less disk activity.

Oh... Thanks.  That's good to know.  I'll set up on my second USB for comparison.

---

