---
title: "Virtualbox Natty Gnome guest randr gamma error"
date: 2011-06-07
forum: General Help
---

### Post by HannoG on 2011-06-07
Hi,

I'm a Ubuntu beginner. 
System: Ubuntu 11 Natty with Gnome GUI as main OS (Nvidia 9800 GT), for some reasons I need to run another Natty with Gnome GUI in a VirtualBox VM ( Virtualbox version 4.0.8 ), Guestadditions already installed.
Here's the problem:
The screen resolution in the VM is 1024 x 768 maximum, while the desired one would be 1280 x 1024.
This is the output of randr:

user@user-VirtualBox:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

Because of the gamma error it is not possible to manually add the desired resolution in randr.
Sorry, I know, there are some posts about it already, but wasn't able to sort it though.
Thanks for help.

---

