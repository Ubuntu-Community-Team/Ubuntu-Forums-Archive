---
title: "Do I need to purge my Nvidia Drivers"
date: 2011-07-25
forum: General Help
---

### Post by zero244 on 2011-07-25
Hey guys I installed the 275 Nvidia drivers a while back, they seem to working alright.
I compiled these drivers from source to my current kernel.

Do I need to uninstall and purge the drivers before I update my kernel again.

If I update the kernel without doing anything will it break my video.

Thanks in advance.

---

### Post by dabl on 2011-07-25
> **zero244 said:**
> 
If I update the kernel without doing anything will it break my video.



Yes.

Why did you not use the Ubuntu utility to install the driver? The main advantage of it is to avoid the problem that you are facing.

If you will download the current Nvidia driver, then upgrade your kernel, then boot the new kernel in recovery mode, you can install the new driver same as you did the one you have now. From the command line.

---

### Post by zero244 on 2011-07-25
Thats what I thought the answer would be.

I compiled the drivers because I was getting freeze ups using the repo drivers.
As it turned out it was a bad motherboard that was causing the freeze ups, but by the time I figured that out I had already installed  the compiled 275 drivers.

Oh by the way the driver utility did not detect any drivers for my nvidia 6200 card.
So I manually installed the 173 drivers in the repos.

Should I uninstall the compiled drivers and go back to the repo drivers to avoid this coming up again.

Thanks for the response.

---

### Post by wildmanne39 on 2011-07-26
Hi, the 173 driver works great with my 6150 card. Since you compiled one yourself you will need to remove it to use the 173 or you will have conflicts.

---

### Post by zero244 on 2011-07-26
> **wildmanne39 said:**
> Hi, the 173 driver works great with my 6150 card. Since you compiled one yourself you will need to remove it to use the 173 or you will have conflicts.

I very painlessly --uninstalled the compiled drivers, booted back into failsafe mode and installed the 173 drivers and everything is working great.
These drivers seem to be better than the 275 compiled drivers.
I thought for sure once I uninstalled the drivers I would be left to editing the xorg or reinstalling Ubuntu.
Very impressive how well Linux can work.

Just wondering if I update the kernel with the 173 repo drivers will the kernel update break the drivers.

---

### Post by wojox on 2011-07-26
> **zero244 said:**
> 
Just wondering if I update the kernel with the 173 repo drivers will the kernel update break the drivers.

I've never had the repo drivers break on a kernel upgrade/update.

---

### Post by wildmanne39 on 2011-07-26
Hi, you should be ok, I am glad it worked,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

