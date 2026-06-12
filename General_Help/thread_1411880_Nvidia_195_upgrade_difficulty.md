---
title: "Nvidia 195 upgrade difficulty"
date: 2010-02-20
forum: General Help
---

### Post by Robbyx on 2010-02-20
The software manager advises that I have one update to make. It is the nvidia binary driver as follows:

> These binary drivers provide optimized hardware acceleration of
OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and flat panel displays are also supported.
Please see the nvidia-195-kernel-source package for building the kernel module required by this package. This will provide nvidia-kerne

The following error message pops up when the installation of the driver is chosen:

```
E: /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-195-libvdpau 0
```

I have just restarted the computer and it says something to the effect that the nvidia driver is incomplete and gives me the option to start in low resolution mode.

What should I do?

---

### Post by flammon on 2010-02-26
The thread is marked as solved but I didn't see the solution so here it is.

```
sudo dpkg --force-all -i /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_amd64.deb
```

---

### Post by Robbyx on 2010-02-27
Thanks for adding the solution for future reference.

---

### Post by Robbyx on 2010-03-24
> **flammon said:**
> The thread is marked as solved but I didn't see the solution so here it is.

```
sudo dpkg --force-all -i /var/cache/apt/archives/nvidia-glx-195_195.36.03-0ubuntu1~karmic~nvidiavdpauppa2_amd64.deb
```

Will this work for intel 32 bit?

---

