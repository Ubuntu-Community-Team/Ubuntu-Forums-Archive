---
title: "Nvidia 190.53 and kernel updates"
date: 2010-01-13
forum: General Help
---

### Post by bruno9779 on 2010-01-13
More than an issue is an annoyance.

I have the NVIDIA 190.53 drivers installed on a 64 bit desktop and a 32 bit laptop. 
They work great, I can play stuff like Regnum, that I couldn't play before.
But every time i get a kernel update I have to reinstall them (stop x, go to tty and sudo the installer) It then says they are installed and that they have probably been switched off by my package manager. I cannot get them to work without a reinstall.

Is there any chance this drivers will enter the repos in a realistic time? or ever?

---

### Post by Cas07 on 2010-01-15
I used the nVidia PPA to install 190.53:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

The Synaptic Commit Log below for the packages selected:
```

Removed the following packages:
nvidia-185-kernel-source
nvidia-185-libvdpau
nvidia-glx-185

Upgraded the following packages:
mplayer (2:1.0~rc3+svn20090426-1ubuntu10.1) to 2:1.0~rc3+svn20091207-0ubuntu1~karmic~nvidiavdpauppa11
mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu10.1) to 2:1.0~rc3+svn20091207-0ubuntu1~karmic~nvidiavdpauppa11
nvidia-common (0.2.15.1) to 0.2.15.1-1~nvidiavdpauppa1
nvidia-settings (180.25-0ubuntu1) to 190.53-0ubuntu1~karmic~nvidiavdpauppa1

Installed the following packages:
libvdpau1 (0.3-2~nvidiavdpauppa5)
nvidia-190-kernel-source (190.53-0ubuntu1~karmic~nvidiavdpauppa8)
nvidia-190-modaliases (190.53-0ubuntu1~karmic~nvidiavdpauppa8)
nvidia-195-modaliases (195.30-0ubuntu1~karmic~nvidiavdpauppa5)
nvidia-glx-190 (190.53-0ubuntu1~karmic~nvidiavdpauppa8)

```

---

### Post by bruno9779 on 2010-02-01
exactly what i was looking for

thanks!

---

### Post by Mayfairy on 2010-03-17
> **bruno9779 said:**
> More than an issue is an annoyance.

I have the NVIDIA 190.53 drivers installed on a 64 bit desktop and a 32 bit laptop. 
They work great, I can play stuff like Regnum, that I couldn't play before.
But every time i get a kernel update I have to reinstall them (stop x, go to tty and sudo the installer) It then says they are installed and that they have probably been switched off by my package manager. I cannot get them to work without a reinstall.

Is there any chance this drivers will enter the repos in a realistic time? or ever?

I'm not having any problems with my drivers, but stumbled upon this thread by searching Regnum Online stuff. For some strange reason I'm not getting the game to work. 

Using an Nvidia 9800GT card with 190.53 drivers that for sure are working ok. 
bruno9779, have any pointers on how you got the working?

EDIT: 

Strange.. Was gonna re-install my drivers but I just got to the part of uninstalling the old one and instead of booting the machine I thought I'd go to X and as a whim I tried to launch Regnum and it worked. :)
It seems that I have 190.53 still installed so I guess instead of uninstalling the drivers it reinstalled them. My xorg.conf still looks the same though. 

Guess that teaches us never to underestimate the power of reinstalling. :)

---

### Post by pbrane on 2010-03-17
What I did is add this script to /etc/kernel/postinst.d/
```

#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0

```

if you place the downloaded driver file in /usr/src and create a link to it
```

ln -s /usr/src/NVIDIA-Linux-x86_64-190.53-pkg2.run /usr/src/nvidia-driver

```

you should be all set. When a new kernel is installed the files in the postinst.d directory are run. This way I can install the latest driver and it will be built for any new kernels that are installed.

---

