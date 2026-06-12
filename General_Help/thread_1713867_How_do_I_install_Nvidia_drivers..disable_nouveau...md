---
title: "How do I install Nvidia drivers..disable nouveau..StopX???"
date: 2011-03-24
forum: General Help
---

### Post by schwabdale on 2011-03-24
Hello all,
I'm pretty new to Linux and I need help installing a Nvidia Driver. 
This is on a Desktop (Dell Dimension E521). Its a PCIE Card called 
Nvidia Geforce 210 (EVGA). 

The problem I'm having is the sound will not come out of the HDMI port. I have a support ticket opened with Nvidia,,, but they take forever to get back to me. 

I try to download the driver to the desktop... Then I hit CTRL+ALT+F1.. This brings me to a command prompt. Then I type sudo /etc/init.d/gdm stop

After that I type cd Desktop (Where I saved the file) 
Then "chmod +x nvidia.run && ./nvidia.run

After the install I just get back to a command prompt. So I try to reboot and I still end up at the command prompt. 

Pleeeese help. This is very annoying. I really need a step by step how to. 

Thanks in advance

---

### Post by schwabdale on 2011-03-25
b

---

### Post by Frogs Hair on 2011-03-25
Did you attempt to install drivers from System> Administration > Hardware/ Drivers or did only try from the Nvidia website. The driver jokey is by far the easiest way to install drivers. [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by schwabdale on 2011-03-25
> **Frogs Hair said:**
> Did you attempt to install drivers from System> Administration > Hardware/ Drivers or did only try from the Nvidia website. The driver jokey is by far the easiest way to install drivers. [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)


Yes, and it gives me the video...just no sound. So tech support from Nvidia says I need to 
install the official driver. But,, thats seems out of my ability. I try to stop X and then Install the driver but can't start x when its done.

---

