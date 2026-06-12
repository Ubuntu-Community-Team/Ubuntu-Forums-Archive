---
title: "Windows 7 No Longer Works in VirtualBox"
date: 2011-01-12
forum: General Help
---

### Post by alohanate on 2011-01-12
I installed virtualbox a couple of days ago and had used Windows 7 (guest) multiple times without an problems.  However, upon attempting to share folders, it will no longer boot and I get this error:

p, li { white-space: pre-wrap; } "Failed to open a session for the virtual machine Windows 7.
 The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1."
Details:
p, li { white-space: pre-wrap; }    Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  Machine
   Interface: 
  IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

p, li { white-space: pre-wrap; } 
Followed by this error:

p, li { white-space: pre-wrap; } Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.


How do I fix this?




Thanks!

---

### Post by Bitrate on 2011-01-12
Try reinstalling VirtualBox and run the guest additions again.

---

### Post by alohanate on 2011-01-12
I removed virtualbox then installed it again.  Still the same message.

---

### Post by ionFreeman on 2011-01-15
Install VirtualBox 4 from the Oracle web site.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Synaptic/Ubuntu Software Center tries to sell you on VirtualBox 3, but it doesn't seem to work with recent kernels. Or something. It doesn't matter what the problem is, but I had it, and I eventually struck upon the bright idea of seeing whether 4 was out of beta.

It is.

---

