---
title: "Update 10.04 wiped out video"
date: 2011-06-11
forum: General Help
---

### Post by dwlamb on 2011-06-11
[SIZE=2][FONT=times new roman,serif]Good day,

I am running Ubuntu 10.04.  I ran  an update after receiving notice from Update Manger to do  so.  I was prompted to reboot. My video drivers no longer load for an  NVIDIA GeForce 210 video card. 

Initially, I found this out while the system was rebooting.  The  system started in low graphics mode.  I examined the kernel.log but can not discern it enough to nail down the problem

If I attempt to run 'NVIDIA X Server Settings' from System -> Preferences I get the message:[/FONT][/SIZE][SIZE=2][FONT=times new roman,serif]
   [/FONT][/SIZE][INDENT][SIZE=2][FONT=times new roman,serif]You do not appear to be using the NVIDIA X driver.  Please edit  your X configuration file (just run `nvidia-xconfig` as root), and  restart the X server.[/FONT][/SIZE]
[/INDENT][SIZE=2][FONT=times new roman,serif]Doing so produces no joy.  I ran [FONT=Courier New][SIZE=1]sudo  nvidia-xconfig [/SIZE][/FONT]then Ctrl+Alt+Backspace to restart the X-server and my  low resolution and mirrored display on 2 monitors remains unchanged.
    
Attempting to troubleshoot the problem, I found this [/FONT][/SIZE][https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and tried the steps under **How to install the NVIDIA driver in Ubuntu 9.10 or higher**.  However, Ubuntu could not find any proprietary drivers to enable.
 
Following this:[INDENT]If the restricted driver remains unactivated after attempting to  activate it in the  Hardware Drivers dialog, you may not have the  appropriate linux headers installed to compile the driver. Ensure that  the linux-headers-XXX and linux-restricted-modules-XXX packages are  installed, where XXX matches the version of the kernel you are using  (linux-image-XXX).  
[/INDENT]I am not able to determine the linux-restricted-modules-XXX packages.   Through the Synaptic Package manager, I can determine linux-headers and  linux-image as 2.6.32-31.61 or 2.6.32-32.62.

Is there a solution to getting my video back?

---

