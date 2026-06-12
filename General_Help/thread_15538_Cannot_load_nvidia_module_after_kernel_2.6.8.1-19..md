---
title: "Cannot load nvidia module after kernel 2.6.8.1-19.11 upgrade"
date: 2005-02-15
forum: General Help
---

### Post by jumahu on 2005-02-15
I used Synaptic to upgrade to new kernel in warty. After rebooting to load the new one, X it doesn't start.

If I try to load the kernel module with "sudo modprobe nvidia" I get an error message that it can't find the module.

I had installed the nvidia drivers as appear in the "BinaryDriverHowto" article from the fresh warty installations and it worked well in  the different kernel upgrading until now.

So I have to boot with the previous kernel when grub is loaded.

Any Idea?

---

### Post by s.deleeuw on 2005-02-15
The linux-restricted-modules-2.6-686 linux meta package is broken. It depends on the non-existing package linux-restricted-modules-2.6.8.1-5-686. The NVIDIA/ATI drivers are included in this package, so they are not installed for this kernel. That's why your nvidia enabled X configuration won't do anymore. I assume this will be fixed soon, but in the meanwhile you can use the "normal" nv driver instead of nvidia's, by changing the following lines in your XF86Config

Section "Device"
        Identifier      "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
#        Driver          "nvidia"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

(or boot your old kernel, if you havn't removed these packages manually)


Sander

---

### Post by arrizaba on 2005-02-16
I've got exactly the same problem. I do as Sander suggested but I only get a blank screen with the X mouse icon. Do you know if the GPL module is causing the problem? Any help is welcome  :?

---

### Post by Xian on 2005-02-16
[QUOTE=arrizaba]I've got exactly the same problem. I do as Sander suggested but I only get a blank screen with the X mouse icon. [/QUOTE]
The upgraded linux-restricted-modules package is in the repo now so try installing that first to see if you can get back into an Xsession. If not, your previous kernel is still on your system unless you for some reason told apt to remove that version. You can always boot your system using the prior kernel and initrd files.

---

### Post by jumahu on 2005-02-17
All is working well again, I've Installed the new upgraded linux-restricted-modules package and nvidia-glx upgrade.

Thanks

---

### Post by arrizaba on 2005-02-17
I'll try to do that as well as soon as I get back to my laptop with Ubuntu at home. Thnx Xian.  :-P

---

