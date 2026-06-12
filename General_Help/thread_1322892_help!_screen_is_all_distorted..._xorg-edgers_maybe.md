---
title: "help! screen is all distorted... xorg-edgers maybe"
date: 2009-11-11
forum: General Help
---

### Post by rygar on 2009-11-11
I logged in today, and was treated with the lovely screenshot (attached).  As you can see, the graphics are all weird and its very hard to navigate as most text is missing (even on dialog boxes).  Also, the graphics were distorted on the boot and log on screens as well.

I thought it might have something to do with the xorg-edgers ppa, so i removed it, update, and upgrade, but it didnt seem to update any xorg packages.  is there a way to get my old ones back?  other than that i dont know what it might be.  i have ubuntu-boot ppa as well, but i dont think that has anything to do with it...

please help!  thanks!
jeff



edit: i probably should have mentioned:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by rygar on 2009-11-11
ahh, fixed it!  after removing the PPA,

```
 sudo apt-get install libdrm-dev/karmic libdrm2/karmic libdrm-intel1/karmic libdrm-radeon1/karmic xserver-xorg-video-intel/karmic libdrm-nouveau1/karmic libgl1-mesa-dri/karmic libgl1-mesa-glx/karmic libgl1-mesa-dev/karmic libglu1-mesa/karmic mesa-common-dev/karmic mesa-utils/karmic xserver-common/karmic xserver-xorg-core/karmic xserver-xorg-input-evdev/karmic xserver-xorg-input-evdev/karmic xserver-xorg-input-synaptics/karmic xserver-xorg-video-ati/karmic xserver-xorg-video-nv/karmic xserver-xorg-video-openchrome/karmic xserver-xorg-video-radeon/karmic

sudo dpkg-reconfigure xserver-xorg
```

For future reference, is there any way to uninstall packages installed by a repository after I remove the repository?  Any way to force apt to download versions from the repository (even if its a downgrade)? etc...  Any solution that helps in a general case without having to know all those package names?

---

