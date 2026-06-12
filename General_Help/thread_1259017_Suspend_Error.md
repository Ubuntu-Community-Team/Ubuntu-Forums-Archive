---
title: "Suspend Error"
date: 2009-09-05
forum: General Help
---

### Post by kyle2595 on 2009-09-05
Hi, I am running Ubuntu 8.04 (I think) and whenever the computer tries to wake up from suspend mode, all I get is a black screen that I can't do anything with. The power light is solid (instead of flashing while in suspend mode) so the computer knows that it should wake up, but I get a blank screen.  Is there any way that I can fix it?  Thanks!

---

### Post by baltadt on 2009-09-05
As far as I know you cannot use suspend or hibernate yet.  It's not a reconizable function.

---

### Post by jobst on 2009-09-06
> **kyle2595 said:**
> Hi, I am running Ubuntu 8.04 (I think) and whenever the computer tries to wake up from suspend mode, all I get is a black screen that I can't do anything with. The power light is solid (instead of flashing while in suspend mode) so the computer knows that it should wake up, but I get a blank screen.  Is there any way that I can fix it?  Thanks!

Number of things to consider:


[LIST=1]
[*]check the size of your swap partition, it must match at least the size of your RAM
[*]your video driver must be able to suspend/hibernate, if it does not on reboot a black screen is what you get
[*]make sure your video driver is not a standard one, for example if you have a NVIDIA card install the nvidia driver
[/LIST]

jobst

---

### Post by baltadt on 2009-09-15
I just read in linux pro mag that not all laptops are able to use this function with Ubuntu.

---

