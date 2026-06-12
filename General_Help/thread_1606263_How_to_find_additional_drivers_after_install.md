---
title: "How to find additional drivers after install"
date: 2010-10-26
forum: General Help
---

### Post by geovino on 2010-10-26
Normally when running the live CD or after the install, Ubuntu will bring an icon to install additional drivers, usually video and wireless. I install 10.10 64bit on a Lenovo laptop and during the live session the icon came up and I was able to download the broadcom driver for wifi and ATI video. since they worked I installed Ubuntu side by side with Windows 7. After the install I was able to go to Win7 or Ubuntu, but when I went into Ubuntu for the first time the icon for additional drivers didn't show up. Why would it not show up? I couldn't find any mention of it in the menus, so I when to a friends who might know, he didn't but connected me to a internet connection to go to synaptic and find those drivers. A few minutes later the icon did finally show up and I was able to get everything loaded and all seems to be working.

Why is it inconsistent in showing up? Is there a way to pull it up if the situation comes up again?

---

### Post by Quackers on 2010-10-26
Unless you have an internet connection (maybe ethernet) the system won't know whether there are any drivers to download, would be my guess.

---

### Post by geovino on 2010-10-26
> **Quackers said:**
> Unless you have an internet connection (maybe ethernet) the system won't know whether there are any drivers to download, would be my guess.

yes, but even before I have the wifi working in live mode, the icon popped up and I was able to install the Broadcom driver that is on the live CD. Once I installed that, I was able to download and install the ATI drivers. So a connection is not needed to bring the icon up on the toolbar.

---

### Post by dcstar on 2010-10-27
> **geovino said:**
> 
..........
After the install I was able to go to Win7 or Ubuntu, but when I went into Ubuntu for the first time the icon for additional drivers didn't show up. Why would it not show up? I couldn't find any mention of it in the menus, so I when to a friends who might know, he didn't but connected me to a internet connection to go to synaptic and find those drivers. A few minutes later the icon did finally show up and I was able to get everything loaded and all seems to be working.

Why is it inconsistent in showing up? Is there a way to pull it up if the situation comes up again?

Ubuntu will not continually waste resources checking for drivers at boot-up, that is scheduled to occur at a later time when the system is (probably) doing less work.

If you need things immediately then that is what **System-Administration-Hardware Drivers** is for, otherwise be patient.

---

### Post by geovino on 2010-10-27
> **dcstar said:**
> Ubuntu will not continually waste resources checking for drivers at boot-up, that is scheduled to occur at a later time when the system is (probably) doing less work.

If you need things immediately then that is what **System-Administration-Hardware Drivers** is for, otherwise be patient.

Thanks for the tip :)

---

### Post by TBABill on 2010-10-27
If you connect to a wired connection right after install it seems to pop up quicker. I do that routinely now because I normally go in sequence after install....1) updates; 2) drivers; 3) additional programs. I don't try to do them all together or do updates and new programs at the same time. Probably overly cautious, but I want my system stable and updated before I do anything to it, then I want all my drivers working properly before adding programs.

---

### Post by coldraven on 2010-10-27
As mentioned above, always be connected to the Internet with a network cable when doing an install.
The live CD will detect my Broadcom wi-fi card but asks to be re-booted to activate it.
Obviously this would just result in the same situation as the live CD is running in memory only and will lose the driver that it had just found.

---

