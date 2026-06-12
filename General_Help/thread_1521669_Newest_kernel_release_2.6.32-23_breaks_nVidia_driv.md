---
title: "Newest kernel release 2.6.32-23 breaks nVidia drivers"
date: 2010-07-01
forum: General Help
---

### Post by Tumex on 2010-07-01
Hey there guys and gals,
I just updated to the latest kernel release 2.6.32-23 and it seems like it broke my nVidia drivers.

I get the following error at start-up

(EE) *Failed to load module* "*nvidia*"  (*module does not exist*, *0*) 
(EE) *No drivers  available*.

I cannot boot into the system at all, and every time that I try I get sent to the console. I have tried reinstalling the nVidia drivers, xServer, xserver-xlg and nouveau drivers but to no avail.

I am certainly aware that if I had access to the latest linux-restricted-modules this would work... but maybe there is a workaround for the time being?

Thanks a lot and I really appreciate the help,
Wish you luck and success,
Tumex

---

### Post by justleen on 2010-07-01
If you have installed the drivers fromsource: yes, it will break when a new kernel is installed. You would have recompile to the new kernel, to get the modules installed.

---

### Post by Tumex on 2010-07-01
> **justleen said:**
> If you have installed the drivers fromsource: yes, it will break when a new kernel is installed. You would have recompile to the new kernel, to get the modules installed.
Hey there, thanks for the quick reply.

How would I go about recompiling to the new kernel? Thanks!

---

### Post by justleen on 2010-07-01
You would just repeat the steps you have taken to get it to work in the first place.

---

### Post by Tumex on 2010-07-01
> **justleen said:**
> You would just repeat the steps you have taken to get it to work in the first place.
Mm I cannot see how running --

```
sudo apt-get install nvidia-current
```AGAIN can fix the problem. I already tried that.

I'm quite new to Ubuntu, but I still cannot see how running again the commands that I ran would work this time.

Thanks for the help,
Tumex

---

### Post by alan_uk on 2010-07-01
I have the same problem - (EE) NVIDIA failed to load NVIDEA Kernal Module .... (EE) No driver available

Having problems in recompiling to the new kernel, to get the modules installed. Just get an error message.

Alan

---

### Post by alan_uk on 2010-07-01
I have tried reinstalling using 

sudo apt-get install nvidia-current

Error! Bad return status for module build on kernel: 2.6.32-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-173/173.14.22/build/ for more information.
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-173
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by justleen on 2010-07-01
If you used apt-get to install the drivers, then you haven't installed from source..

---

### Post by Tumex on 2010-07-01
> **justleen said:**
> If you used apt-get to install the drivers, then you haven't installed from source..
Alright, did a quick search and found how to install from source.

Here's what I did:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/256.35/NVIDIA-Linux-x86-256.35.run
```

```
sudo apt-get remove --purge nvidia-current
```

```
sudo sh ./NVIDIA-Linux-x86-256.35.run
```

Successfully installed, but still not working although it fixed the resolution somehow (it's now back to 1680x1050).

I still get the "No drivers available" error!

Thanks again for the help,
Tumex

---

### Post by clrg on 2010-07-01
I recently updated to 2.6.32-23, and I got the same error.

Luckily, I still had the proprietary Nvidia-Driver in my download directory, so I just stopped X11 and reinstalled the driver. It recompiled the module, reinstalled some files, and after a reboot, it worked like a charm. 

I don't see why anyone would recommend you to recompile the kernel, reinstalling the driver suffices.

---

### Post by TheStroj on 2010-07-01
Edit your xorg.conf file and tell it to use 'vesa' drivers (make sure to backup the xorg.conf before doing this: just copy it to some other place).
```
nano /etc/X11/xorg.conf
```

At 'Section: Device' change Driver from whatever it is to vesa, so it looks like:
```
Driver "vesa"
```

Now save the file and try to get into the desktop by running
```
startx
```

This will get you to desktop using default drivers. Now remove the old drivers with either Synaptic or whatever you will use, then install new drivers.

Hope it works :)

---

### Post by Leppie on 2010-07-01
i'm no expert with nvidia cards, but i think you would want to do something like:
```
nvidia-config
```

---

### Post by stoneage on 2010-07-01
Double post


:/

---

### Post by stoneage on 2010-07-01
If I remember rightly, it is generally a bad idea to install drivers from diverse sources. Install either one or the other, but not both. 

It might be a good idea now to purge all nVidia files and reinstall.

---

### Post by Spr0k3t on 2010-07-01
I had this issue as well.  I rolled back the nvidia-current as well as nvidia-current-modaliases to the lucid-release drivers.  That fixed the problem I was having.  I tried rolling the kernel back to 2.6.32-22 and -21... but it wasn't until I change the nvidia portion that I could log in with the nvidia drivers from the repos.

---

### Post by danbuter on 2010-07-01
Curious as to how something this important made it through Ubuntu QC.

---

### Post by fragos on 2010-07-01
I didn't experience this problem and I believe that may be because I ran the Hardware Drivers preferences after the initial install of 10.04 and selected the recommended nvidia-current to activate. This insures I get a compatible driver whenever the kernel is updated.

---

### Post by DougEdey on 2010-07-01
I did this originally and I got some massive issues with my nvidia Quadro 140, basically I can see GDM fine, but when I get to the desktop I can only see the top left of the screen

---

### Post by DougEdey on 2010-07-01
I should point out that one system (Nvidia Quadro FX 570) is fine with all the updates, the 195.36.24

My other system, Nvidia Quadro 140, is having massive issues.

I've rolled the 140 back to the older 195.36.15 drivers and the 173 series drivers, on both kernels .22 and .23 and it doesn't work still.

What I can tell is it's a desktop effects issue, anything above "none" causes me to lose my display basically!

---

### Post by DougEdey on 2010-07-01
Turns out something caused CCSM to disable detecting outputs, nothing to do with this issue

---

### Post by mbower on 2010-07-01
I had the same issue, seems adding **nvidia-current** to **/etc/modules** worked.

---

### Post by abadr on 2010-07-01
A temporary solution is to boot using the previous kernel. Since 10.04 is using Grub2 which hides the kernel and OS boot menu, press shift while booting to make it show again. Boot using an old kernel and using Synaptic or similar tool remove the latest kernel. 

Hope this helps

---

### Post by M@XflY on 2010-07-02
I have a new solution.

I think he have a problem with compilation official nvidia driver with this new kernel or with dkms.

I use this method and it's works !! :D

In first time boot to the kernel 2.6.32-23.
Make :
```
sudo apt-get install -f
```to check your package and repair their.

remove and install the hearders :
```
sudo apt-get install --reinstall linux-headers-2.6.32-23-generic
``` purge and install nvidia drivers for this kernel :
```
sudo apt-get purge nvidia-*
sudo apt-get autoclean
sudo apt-get install nvidia-glx-185
```use nvidia-glx-185 if you use this nvidia driver version 195.36.24

reboot and enjoy it !! :p

---

### Post by t4thfavor on 2010-07-12
somewhat similar problem where the new kernel fails to install correctly, and apt errors with a bunch of gibberish after generating a new menu.lst.

I did a dpkg-reconfigure nvidia-common and all is well.

 hope it helps you all figure this problem. 
 
pm me with QQ'a  its the only way to get me. I will make sure they get to the board if relevant.

---

### Post by cfraser on 2010-07-18
I added the following to /etc/modprobe.d/nvidia-graphics-drivers.conf:

alias nvidia nvidia-current

This seems to have worked for me.

---

### Post by thenellt on 2010-07-25
Anyone have any luck with the 256.35 drivers? I can't even get them to install from source.

---

