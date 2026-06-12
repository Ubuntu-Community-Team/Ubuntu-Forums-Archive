---
title: "Removing windows from grub"
date: 2010-10-11
forum: General Help
---

### Post by ronyjoe on 2010-10-11
Hi,
   I had windows 7 installed in my 4th drive and windows vista as my boot drive. I formatted my windows 7 drive using vista and installed ubuntu 10.04 in its place. But still, when i update grub it shows windows 7 as one of the operating systems and my vista OS has been renamed as Windows 7. Please help. How can I remove windows 7 from the list, while i update grub.

---

### Post by mike555 on 2010-10-11
you could install " Grub Customizer " ......
[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)


of course be careful with it , don't uncheck your main os.

---

### Post by Mark Phelps on 2010-10-11
> **ronyjoe said:**
> Hi,
   I had windows 7 installed in my 4th drive and windows vista as my boot drive. I formatted my windows 7 drive using vista and installed ubuntu 10.04 in its place. But still, when i update grub it shows windows 7 as one of the operating systems and my vista OS has been renamed as Windows 7. 
That's because Win7 and Vista use the same Windows loader program, so GRUB sees them as the same.
> Please help. How can I remove windows 7 from the list, while i update grub.
There is no easy way to remove GRUB entries anymore as the ne GRUB automatically generates them. If you start messing around with the new boot scripts, you could render your machine unbootable.

---

### Post by ronyjoe on 2010-10-11
I get that, but is there any way to use the windows bootloader in place of grub and chain-load ubuntu using windows bootloader.

---

