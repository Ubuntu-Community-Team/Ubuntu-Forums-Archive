---
title: "Amarok 1.4 and NVIDIA 190.42 conflicts"
date: 2009-11-18
forum: General Help
---

### Post by aniruddha on 2009-11-18
Hello all, I have recently installed the new 190.42 drivers from NVIDIA by adding the "ppa:nvidia-vdpau/ppa" in Karmic 64bit. However, during install I was told that amarok14 (got via Bogdan's PPA) as well as libxine1 (and a few related entries) and nvidia-185-libvdpau would have to be removed. I chose to go ahead, figuring (pretty stupidly I suppose) that I could always re-install these later. The install of the 190.42 drivers went off successfully. 

Now however, when I try to install amarok14, (both by apt-get and in Synaptic) I am told I would have to uninstall the nvidia-190-glx and nvidia-190-libvdpau entries. Has anyone else experienced this problem (and hopefully found a workaround?)? Any help would be greatly appreciated.

As an aside, I was able to install the 190.42 drivers manually using the method given at [http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185) and still retain amarok14. Nvidia settings should the system using the 190.42 drivers and amarok14 was able to install nvidia-185-libvdpau. Does anyone know why this was, and if this is indeed advisable?

Many thanks people.

---

### Post by aniruddha on 2009-11-19
anyone?

---

### Post by mc4man on 2009-11-20
Whether it was done intentionally or not that ppa has conflicting packages for karmic which is a poor idea.

The conflict is in the libxine1 packages, which while they would work with fine with amarok14, ect. will not work with the nvidia 190 packages.

You can see that clearly here in the control file for libxine1-bin

> Package: libxine1-bin
Source: xine-lib
Version: 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
Architecture: amd64
Maintainer: Brandon Snider <brandonjsnider@gmail.com>
Installed-Size: 3104
Depends: libc6 (>= 2.8), libfreetype6 (>= 2.2.1), libx11-6, libxext6, libxinerama1, [COLOR="Red"]nvidia-185-libvdpau[/COLOR], zlib1g (>= 1:1.2.3.3.dfsg)

So if you wanted that ppa's nvidia 190, then, as things stand now, install it and **then disable the ppa**. ( plus *probably* make sure  all libxine1 packages are removed

Then reload your sources and re-install amarok14 and your libxine1 packages from the karmic repo


Now if this was a mistake rather than intentional, you could dl the libxine1-bin package and thru a little script hack the control file and change the depend to nvidia-190-libvdpau and have both the 190 nvidia and the patched xinelibs from the ppa.

(this I don't know, and have no use for either myself atm, so I'm not going to see what the deal is...

---

### Post by aniruddha on 2009-11-22
Hmmm. Thanks for the info. I was working over this on the weekend and the conflict is definitely with the libxine package. I am not sure about the nvidia ppa either (got it from [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)). Am just going with the manual driver install from now. There don't seem to be any problems and amarok14, mplayer and some d3d games are all working fine.

---

### Post by aniruddha on 2009-11-23
Well that was simple. I just got an update from the 190 ppa which solved both the libvdpau and libxine1 conflicts. So onward to amarok14 on nvidia 190.42. Woot!!!

Thanks for all the help, and a special thank you to the maintainers of the ppa!

---

