---
title: "VGA out working, but not HDMI out"
date: 2012-03-28
forum: General Help
---

### Post by cyberjar09 on 2012-03-28
Hi all, 

I have a peculiar problem as described below:

I am installing Ubuntu 10.04 (LTS) on multiple machines and encountered that most of them are working with HDMI out but a few dont. All the machines on which I am performing the installation are exactly identical. On these machines where HDMI does not work, the VGA out works, but that is not an option due to other reasons. 

Exact problem could be described as follows: 
Machine boots, POST is seen, RAM test passed, proceeds to boot Ubuntu. When Ubuntu is booting, the monitor looses signal. 

On the machines on which the HDMI out din't work, I tried looking into the BOIS but found nothing different. I also tried to switch the hard drives with one where HDMI is working to ascertain that the fault is actually in the hardware. 

Right, so im sure at this point that the HDMI out is giving trouble. So I tried inserting a Windows hard drive into the machine, and viola!, the damn HDMI works in the OS environment. Now why on 2 identical machines, would HDMI out work on one and not another in Ubuntu? 

Here is the info of the graphics controller
intel corporation mobile series 4 chipset integrated graphics controller (rev 07)

The proprietary drivers don't show anything for me to install and I dont even know the location of the installed intel drivers to report that they are not functioning. 

Please help...

---

### Post by cyberjar09 on 2012-03-28
*bump*

---

### Post by cyberjar09 on 2012-03-29
Im poking around a little more trying to find some answers but thing yet. 

I did find the following:
The package containing the graphics driver in the kernel is called "xorg-server-video-intel" and it is up to date. 

I tried to download the latest drivers from intel ([http://www.intel.com/p/en_US/embedded/hwsw/software/emgd?iid=3747]("http://www.intel.com/p/en_US/embedded/hwsw/software/emgd?iid=3747")) but the download file only returns me the Windows installer. 

No idea how to proceed now.

---

### Post by varunpr97 on 2012-03-29
> **cyberjar09 said:**
> Im poking around a little more trying to find some answers but thing yet. 

I did find the following:
The package containing the graphics driver in the kernel is called "xorg-server-video-intel" and it is up to date. 

I tried to download the latest drivers from intel ([http://www.intel.com/p/en_US/embedded/hwsw/software/emgd?iid=3747]("http://www.intel.com/p/en_US/embedded/hwsw/software/emgd?iid=3747")) but the download file only returns me the Windows installer. 

No idea how to proceed now.

do you have a sandy bridge CPU? Try precise.. it has the 3.2 kernal- maybe the issue are addressed there... if you want gnome classic then install gnome fallback. A lot of work has been put into it upstream by the gnome devs to make the experience better

---

