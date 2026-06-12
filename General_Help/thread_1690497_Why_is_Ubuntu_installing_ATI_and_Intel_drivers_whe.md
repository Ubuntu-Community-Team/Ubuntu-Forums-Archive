---
title: "Why is Ubuntu installing ATI and Intel drivers when I have Nvidia?"
date: 2011-02-18
forum: General Help
---

### Post by veggen on 2011-02-18
My update manager at some point informed me that there are updates for my (already installed) ATI and Intel X.org drivers. Since I have Nvidia, I can't comprehend why would this be installed in the first place, let alone updated... So, does anyone know what's the catch here?

---

### Post by sikander3786 on 2011-02-18
Did you install the updates? If not, please post a screenshot or an output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

So no when it asks to proceed.

And also post the output of these commands please.

```
lspci | grep VGA
glxinfo | grep vendor
```

---

### Post by veggen on 2011-02-18
List of packages:
> 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  fglrx-modaliases intel-gpu-tools libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 nvidia-185-modaliases nvidia-current
  nvidia-current-modaliases nvidia-glx-185 nvidia-settings
  xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-radeon
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.1MB of archives.
After this operation, 4,428kB of additional disk space will be used.
Do you want to continue [Y/n]? Abort.
It's these: 
intel-gpu-tools
libdrm-intel1 
libdrm-radeon1
xserver-xorg-video-ati 
xserver-xorg-video-intel 
xserver-xorg-video-radeon
that I don't understand why I need.
> 
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)


> 
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation


---

### Post by sikander3786 on 2011-02-18
Did you check under Software Center or Syanptic if some nvidia or ATI packages are installed there accidently...?

---

### Post by veggen on 2011-02-18
I now see that I have xserver-xorg-video-all package installed, which installes all X.org drivers. I have no idea how that got installed, but I'm removing it.

---

### Post by Vaphell on 2011-02-18
i think they are installed by default so your machine can work right off the bat when you change your gfx hardware. They are about 1.5MB in size so no big deal. Of course you don't need them.

---

