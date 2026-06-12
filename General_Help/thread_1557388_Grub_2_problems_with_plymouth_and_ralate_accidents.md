---
title: "Grub 2 problems with plymouth and ralate accidents"
date: 2010-08-20
forum: General Help
---

### Post by unconcrete on 2010-08-20
Hi Net,
I'm trying to make the splash plymouth working, since my screen remains black at boot. I am not sure of the steps I'm going to do, then any suggestion or warning is welcome. I'm trying to follow the guide found at [http://www.linuxqualityhelp.it/supporto/viewtopic.php?f=25&t=5950](http://www.linuxqualityhelp.it/supporto/viewtopic.php?f=25&t=5950).
I resume: I have a Nvidia Geforce gtx260 for a Philips flat screen 220WS. From Nvidia-settings I know my current resolution is 1680x1050 that is the same value reported in the output ou xrandr:
djangou@ESPERYDES:~$ xrandr
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050 
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0*    51.0  
   1440x900       52.0     53.0  
   1400x1050      54.0     55.0     56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0  
   1280x960       61.0  
   1280x720       62.0  
   1152x864       63.0     64.0     65.0     66.0  
   1024x768       67.0     68.0     69.0  
   960x600        70.0  
   960x540        71.0  
   840x525        72.0     73.0     74.0     75.0  
   832x624        76.0  
   800x600        77.0     78.0     79.0     80.0  
   720x450        81.0  
   700x525        82.0     83.0  
   680x384        84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0  
   512x384        91.0     92.0  
   400x300        93.0  
   320x240        94.0     95.0  
I wish to compile my grub 2 in order to make plymouth or a kind of it finally working. But my skill in treatibg this items is very poor and my Grub could be at stake. I've learned not all resolutions are accepted by Grub2. In fact the first time I tryed it the result was a blocked Grub. No way to enter other partitions. Only to format again the ext4  partitions. I know that probably I've made some errors, and I hope you help me to avoid to repeat them. 
Now I describe what I'm gong to do step by step.

1. Exchange vesafb with uvesafb by installing v86d.

2. sudo gedit /etc/default/grub
change [# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"] with 
[GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"]
add [GRUB_GFXMODE=1680x1050]
Note: the guide warns me to avoid the string GRUB_GFXPAYLOAD_LINUX=keep and I'll comment out it. Save grub.

3.sudo gedit /etc/initramfs-tools/modules
add[uvesafb mode_option=1680x1050-24 mtrr=3 scroll=ywrap] save initramfs

4.from terminal do: [echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash] so I should use the uvesa frame buffer.

5. finally:
[sudo update-grub2
sudo update-initramfs -u] and reboot.
In your view these steps are right or I'm going to damage again the Grub2?
Thaks in advance.
Enrico

:popcorn:

---

