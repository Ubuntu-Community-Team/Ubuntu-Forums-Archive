---
title: "How to install the latest Nvidia graphics driver in Ubuntu 64 bit?"
date: 2012-06-12
forum: General Help
---

### Post by Welly Wu on 2012-06-12
[http://www.codeweavers.com/support/tickets/browse/?ticket_id=895356;layout=user_tickets;sort%5Bstatus%5D=ASC](http://www.codeweavers.com/support/tickets/browse/?ticket_id=895356;layout=user_tickets;sort%5Bstatus%5D=ASC)

I purchased Codeweavers' CrossOver for Linux 64 bit version 11.1.0 yesterday for $59.99 USD for a 12 month license subscription. If you read the support ticket that I posted, Andrew Balfour responded by telling me to install the Nvidia 295.53 64 bit closed source proprietary graphics driver for my Nvidia GeForce GT 325M GPU with 1.00 GB of DDR3 SODIMM SDRAM and Nvidia Optimus technologies. When I tried to install the Nvidia 295.53 64 bit graphics driver, it tells me that my X Server is still running and I need to exit the X server to continue to install. However, I did install the latest Nvidia graphics driver by adding and installing the Bumblebee Project version 3.0.2 and the X-Swat/X-Updates PPAs. When I launch nvidia-settings, it tells me that I am not running the Nvidia X server and I should run nvidia-xconfig as root and reboot my computer to let the changes take into effect. I am a bit concerned about doing this as I think that it will lead to a failure to launch the X Server and the Ubuntu Unity desktop environment with 3D hardware graphics acceleration. According to the Nvidia readme file, the nvidia-xconfig will make a backup of my current X Org server configuration. How do I do this by myself manually just in case? I read and carefully followed the directions regarding ptrace. It is now permanently set to kernel.yama.ptrace_scope = 0 in my /etc/sysctl.d/10-ptrace.conf file.

This is due to the fact that Codeweavers' CrossOver for Linux 64 bit version 11.1.0 is telling me that libGL.so.1 library is missing. Furthermore, my Valve Corporation Steam client fails to run properly resulting in the "Fatal error: VGUI_Setup failed" error message.

I decided to bring this to the attention to the Ubuntu Forums community to see if anyone here might be able to help me with two specific problems:

1. Is it safe for me to install the Nvidia 295.53 64 bit graphics driver when I have the Bumblebee Project version 3.0.2 installed with the X-Swat/X-updates PPAs? How do I install the Nvidia 295.53 64 bit graphics driver? Should I run nvidia-xconfig as root and reboot my computer as an alternative solution?

2. How do I get Valve Steam to run properly without errors?

Thank you.

---

### Post by nj_peeps on 2012-06-12
I have been running the Nvidia closed source drivers for years now, and have not had any issues.  (currently on 295.40)  To install, you need to stop your X server and window manager.  Log out of your current GUI session.  and press Ctl-Alt-F1, this will bring you to console session.  Login as your self and run.
```
sudo service lightdm stop
```This will stop all the X server, and all other graphics. Then run the the nvidia driver file (must be done as root) ```
sudo sh NVIDIA-Linux-x86_64-295.53.run
```I have always had the Nvidia setup backup and edit the xconf.org file, and then gone back and edited it to add any tweaks/fixes needed.

I have never used the BumbleBee Project, so I can not say if there will be a conflict. 

As for steam, I run it under Wine, and I haven't run into any issues yet.

A howto can be found here. [https://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu](https://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu)

Hope this helps.

---

### Post by uylug on 2012-06-12
> **nj_peeps said:**
> I have been running the Nvidia closed source drivers for years now, and have not had any issues.  (currently on 295.40)  To install, you need to stop your X server and window manager.  Log out of your current GUI session.  and press Ctl-Alt-F1, this will bring you to console session.  Login as your self and run.
```
sudo service lightdm stop
```This will stop all the X server, and all other graphics. Then run the the nvidia driver file (must be done as root) ```
sudo sh NVIDIA-Linux-x86_64-295.53.run
```I have always had the Nvidia setup backup and edit the xconf.org file, and then gone back and edited it to add any tweaks/fixes needed.

I have never used the BumbleBee Project, so I can not say if there will be a conflict. 

As for steam, I run it under Wine, and I haven't run into any issues yet.

A howto can be found here. [https://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu](https://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu)

Hope this helps.

Exactly this.

Just download the file, stop the graphical interface and simply execute the installer. Works like a charm and you don't have to start messing with packages and stuff.

---

### Post by Welly Wu on 2012-06-12
Just in case this does not work and I can not load the Unity 3D desktop environment, how do I reverse the changes that I am about to make back to the original configuration?

---

### Post by Welly Wu on 2012-06-12
I followed the directions and I got more error messages:

1. Both the Nvidia 295.53 and 295.59 Linux 64 bit graphics drivers told me that I did not have a supported Nvidia GPU installed and it gave me a warning.

2. Both the Nvidia 295.53 and 295.59 Linux 64 bit graphics drivers pre-installation shell scripts failed to load properly and it asked me if I want to continue. I clicked cancel and I aborted the installation.

What is the problem?

What should I do?

I think it is due to the fact that the Nvidia 295.53 Linux 64 bit graphics driver does not support Nvidia Optimus technology. Remember, Nvidia does not officially support Optimus technology in GNU/Linux distributions. This is why the Bumblebee Project was created to create a temporary workaround for notebook PC owners that have Nvidia GPUs and Nvidia Optimus technologies until Nvidia Corporation finalizes the software code and the legal support regarding the GNU Public License to support Optimus technology in GNU/Linux distributions.

---

