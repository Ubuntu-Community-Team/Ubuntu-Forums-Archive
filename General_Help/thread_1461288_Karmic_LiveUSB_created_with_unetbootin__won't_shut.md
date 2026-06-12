---
title: "Karmic LiveUSB created with unetbootin  won't shutdown?"
date: 2010-04-24
forum: General Help
---

### Post by carn1x on 2010-04-24
I've been using a LiveUSB I created using unetbootin from Windows Vista/7.

Whenever I use it to install Ubuntu (done it a few times now) or as a LiveUSB to try and rescue my installation, it never shuts down or reboots. It just starts the cycle then hangs on the white Ubuntu logo. As it never gets past this, I'm forced to hard power off, and I'm concerned this could be damaging my mounted system drives? I've decided I should be unmounting before I try and shut it down now, is there a proper way to do this, and can I fix the LiveUSB itself?

Thanks

---

### Post by wilee-nilee on 2010-04-24
Reload the usb and use this links information to avoid hard shutdowns.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

Notice that the b at the end=reboot if you use a o instead=off. so hold down alt and sysrq keys and slowly hit reisub or reisuo

When you say rescue your installation that is confusing, what type of install is it, is it a wubi install or a dual boot.

---

### Post by carn1x on 2010-04-24
Been having problems getting Ubuntu to boot, so I've been messing with the LiveUSB in order to either save the installation or backup files.

Thanks for the info I'll check it out :)

---

### Post by wilee-nilee on 2010-04-24
> **carn1x said:**
> Been having problems getting Ubuntu to boot, so I've been messing with the LiveUSB in order to either save the installation or backup files.

Thanks for the info I'll check it out :)

Have you posted the problems, theoretically you should  not be having any problems with booting. I suspect this is a wubi install eh?

---

### Post by carn1x on 2010-04-24
No I installed from the LiveUSB, the problems started just over 24 hours ago. I posted the problems on the forums here, but I didn't get any response for 24hours so I decided to reinstall. As soon as I come back online from the reinstall, I have a reply!

In case you are interested:

[http://ubuntuforums.org/showthread.php?t=1460783](http://ubuntuforums.org/showthread.php?t=1460783)

Although in regards to that issue, I can no longer provide feedback! :)

---

### Post by wilee-nilee on 2010-04-24
So here are two links that may of help in the future the first is how to reinstall grub2 which Karmic is running if updated, step 11 is where you want to look. The second is a boot script that will tell all so to speak of whats going on and the members who are very good at reading this and suggesting fixes will want to see it.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Posting the boot script will bring help faster, it cuts to the chase. Best of luck I had to reimage my computer 3 times in the first 6 months of starting with Ubuntu 3 years ago. User error sucks at times.

---

