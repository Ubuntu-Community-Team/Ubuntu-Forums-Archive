---
title: "Ubuntu 11.10 nvidia - Get to 1600 x 1200 resolution?????"
date: 2011-12-07
forum: General Help
---

### Post by blakeljb on 2011-12-07
Newbie.  Installed 11.10 on an HP with a GeForce 6150SE nForce 430 graphics card.  Works well at 1600 x 1200 in windows but can only get to 1024 x 768 in linux.  Have done all updates to 11.10.  Tried the proprietary drivers and the "NVIDIA binary Xorg driver, kernel module and VDPAU library", "nvidia_173_updates", "nvidia_current" drivers.  None get me to 1600x1200.  

output of xrandr as follows:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  

Messed around with xorg.conf and tried to set new modelines in xrandr but seemed to get into more problems than closer to 1600 x 1200.

Other drivers out there to try?  Other suggestions?

---

### Post by thaelim on 2011-12-08
The nVidia binary drivers do not support xrandr. You need to configure the resolution using the nvidia-settings utility, which is installed when you install the binary drivers.

---

### Post by blakeljb on 2011-12-08
nvidia-settings doesn't show a 1600x1200.  Other drivers or ways to force it?

---

### Post by Alln on 2012-01-05
blakeljb,

I have a HP with a GeForce 6150SE nForce 430 too.
But, I've installed Ubuntu 11.10 and then, graphic cards driver. (290.10)

But the X simply don't start! Black screen, forever! :confused:

After driver installation, I've used this command to configure xorg.conf:```
sudo nvidia-xconfig --mode nvidia-auto-select
```

With this, you may have the best resolution...

My driver was properly installed. Because I've made this:
```
sudo service lightdm stop
cd /usr/share/X11
sudo mv xorg.conf.d xorg.conf.test
sudo service lightdm start
```

And then, 1360x768@60Hz login page show's perfect! But, no mouse, no keyboard, no Power button... No any input! :(

Can you, please, explain the steps to install and configure GeForce 6150SE nForce 430 in Ubuntu 11.10?

P.S: I've started linux by editing boot entry "quiet splash" to "nomodeset" and installed the "NVIDIA-Linux-x86-290.10.run"

Best Regards

---

