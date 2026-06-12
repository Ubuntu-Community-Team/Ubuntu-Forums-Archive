---
title: "win7 on virtualbox"
date: 2011-10-06
forum: General Help
---

### Post by cowboy7305 on 2011-10-06
I have win7 on first partition of my hard drive and ubuntu 10.04lts on second partition ,if i run VB can i use the win7 on from first partition on it or do i still have to reload win7 via VB
any help please

---

### Post by Basher101 on 2011-10-06
you cannot load a partition using Virtualbox. As you can guess from the name it creates a **_*[COLOR="Red"]virtual[/COLOR]*_** partition and uses ***_[COLOR="Red"]virtual[/COLOR]_*** hardware components (like a virtual hard disc) so you cannot load windows 7 from the partition itself.

---

### Post by jespdj on 2011-10-06
When you make a virtual machine in VirtualBox, that virtual machine acts as a completely different virtual computer.

The OS that's running inside the virtual machine doesn't have direct access to the hardware. It's all managed by VirtualBox. That means that an existing Windows installation cannot run inside VirtualBox, because it will have drivers installed that expect to be talking directly to the real hardware, and not virtual hardware.

For example, the OS running in the virtual machine will not get direct access to the video card. If you have for example an NVIDIA video card, then the OS in the VM won't see that - instead it will see a special VirtualBox videocard. You won't be able to install the NVIDIA driver on the OS in the VM; instead, you'll need to install a driver for the VirtualBox virtual video card.

VirtualBox comes with "guest extensions", which provides these drivers. You install the guest extensions on the OS in the VM to make it work.

---

### Post by haqking on 2011-10-06
> **Basher101 said:**
> you cannot load a partition using Virtualbox. As you can guess from the name it creates a **_*[COLOR="Red"]virtual[/COLOR]*_** partition and uses ***_[COLOR="Red"]virtual[/COLOR]_*** hardware components (like a virtual hard disc) so you cannot load windows 7 from the partition itself.

> **jespdj said:**
> When you make a virtual machine in VirtualBox, that virtual machine acts as a completely different virtual computer.

The OS that's running inside the virtual machine doesn't have direct access to the hardware. It's all managed by VirtualBox. That means that an existing Windows installation cannot run inside VirtualBox, because it will have drivers installed that expect to be talking directly to the real hardware, and not virtual hardware.

For example, the OS running in the virtual machine will not get direct access to the video card. If you have for example an NVIDIA video card, then the OS in the VM won't see that - instead it will see a special VirtualBox videocard. You won't be able to install the NVIDIA driver on the OS in the VM; instead, you'll need to install a driver for the VirtualBox virtual video card.

VirtualBox comes with "guest extensions", which provides these drivers. You install the guest extensions on the OS in the VM to make it work.


Both wrong i am afraid.

You can mount can use an existing partition inside a virtual machine.

see this thread [http://ubuntuforums.org/showthread.php?t=1855152](http://ubuntuforums.org/showthread.php?t=1855152) where i have posted links on how to do so which are also following:

HOWTO: [https://forums.virtualbox.org/viewtopic.php?t=9697](https://forums.virtualbox.org/viewtopic.php?t=9697)
[http://lifehacker.com/278015/turn-a-...irtual-machine](http://lifehacker.com/278015/turn-a-...irtual-machine)
[http://www.rajatarya.com/website/tam...-virtualbox-vm](http://www.rajatarya.com/website/tam...-virtualbox-vm)

---

