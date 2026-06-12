---
title: "USB Not Recognized in Virtualbox"
date: 2011-10-22
forum: General Help
---

### Post by mihalybaci on 2011-10-22
I can't figure out how to get Windows XP SP3 in Virtualbox to read my USB stick. I found a few other posts on the subject with no luck. One post recommended recompilin the VB kernel (which didn't work) and my login user has all the needed permissions for VB. If it helps, I'm running Lucid (10.04), Virtualbox 3.2.8 (most up-to-date in repositories), and I have installed the VM Guest Additions. What am I missing?

Thanks for any help.

---

### Post by northd_tech on 2011-10-23
It sounds like another guy had success with WinXP under VirtualBox with the VB extensions.  Take a look at this thread in the Virtualization sub-forum:

VirtualBox remote USB
[http://ubuntuforums.org/showthread.php?t=1865930](http://ubuntuforums.org/showthread.php?t=1865930)

It sounds like his remote setup is more complicated that what you (and I) are probably trying to do with VirtualBox and USB.

---

### Post by 3rdalbum on 2011-10-23
Here's a quick checklist:

1. Are you using the proprietary version of Virtualbox or the open-source edition? The open-source edition does NOT have USB support.

2. Have you used the Virtualbox settings to actually turn on the USB support and allow it to "passthrough" that USB device?

3. Is the device mounted in the host OS? If so, it needs to be unmounted.

4. When I say "unmounted", I mean use the "Eject" or "Unmount" option. DO NOT use "Safely remove hardware" as this actually switches off the USB device.

---

### Post by mihalybaci on 2011-10-23
Yes, I am using the OSE version. Not too long after I posted this question, one of my friends gave me a tip to just uninstall the VB 3.2.8 using Synaptic and install the latest version (4.0.14). I had considered that, but didn't want the hassle of reloading XP. But, my friend enlightened me to the fact that the OS gets saved as a .vdi file in the ~/.VirtualBox folder. So I was able to upgrade to the new VB OSE, without destroying my virtual OS. Then the new VB has a "USB" device option that can simply be enabled. 

Thanks for the quick replies!

---

### Post by oldtimer7777 on 2011-10-23
I have the same problem with Virtualbox. A friend of mine recommended to install VMWare player instead, and I can now access my usb devices virtualized. 

Here is a link to VMWARE so you can install it and try it:

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

> **mihalybaci said:**
> I can't figure out how to get Windows XP SP3 in Virtualbox to read my USB stick. I found a few other posts on the subject with no luck. One post recommended recompilin the VB kernel (which didn't work) and my login user has all the needed permissions for VB. If it helps, I'm running Lucid (10.04), Virtualbox 3.2.8 (most up-to-date in repositories), and I have installed the VM Guest Additions. What am I missing?

Thanks for any help.

---

