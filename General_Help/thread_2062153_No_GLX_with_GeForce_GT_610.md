---
title: "No GLX with GeForce GT 610"
date: 2012-09-24
forum: General Help
---

### Post by fmmarzoa on 2012-09-24
Hi there,

I have an Asus GeForce GT 610 graphic card in new Desktop PC that I bought some days ago. I have installed Ubuntu 11.10 and nvidia propietary drivers as needed, adding ubuntu-x-swat ppa, but:

- Compiz effects does not work.
- nvidia-settings says "Failed to query the GLX server vendor" on OpenGL/GLX Information
- glxgears won't run and complains about "Error: couldn't get an RGB, Double-buffered visual"

Installed nvidia driver version is 304.43

Any ideas on how to solve this?

Best regards,

---

### Post by einonm on 2012-09-24
Does your processor have inbuilt graphics also? You may currently be displaying your desktop using the inbuilt graphics card which may not support accelerated openGL. To see if there is another graphics adapter present, run 'sudo lshw' on the command line and post the output.

If there is another adapter, there is a PPA for a package called 'bumblebee' which allows you to use the Nvidia card on you system.

---

### Post by fmmarzoa on 2012-09-24
Hi,

Thanks a lot for your answer.

Unfortunately that does not seem to be the problem. nvidia-settings reports to be using GeForce GT 610 graphic processor on GPU 0,and there is no other GPU configured.

Also lshw only reports one vga device, and it is an nVidia one. So lspci does.

$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation Device 104a (rev a1)
$

Any other ideas?

Best regards,

---

### Post by einonm on 2012-09-25
Ok, unfortunately support proprietary code makes things a bit more difficult, but I assume from the driver version number that you are using the 64bit version of Ubuntu?

If so, there is a slightly more recent version of the driver available from the Nvidia website:

[http://www.nvidia.co.uk/object/linux-display-amd64-304.51-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-304.51-driver-uk.html)

Could you give that a try? Note that you should read the installation instructions if you haven't installed an Nvidia driver this way before.

---

### Post by fmmarzoa on 2012-09-25
Hi,

No, I am using a 32bit version. I will try to manually install those drivers to see if they make difference, but I will make a full HD backup first... ;-)

Best regards,

---

### Post by einonm on 2012-09-25
> **fmmarzoa said:**
> Hi,

No, I am using a 32bit version. I will try to manually install those drivers to see if they make difference, but I will make a full HD backup first... ;-)

In which case, the 32 bit driver is listed on the Nvidia website as a lower version (295). I would suggest that you try that one...

---

### Post by bogan on 2012-09-25
Hi!, 

RE: **einonm'**s Post: I just ran nvidia.com>Drivers>Download, and it shows the 304.51 version driver for the gt610 card with 32bit Linux.

Chao!, **bogan.**

---

### Post by fuzzylogic25 on 2012-09-27
Hi,

I am thinking about buying this video card:

[http://www.asus.com/Graphics_Cards/NVIDIA_Series/GT610SL1GD3L/](http://www.asus.com/Graphics_Cards/NVIDIA_Series/GT610SL1GD3L/)

So I am guessing this is the same as yours yes? I mainly want it for its silent cooling (no fan required).


I dont play any compute games, but I do like the graphical stuff like compiz, watching 1080 quality video files.

Will it work fine on this video card?

Does Ubuntu now work for the video card? I am running 10.04 version of ubuntu though, will it still work?

thanks so much in advance for the help!

---

### Post by fmmarzoa on 2012-10-03
> **einonm said:**
> In which case, the 32 bit driver is listed on the Nvidia website as a lower version (295). I would suggest that you try that one...

Hi,

I think that one does not even support GT610, so I am using the latest packed drivers from Ubuntu X Swat.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Best regards,

---

### Post by fmmarzoa on 2012-10-26
JFTR: It seems to be fixed on driver 304.60

---

