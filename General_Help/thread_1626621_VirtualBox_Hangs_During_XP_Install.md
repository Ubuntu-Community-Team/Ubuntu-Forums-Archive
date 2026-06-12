---
title: "VirtualBox Hangs During XP Install"
date: 2010-11-20
forum: General Help
---

### Post by RikkiUW on 2010-11-20
Hey guys,

I'm trying to create a Windows XP VM using VirtuallBox, and creating/formatting the disk goes OK, but when it's actually running setup it hangs only a few minutes in. I'm using VirtuallBox 3.1.10 on Ubuntu 10.04. Does anyone have any suggestions? I've Googled the problem, but haven't found anything that works.

Thanks,
--Rikki

---

### Post by papibe on 2010-11-21
What kind of license is your Windows software?  I believe regular OEM versions (that ones that come with your PC/Laptop) won't work because they can only be installed on your original hardware.

Nevertheless, if that's the case, it may be valuable ;) to you to go to the VirtualBox forums.

Regards.

---

### Post by RikkiUW on 2010-11-22
It's not OEM, I bought the full version. Used to have it on my desktop, then upgraded to win7. My desktop is out of commsion right now though, which is why I'm trying to set up a virtual machine.

I'll check out the VirtualBox forums.

Thanks,
--Rikki

---

### Post by RikkiUW on 2010-11-23
Got it solved. I had used nlite to customize the image, and apparently VirtualBox didn't like that. I used a fresh image and it's installed and working perfectly.

Thanks!
--Rikki

---

