---
title: "Can't install nVidia drivers on Ubuntu 10.10"
date: 2011-01-04
forum: General Help
---

### Post by -Ziggy- on 2011-01-04
I've got Ubuntu 10.10 and a nVidia 8400GS but when I try to install the newest drivers I get the following error:

ERROR: You appear to be running an X server; please exit X before installing.

I have no idea what the error message is telling me nor how to fix it.

Can anybody help me so I can install the drivers, please?

---

### Post by seawolf167 on 2011-01-04
First, make sure you are attempting to install the latest drivers from the [official support site]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Second, if you still get the error message, do the following:

Change to a console

```
[CTRL][ALT][F2]
```

Stop the X server

```
sudo /etc/init.d/gdm stop
```

note: this is the new way

```
sudo service gdm stop
```

Install the drivers now according to their install instructions

Restart the X server

```
sudo /etc/init.d/gdm start
```

or using the new way

```
sudo service gdm start
```

Then you should be good to go

---

### Post by gmargo on 2011-01-04
I was just about to give this PPA a try.  It has the latest nvidia driver.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by -Ziggy- on 2011-01-04
Seawolf, thank you for your help, but when I follow your steps I get another different error:

ERROR: The Nouveau kernel is currently in use by your system. This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.

Does anybody know how to disable it?


Gmargo, are you saying that I get the newest nVidia drivers just for getting that X.org update?

---

### Post by seawolf167 on 2011-01-04
I haven't run into anything like that new error before, but a quick google search gave these two promising results, see if either of the threads can help you out

[http://ubuntuforums.org/showthread.php?t=990978&page=140](http://ubuntuforums.org/showthread.php?t=990978&page=140)
(see the 3rd post on this page for the same error)

[http://www.linuxquestions.org/questions/ubuntu-63/nouveau-kernel-driver-825432/](http://www.linuxquestions.org/questions/ubuntu-63/nouveau-kernel-driver-825432/)

Let us know if either work!

---

### Post by gmargo on 2011-01-04
> **-Ziggy- said:**
> 
Gmargo, are you saying that I get the newest nVidia drivers just for getting that X.org update?

Yup, I just rebooted - I'm now running the latest nVidia driver from that PPA.  All it took was a normal update/upgrade. (You may have to install the "nvidia-current" package if you don't have it installed now.)

---

### Post by -Ziggy- on 2011-01-04
> **gmargo said:**
> Yup, I just rebooted - I'm now running the latest nVidia driver from that PPA.  All it took was a normal update/upgrade. (You may have to install the "nvidia-current" package if you don't have it installed now.)

Well then that X.org rocks!

Thank you for your help. : )

Just one more question, does it matter if I install the "nvidia-current" package after or befor downloading the PPA and rebooting?


Seawolf, I'll try later what you posted to see if it works and I'll post the results here.

---

### Post by gmargo on 2011-01-04
> 
Just one more question, does it matter if I install the "nvidia-current"  package after or befor downloading the PPA and rebooting?
I would add the PPA, do an update/upgrade, then add the nvidia-current package.  No need to install the older nvidia driver first (which amounts to an extra 48MB download!).

---

### Post by joelwalters on 2011-01-14
I'm having the same problem, trying to follow the below instructions:

> **seawolf167 said:**
> First, make sure you are attempting to install the latest drivers from the [official support site]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Second, if you still get the error message, do the following:

Change to a console

```
[CTRL][ALT][F2]
```Stop the X server

```
sudo /etc/init.d/gdm stop
```note: this is the new way

```
sudo service gdm stop
```Install the drivers now according to their install instructions

Restart the X server

```
sudo /etc/init.d/gdm start
```or using the new way

```
sudo service gdm start
```Then you should be good to go

I'm having trouble with "Install the drivers now according to their install instructions". I switch to console and turn off x server and tried the following commands:

sudo chmod 777 /[my directory]/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
    then:
sudo /[my directory]/NVIDIA-Linux-x86_64-100.14.11-pkg2.run

These commands work in the desktop, but in the console it doesn't recognize the directory. Do I need to install differently while in the console?

---

### Post by ajay_vishvanathan on 2011-12-08
> **joelwalters said:**
> I'm having the same problem, trying to follow the below instructions:



I'm having trouble with "Install the drivers now according to their install instructions". I switch to console and turn off x server and tried the following commands:

sudo chmod 777 /[my directory]/NVIDIA-Linux-x86_64-100.14.11-pkg2.run
    then:
sudo /[my directory]/NVIDIA-Linux-x86_64-100.14.11-pkg2.run

These commands work in the desktop, but in the console it doesn't recognize the directory. Do I need to install differently while in the console?


try using sudo sh Nvidia-whatever-the-file-name-is.run

---

