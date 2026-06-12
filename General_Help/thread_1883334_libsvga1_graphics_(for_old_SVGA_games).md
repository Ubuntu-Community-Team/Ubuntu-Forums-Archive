---
title: "libsvga1 graphics (for old SVGA games)"
date: 2011-11-18
forum: General Help
---

### Post by clubsoda on 2011-11-18
I guess SVGA applications are the linux equivalent of DOS games. :)
However, with each new Ubuntu release it's getting more and more difficult to get the console into SVGA mode. Here are some approaches which should work.

**1)** Run an older version of Ubuntu. [Lucid? Added benefit of OSS sound.]
OR
**2)** Use a graphics card which isn't supported by KMS (kernel modesetting), i.e. not ATi/AMD/Intel. The chipset section of the file /etc/vga/libvga.config has a good list of candidates.
OR
**3)** Deactivate KMS [since Maverick]
AND
**4)** Prevent GRUB from setting the console to graphic mode [Natty onwards].

**Deactivating KMS**
Add *nomodeset* to the linux line at boot. [If using a live CD, press F6 then Esc to edit the bootstring]. To make this change permanent, add *nomodeset* to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and then sudo update-grub.
An alternate approach for ATi/AMD is to add *radeon.modeset=0* to the bootstring, likewise *i915.modeset=0* for Intel graphics. These can be made default by creating a file like /etc/modprobe.d/radeon-kms.conf containing ```
options radeon modeset=0
```

**Preventing GRUB from setting the console to graphic mode**
Even if SVGA works with a live CD, it can be broken once the system is installed to disk. Why? GRUB puts the console into graphical mode to display a pretty picture during boot. This can be deactivated by editing the grub commands at boot time. Look for the line ```
set gfxpayload=$linux_gfx_mode
``` and change it to ```
set gfxpayload=text
```To make this change permanent, edit /etc/default/grub to include```
GRUB_GFXPAYLOAD_LINUX=text
```and comment out any line which sets GRUB_GFXMODE. Then sudo update-grub.


**Diagnosis**
This command tells an interesting story```
dmesg|grep "fb0:\|Conso\|modes"
```Ideally, you want to see output like```
Console: colour VGA+ 80x25
[drm] VGACON disable radeon kernel modesetting.
```SVGAlib should then be working.
Stuff you don't want to see would be```
Console: colour dummy device 80x25
Console: switching to colour frame buffer device 160x64
fb0: VESA VGA frame buffer device

or

[drm] radeon defaulting to kernel modesetting.
[drm] radeon kernel modesetting enabled.
[drm] initializing kernel modesetting.
Console: switching to colour frame buffer device 240x75
fb0: radeondrmfb frame buffer device
```Enjoy!


PS: Please post back with any corrections or improvements, or if you know how to
**5)** Make libsvga talk to radeondrmfb or vesafb
OR
**6)** Run SVGA in an X-window wrapper.

---

