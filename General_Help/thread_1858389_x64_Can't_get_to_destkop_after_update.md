---
title: "x64 Can't get to destkop after update"
date: 2011-10-12
forum: General Help
---

### Post by pjar on 2011-10-12
Hi, I'm beginner user of Ubuntu 10.10 64bit
I'm (un)lucky owner of dual graphics - integrated Intel plus nVidia 540m being under command of nVidia Optimus technology.
I have Toshiba Satellite p755.

After today's update I can't get into desktop. Instead of that during boot I have to wait couple more seconds than usual to see only the login screen in desktop mode in low resolution (I don't use that - normally it should just go without login). I can't get past this screen - it gets back after every password input.

Don't really know where to look at.

Now I'm forced to use recovery mode in grub and going through failsafe graphic mode to use my ubuntu.

I don't know how to be more specific to describe the problem. Please advise me how to get anything you need to help with that.

Thanks

---

### Post by mikejonesey on 2011-10-12
remove and purge the updates via tty1... /var/log/dpkg.log

---

### Post by pjar on 2011-10-12
> **mikejonesey said:**
> remove and purge the updates via tty1... /var/log/dpkg.log

well, thanks for that tip but as a noob I know how to remove purge a single package but I'm assuming that you meant whole update.

Is there any way to do it in one command or I have to remove purge everything from dpkg.log that have appeared on the specific date?


The second thing is that my problem appears not only when I try to use the very new kernel but it did affect the previous one. I can't get desktop over there as well. I don't get it why.

---

### Post by pjar on 2011-10-13
Bump. 
No other ideas?? I'm still stuck, being forced to use recovery mode to use my Ubuntu :(

---

### Post by pjar on 2011-10-18
OK I assume that's somehow new problem and is not recognized yet.

As I have to boot through recovery mode to get failsafeX and run Ubuntu with basic settings (which works fine for me) is there any way to get to that mode straight away without going to recovery mode?

Cheers

---

### Post by pjar on 2011-10-26
Bump

To be honest I thought it's easy thing for experienced ubuntu users. 

Still looking for any advice.

cheers

---

### Post by dino99 on 2011-10-26
following the previous howto: "remove and purge the updates via tty1... /var/log/dpkg.log"

into a terminal:

sudo rm /var/log/dpkg.log

then update again

---

### Post by pjar on 2011-10-26
> **dino99 said:**
> following the previous howto: "remove and purge the updates via tty1... /var/log/dpkg.log"

into a terminal:

sudo rm /var/log/dpkg.log

then update again

Thanks for quick reply.
After removing dpkg.log, I wanted to update (through Update Manager) but there are no updates to install. What is other option to do it?

---

