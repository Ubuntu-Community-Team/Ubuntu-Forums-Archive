---
title: "NVidia driver problems"
date: 2011-06-30
forum: General Help
---

### Post by k3ith on 2011-06-30
Hi,

New here so please go easy. I am trying to get OpenGL running on Ubuntu 10.04 (64 bit). The hardware is a Dell box with a NVidia Quadro 600 graphics card; I am also running under VMware. 

I tried using "apt-get install nvidia-current", followed by "nvidia-xconfig", which told me a new xorg.conf file had been written. I then rebooted. A dialog appeared saying Ubuntu is running in low-graphics mode and that it had failed to load module "nvidia" and no drivers available.

As I didn't seem to get very far this way, I tried downloading the NVidia 64 bit linux driver  version 275.09.07 and ran this from the console. Firstly it told me that I do not appear to have a NVidia GPU supported by this version of the driver (yet NVidia's description of the driver says it does support this gpu). I went ahead and let it try to build the kernel module but then it failed with the message "failed to load kernel module 'nvidia.ko"

I'm not clear how to proceed on this one. Has anyone else got a Quadro 600 card to work? If so, how?

Thanks for any advice in advance!

---

### Post by Ozymandias_117 on 2011-06-30
If you're running under VMWare, the guest OS doesn't get direct access to your graphics card.  Instead you need to install the driver for the VMWare graphics, which should be the package xserver-xorg-video-vmware.

```
sudo apt-get install xserver-xorg-video-vmware
```

---

### Post by k3ith on 2011-06-30
Thanks, I tried that, and got the message:

xserver-xorg-video-vmware is already the newest version.

---

### Post by k3ith on 2011-06-30
What's worse, even reverting to the default which I found from some googling with:

sudo dpkg-reconfigure -phigh xserver-xorg

leaves the graphics unable to run OpenGL in mesa software emulation mode. Any ideas on how I can get a workable OpenGL display running?

---

### Post by grahammechanical on 2011-06-30
In a virtual machine do you not need to specify the ram memory that will be used as video memory? Could this be what is restricting the display?

Regards

---

### Post by wodenickel on 2012-03-01
I'm hoping that the original poster has already succeeded but I wanted to clarify for future finders of the post.

In a Virtual machine, that machine NEVER knows what type of card you have in the host computer, it uses the virtual driver provided by the virtualization package. In this case it's VMware but the same happens in VirtualBox - the hardware card is not exposed to the VM's operating system.

Thus the Nvidia drivers have no bearing on any of this for the Virtual Machine.

In VirtualBox and I believe also VMware, you DO specify the amount of RAM and, for VirtualBox, whether 3D acceleration should be used by the virtual video card. Perhaps relooking at those parameters and adding RAM / turning the 3D on will help things.

I normally use VirtualBox but have used VMWare as well. I run Ubuntu and don't remember loading anything OpenGL specific though perhaps I did.

Running glxgears will let you know if you have things working.

good luck,
Mark

---

