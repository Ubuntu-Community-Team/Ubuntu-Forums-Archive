---
title: "Updating Geforce gt 540m graphics driver, help :c"
date: 2012-06-20
forum: General Help
---

### Post by Kiraush on 2012-06-20
I'm trying to use the .run file from the geforce website to update my drivers, I'm doing:
```
cd ~/Desktop
```
```
chmod +x NVIDIA-Linux-x86_64-295.59.run"
```
```
sudo ./NVIDIA-Linux-x86_64-295.59
```

and this pops up:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 20 18:14:41 2012
installer version: 295.59

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1164' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Any ideas?

---

### Post by oldos2er on 2012-06-21
You need to "kill" the running X server before you can install those drivers. But instead of doing that, I would encourage you to install the drivers from this PPA, [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
Doing so will make installing and updating the drivers much easier.

---

### Post by Kiraush on 2012-06-21
> **oldos2er said:**
> I would encourage you to install the drivers from this PPA, [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

Does it matter which graphics card I have? When I look at the details of it, it says it's for:
>   GeForce GT 620M      GeForce GT 640M      GeForce GT 640M LE      GeForce GT 650M      GeForce GTX 660M      GeForce GTX 670M      GeForce GTX 675M      GeForce GTX 555      GeForce GTX 560 SE      GeForce GT 415      GeForce GTX 460 v2      NVS 5400M      NVS 310      Quadro 410

My notebook has a GeForce GT 540m

---

### Post by oldos2er on 2012-06-21
Maybe this will help? [http://askubuntu.com/questions/107475/nvidia-optimus-geforce-gt-540m-not-recognised-as-a-proprietary-driver](http://askubuntu.com/questions/107475/nvidia-optimus-geforce-gt-540m-not-recognised-as-a-proprietary-driver)

---

