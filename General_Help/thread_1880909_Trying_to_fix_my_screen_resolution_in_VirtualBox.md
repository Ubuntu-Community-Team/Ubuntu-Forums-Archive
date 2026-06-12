---
title: "Trying to fix my screen resolution in VirtualBox"
date: 2011-11-14
forum: General Help
---

### Post by Mollering on 2011-11-14
I have Kubuntu 11.10 installed on VirtualBox (latest version). Host OS is Win7.
The problem is the screen resolution... The Kubuntu settings do not allow the 1280x800 screen resolution, I mean, that setting doesn't exist...

But I really need that res, any suggestion?

---

### Post by gmargo on 2011-11-14
While I haven't used Win7 as the host, in general you should install the virtualbox guest utilities to improve host-guest interaction. 

Try installing these three packages (on the Kubuntu guest).  After rebooting the guest, you should be able to resize the window at will.

virtualbox-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-guest-x11 - x86 virtualization solution - X11 guest utilities

---

### Post by haqking on 2011-11-14
> **gmargo said:**
> While I haven't used Win7 as the host, in general you should install the virtualbox guest utilities to improve host-guest interaction. 

Try installing these three packages (on the Kubuntu guest).  After rebooting the guest, you should be able to resize the window at will.

virtualbox-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-guest-utils - x86 virtualization solution - non-X11 guest utilities
virtualbox-guest-x11 - x86 virtualization solution - X11 guest utilities

just go to devices menu, choose virtual box additions, it mounts the iso and install then restart the VM

---

### Post by leugi101 on 2011-11-14
when i installed windows xp in virtualbox there wasnt a perfect resolution for my screen, but once i installed the guest additions it automatically detected my screen resolution.

---

### Post by Mollering on 2011-11-14
Yap, you were correct. It's solved now, thanks!

---

### Post by haqking on 2011-11-14
> **Mollering said:**
> Yap, you were correct. It's solved now, thanks!

cool, remember to use thread tools to mark the thread as solved.

Cheers

---

