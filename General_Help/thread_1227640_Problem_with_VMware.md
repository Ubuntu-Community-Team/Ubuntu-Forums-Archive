---
title: "Problem with VMware"
date: 2009-07-30
forum: General Help
---

### Post by dustinYo on 2009-07-30
First and foremost, I must say that I am relatively new to Ubuntu.  I've only been using it for several months now.
My problem is that, when trying to install VMware, I'm getting a message that says that my drive must have at least 554MB of free space for installation.
Of course, I've checked to make sure that I'm not running low on free space.  I've got roughly 60gb left on my hard drive.
I'm attempting to install it using Wine.

Can anyone help me sort out this problem?

---

### Post by SoftwareExplorer on 2009-07-30
A couple of things. First, I think that there is a native Linux VMware. I would be amazed if Windows VMware worked in wine because of how closely dependent such applications can be on hardware.  Second, have you checked out virtualbox? It is like VMware but runs on Ubuntu fine and is free.

---

### Post by philcamlin on 2009-07-30
vmware and virtualbox run on virtual filesystems that means when you vcreated your virtual hdd you made it too small :(

---

### Post by dustinYo on 2009-07-30
Actually, the reason I'm attempting to install VMware is for gaming, and as far as I've read VMware is the only virtual machine that supports 3D graphics, so VirtualBox isn't an option.

---

### Post by dustinYo on 2009-07-30
> **philcamlin said:**
> vmware and virtualbox run on virtual filesystems that means when you vcreated your virtual hdd you made it too small :(

Is there any way I can fix that?

---

### Post by SoftwareExplorer on 2009-07-30
> **philcamlin said:**
> vmware and virtualbox run on virtual filesystems that means when you created your virtual hdd you made it too small :(

Wouldn't that just a problem for the OS inside the Virtual Machine? I don't think that it would a problem when you are installing VMware. 

@dustinYo In that case use the native Linux version of VMware.

According to [this page]("http://www.vmware.com/download/ws/") there is, in fact, a native (doesn't use wine) version for Linux.

---

