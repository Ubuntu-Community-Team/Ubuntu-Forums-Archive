---
title: "how to disable nouveau kernel driver?"
date: 2011-06-23
forum: General Help
---

### Post by ryadav on 2011-06-23
i am unable to install the nvidia driver on kubuntu11.04, i am told i need to disable the nouveau kernel driver. after searching i have not found an answer.

what do i need to do? thanks!

---

### Post by pqwoerituytrueiwoq on 2011-06-23
```
sudo echo nouveau >> /etc/modprobe.d/blacklist.conf
```
on next boot it will be disabled
you should boot to recovery mode and drop to  normal user tty to install the nvidia driver
[http://ubuntuforums.org/showthread.php?t=1682799](http://ubuntuforums.org/showthread.php?t=1682799)

---

### Post by ryadav on 2011-06-23
i already added 'blacklist nouveau' to this file, did a reboot, but i am still getting this error

---

### Post by wildmanne39 on 2011-06-23
> **ryadav said:**
> i already added 'blacklist nouveau' to this file, did a reboot, but i am still getting this errorHi, what error, you did not list an error message.

---

### Post by ryadav on 2011-06-24
Hi the error I am getting is from the nvidia driver installer, it will not install because the nouveau kernel driver is still running. Trying to blacklist nouveau as was suggested does not help. The nouveau driver still seems to be getting loaded. I want to know how to disable it from getting loaded.

---

### Post by wildmanne39 on 2011-06-24
> **ryadav said:**
> Hi the error I am getting is from the nvidia driver installer, it will not install because the nouveau kernel driver is still running. Trying to blacklist nouveau as was suggested does not help. The nouveau driver still seems to be getting loaded. I want to know how to disable it from getting loaded.
Hi, go into synaptic or your package manager since I am not sure synaptic is installed by default in kubuntu 11.04 and type in the name of the driver then right click on it and check to remove completely.

---

### Post by 3rdalbum on 2011-06-24
> **wildmanne39 said:**
> Hi, go into synaptic or your package manager since I am not sure synaptic is installed by default in kubuntu 11.04 and type in the name of the driver then right click on it and check to remove completely.

Err... no, don't even try that. Very bad idea, that basically causes the removal of all your programs.

I think you need to blacklist fbdev too; not entirely sure to be honest.

If you install the Nvidia proprietary driver from the repositories, you won't need to modify any settings at all. Have you tried the version of the Nvidia driver from the repositories? (you could install the "jockey-gtk" package if you want Ubuntu's Additional Drivers program to help you).

If your graphics card is too new for the repository version of the driver, then you could look for a PPA which should also not require Nouveau to be disabled.

---

### Post by ryadav on 2011-06-24
Oh Thanks I installed the nvidia driver from the repository and that worked, I now got both my dual monitor working fine. fyi, blacklisting fbdev did not help.

also I just did a "lsmod | grep nouveau" after i installed the nvidia driver /w a reboot and nouveau is gone, so now I can build the driver for my nvidia chipset if I need to!

[update] I went ahead and installed the latest nvidia from source. As an FYI you must uninstall the old nvidia that was installed from the repository using the software package manager like i did, otherwise x will fail to start as I found out.

---

### Post by wildmanne39 on 2011-06-24
> **ryadav said:**
> Oh Thanks I installed the nvidia driver from the repository and that worked, I now got both my dual monitor working fine. fyi, blacklisting fbdev did not help.

also I just did a "lsmod | grep nouveau" after i installed the nvidia driver /w a reboot and nouveau is gone, so now I can build the driver for my nvidia chipset if I need to!

[update] I went ahead and installed the latest nvidia from source. As an FYI you must uninstall the old nvidia that was installed from the repository using the software package manager like i did, otherwise x will fail to start as I found out.Hi, glad you got it working,
would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

