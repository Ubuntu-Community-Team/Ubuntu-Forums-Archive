---
title: "Old Usb stick refusing to mount with &quot;daemon is inhibited&quot; message"
date: 2011-12-21
forum: General Help
---

### Post by blackbird34 on 2011-12-21
Hi 
Had this usb stick (kingston datatraveler usb 2.0, 2GB) for years, carried all sorts of stuff around with it (from Macs to Linuxes to Windows indiscriminately) and done several live usb runs and installs. Last distro on it was the latest fuduntu. 
I've been trying to open it recently but when i stick it in the usb port, it refuses to mount. It won't mount manually (right click > mount in nautilus side bar) or automatically, and it won't "safely remove drive" or "eject", it just gives a little "daemon is inhibited" message. 

How can i save it? 

Is there something like the /var/dpkg/lock on apt for preventing several package managers overriding each other like this 
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```to stop you mounting a drive while Gparted (for example) is working on it, that you can remove manually if necessary (due to malfunctioning)?

---

### Post by blackbird34 on 2011-12-22
bump...:(

---

### Post by plucky on 2011-12-22
What does ```
sudo fdisk -l
``` show you with the USB stick plugged in?

---

