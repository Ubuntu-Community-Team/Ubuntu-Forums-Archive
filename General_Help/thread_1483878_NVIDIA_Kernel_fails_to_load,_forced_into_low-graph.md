---
title: "NVIDIA Kernel fails to load, forced into low-graphics mode"
date: 2010-05-15
forum: General Help
---

### Post by the real omni on 2010-05-15
Hi,

I can run Ubuntu 10.04 just fine as long as I have my hardware drivers disabled, but when I enable my hardware drivers I get an error before the GDM login screen that says something to the effect of it being unable to load the NVIDIA Kernel

I'm then given the choice of booting into low-graphics mode, configuring xorg for this hardware, troubleshooting, dropping to console, or restarting X.

Booting to low-graphics mode does nothing useful, just boots to low gfx mode.

Configuring xorg for this hardware does nothing at all - same errors after trying every single option in the configuring xorg section

Troubleshooting is equally useless to me - I can't copy and paste the very-long error reports, I'm not an xorg pro so editing the xorg conf doesn't help me, and when I tried following the option to export all my config and error logs, it said that it has exported it to $xorg_backup_file - but that's just a variable not a file.. after a reboot I can't find this anywhere.

I've googled this and the only useful info I've found is to run nvidia-xconfig as root, which I've done and it has zero effect.

The only temporary solution is to disable the nvidia driver, which lets me boot normally using metacity at full resolution, but has no accelerated 3d or composite overlay so I'm unable to run compiz or have any nifty 3d.

Is there anyone out there who has the skills to help me out here?

Details: 
 Vid card: NVIDIA G96 (according to lspci)
 Driver: NVIDIA accelerated graphics driver (version current) [Recommended]
 OS: Ubuntu 10.04

---

### Post by David Valentine on 2010-05-15
I'm in exactly the same boat.  This does not sound the same as the Plymouth/Grub/nVidia bug noted elsewhere, as I'm getting native resolution but no hardware acceleration.  Is the fix the same?:(

---

### Post by the real omni on 2010-05-15
(bump)

Bug filed at: [https://bugs.launchpad.net/ubuntu/+bug/581033](https://bugs.launchpad.net/ubuntu/+bug/581033)

Still hoping someone might read this post and have some insight to offer.

Thanks in advance (hopefully)!

---

### Post by ankit singh on 2010-05-15
i also had this problem.uninstall ur nvidia driver and open synaptic.
mark 1)nvidia-current-dev
     2)nvidia-current
     3)nvidia-kernel-common
     4)nvidia-current-modaliases

after that reboot and run

sudo nvidia-xconfig 

and that relogin.

u can also go for the driver frm the official website.it works better than this driver

---

### Post by enzio on 2010-05-15
I was having what appears to be the same problem. In my case the problem was that my kernel headers did not match the kernel version (I found this out when I tried to install the driver by hand). 

I went to System->Administration->Hardware Drivers and uninstalled the nvidia driver.

reboot.

sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package
sudo apt-get build-dep linux
You probably only need kernel-package, but since I installed the others I listed them as well.

reboot.

Went to System->Administration->Hardware Drivers and re-installed the nvidia driver.


Hope this helps,
Enzio

---

### Post by the real omni on 2010-05-15
ankit singh, enzio: thanks for your suggestions, unfortunately having tried both those suggestions I'm still back at square one.

Has anyone experienced this with an NVIDIA G96 specifically?

---

### Post by the real omni on 2010-05-18
(bump)

---

### Post by the real omni on 2010-05-22
(bump)

---

### Post by Danno2468 on 2010-05-29
When you get to that Low graphics screen.  Try hitting ctrl+alt+F1 at the same time.  That should bring you to a cli. Then I would shut down the display manager.  Get rid of the old Nvidia driver, and install a new one.  Configure a new xorg.conf

sudo gdm stop
sudo rm /etc/X11/xorg.conf
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-xconfig

---

### Post by EdEase on 2010-12-30
> **Danno2468 said:**
> When you get to that Low graphics screen.  Try hitting ctrl+alt+F1 at the same time.  That should bring you to a cli. Then I would shut down the display manager.  Get rid of the old Nvidia driver, and install a new one.  Configure a new xorg.conf

sudo gdm stop
sudo rm /etc/X11/xorg.conf
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-xconfig

Had the same problem after upgrading 9.10 to 10.04, and the above solution fixed it real fine! Thanks, Danno

---

### Post by p110011 on 2011-01-19
> **Danno2468 said:**
> When you get to that Low graphics screen.  Try hitting ctrl+alt+F1 at the same time.  That should bring you to a cli. Then I would shut down the display manager.  Get rid of the old Nvidia driver, and install a new one.  Configure a new xorg.conf

sudo gdm stop
sudo rm /etc/X11/xorg.conf
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-xconfig

Did this^
But it was necessary. 
Still no driver, opened synaptic package manager, searched nvidia, and installed nvidia-common.
Then system/preferences/appearance selected extras in visual effects and driver was installed.
I'm sure there must be a real cli way to this;)

---

### Post by p110011 on 2011-01-19
,

---

### Post by p110011 on 2011-01-19
.

---

