---
title: "nvidia broken following kernel update?"
date: 2012-06-15
forum: General Help
---

### Post by pmains on 2012-06-15
I have an Ubuntu laptop, which I use with a second monitor via a docking station. The laptop, dock and external monitor are all Dell products. After accepting updates from update-manager this morning, which included a kernel update plus the subsequent reboot, my external monitor was no longer automatically used by Ubuntu (in addition to the monitor built into the laptop).

At least since installing 12.04, I have been using NVIDIA X Server Settings to switch between single and dual monitor mode. However, now when I open NVIDIA X Server Settings I get the following message.

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I ran nvidia-xconfig and ran "restart lightdm" as root and using sudo. Neither fixed the issue. I have rebooted the computer. That didn't solve the problem.

I tried copying an old xorg.conf file that I had backed up while using 11.10 over /etc/X11/xorg.conf and restarting lightdm. That doesn't work, either.

Should I be purging reinstalling NVIDIA related packages? How do I get past this issue?

---

### Post by Redblade20XX on 2012-06-15
I think you have to rebuild the NVIDIA module and reinsert it into the kernel. In other words, reinstall the driver through the NVIDA package.

-Red

---

### Post by firekage on 2012-06-16
> **Redblade20XX said:**
> I think you have to rebuild the NVIDIA module and reinsert it into the kernel. In other words, reinstall the driver through the NVIDA package.

-Red

Can you post how to do it?

---

