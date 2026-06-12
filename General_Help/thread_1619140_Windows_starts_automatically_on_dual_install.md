---
title: "Windows starts automatically on dual install"
date: 2010-11-11
forum: General Help
---

### Post by edco76 on 2010-11-11
I just reinstalled Ubuntu alongside windows for a dual install. The installation went ok but when Ubuntu said it needed to restart to complete, now my pc just loads windows 7 everytime. It doesnt give me an option of choosing Ubuntu. I know the install worked because when I look at my drive in windows it is the partitioned size.

Any way to manually launch Ubuntu?

---

### Post by Verbeck on 2010-11-11
try holding down the SHIFT key on boot

---

### Post by bonixavier on 2010-11-11
This might help:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

Edit: Google first. What I posted was the FIRST result for &quot;ubuntu grub recovery&quot;

---

### Post by Mark Phelps on 2010-11-11
Holding down the SHIFT key forces the GRUB menu to appear -- presuming that you're initially booting using GRUB through the MBR.  If GRUB is not installed to the MBR you're using to boot, holding down that key will not do anything.

Your case is unusual because, when you install Ubuntu, it generally sets up GRUB so that IT is the default OS, not Windows.

But, when you reinstalled Ubuntu, did you do a Wubi-install (inside Windows), or did you do an install to a separate partition?

If the second, what did you do when prompted to install GRUB?

---

### Post by mug_costanza on 2010-12-26
I am having the same problem with my installation. I installed UNR via a USB stick on my netbook but when I try to boot I do not see GRUB, windows 7 starts automatically and works as it normally does. I also tried holding down SHIFT during boot but to no avail. UNR was installed into a partition on the same drive as Windows. If anyone has any ideas please help! Thanks!

---

### Post by wilee-nilee on 2010-12-26
> **mug_costanza said:**
> I am having the same problem with my installation. I installed UNR via a USB stick on my netbook but when I try to boot I do not see GRUB, windows 7 starts automatically and works as it normally does. I also tried holding down SHIFT during boot but to no avail. UNR was installed into a partition on the same drive as Windows. If anyone has any ideas please help! Thanks!

Your going to want to start your own thread and do this, these threads can get quite convoluted so start your own please.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Thread starter post this script as well.

---

### Post by Quackers on 2010-12-26
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

