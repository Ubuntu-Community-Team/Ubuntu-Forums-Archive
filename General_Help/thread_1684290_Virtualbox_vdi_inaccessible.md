---
title: "Virtualbox: vdi inaccessible"
date: 2011-02-08
forum: General Help
---

### Post by udarnick on 2011-02-08
I have been using Virtualbox for many years now without any issues.  I have a Windows7 vdi that has been working for about 6 months without any issues.  

Today I launched Virtualbox and the vdi said it was inaccessible.  I read some posts on how to fix it like running /etc/init.d/vboxdrv setup and modprobe vboxdrv, but neither of these commands seemed to help.

I will be happy to run any diagnostics you can suggest.  Any help would be appreciated.

---

### Post by mayhembg23 on 2012-06-03
Hello!
Today I think I experienced the same problem. As you can see on the picture attached, virtualbox advises me to create new disks, while the already existing become accessible... However I ignored the message and succeeded to operate with my virtual machines (with slower performance, but working).  

I was wondering should expect these machines to become accessible? And if yes when, why and how should I expect this? Anyone acquainted with VirtualBox, please help...

---

### Post by traditionalist on 2012-06-03
> **mayhembg23 said:**
> Hello!
Today I think I experienced the same problem. As you can see on the picture attached, virtualbox advises me to create new disks, while the already existing become accessible... However I ignored the message and succeeded to operate with my virtual machines (with slower performance, but working).  

I was wondering should expect these machines to become accessible? And if yes when, why and how should I expect this? Anyone acquainted with VirtualBox, please help...

That just means that something the Virtual Machine requires to run is not available to it. If you have a VM on another disk and have not mounted the disk you will get this. The same if you move or remove virtual disks ( isos).

---

