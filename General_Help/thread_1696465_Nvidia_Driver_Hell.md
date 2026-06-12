---
title: "Nvidia Driver Hell"
date: 2011-02-27
forum: General Help
---

### Post by Precipitous on 2011-02-27
I am running UbuntuStudo 10.10 and have an Nvidia Geforce 7300 LE video card. Every time there is an update to the Nvidia Current driver, I get a black screen and log-in prompt when I reboot, unless I boot into an older kernel. This hasn't been too much trouble until the last couple of updates. Now the only way I am able to boot into a working desktop is to install and run the Nvidia driver release 260.19.36 from their website, and to boot into kernel 2.6.35.24. None of the other kernels will work...

I desperately need to be able to use either the low latency or real time kernels, but am now unable to do so. In the past I had to patch the video driver before being able to do so, but now I am unable to do that either. I am assuming because of the driver being downloaded from Nvidia instead of from one of the repositories?

Does anyone have a good suggestion for how to get out of this Nvidia hell? If not, what video card would be best to switch to. I have very little free money, so inexpensive is best.

---

### Post by alzie on 2011-02-27
If I read you correctly, each time there is a kernal update you lose your nVidia driver.

I had a similar problem after installing from the nVidia site but I did find instructions to have the nVidia drivers auto update after a kernal update here: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

It has worked for me, it might be what you are looking for.

Hope it helps.

---

### Post by Precipitous on 2011-03-04
Just in case anyone has this same problem in the future, here are the steps I went through to resolve it:


[LIST=1]
[*]Download the latest driver from [http://www.nvidia.com/content/global/global.php](http://www.nvidia.com/content/global/global.php)
[*]Open module blacklist as admin:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
[*]Add the following lines, then save:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[*]Uninstall any previously installed Nvidia drivers
```
sudo apt-get --purge remove nvidia-*
```
[*]Reboot the computer (should boot to a black screen with a command window style text log in prompt)
[*]Log in as per normal
[*]Install the driver
```
sudo service gdm stop
cd (directory the driver was downloaded to in Step1)
sudo sh NVIDIA-Linux-x86-260.19.36.run   (substitute your driver version)
sudo service gdm start
```
[*]Log in to desktop
[*]When desktop has loaded re-configure X
```
sudo nvidia-xconfig
```
[/LIST]

---

