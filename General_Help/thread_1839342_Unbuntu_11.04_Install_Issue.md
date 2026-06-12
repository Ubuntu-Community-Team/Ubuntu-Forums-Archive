---
title: "Unbuntu 11.04 Install Issue"
date: 2011-09-05
forum: General Help
---

### Post by LMNUCOHEN on 2011-09-05
I have the Desktop installer CD for Ubuntu 11.04. My system is an HP Envy 17 3D. My current host OS is Windows 7 Professional.

When I run Ubuntu from the CD, all seems OK; in particular the default graphics user interface (GUI) properly displays.

However I then tried to install Ubuntu 11.04 on a virtual machine as a guest OS (VM Ware VM Workstation 7.1.4). In this case the GUI did not display and I had only a text-based command prompt screen.

It would seem that my display system is compatible because running from the CD displayed the GUI.

Any thoughts about why the GUI did not appear when installed on a virtual machine?

---

### Post by e79 on 2011-09-05
I was never able to get Unity working in VMware workstation as 3d effect is not supported. I was only able to get it in VirtualBox. sometime after installing the 'Guest Additions'  (same as VMware Tools but for VirtualBox) on the virtual machine.

But your installation should only have warned you that your machine could not display Unity and should have fall back to Gnome2 immediately...

Running Ubuntu from the LiveCD on your host computer use your real hardware, as opposed to an virtualization software use another layer which can't emulate the 3d properly for now (that's why most Windows games won't run in a virtual machine)

So if you only see command line after installing it in a virtual machine, I'd say that something went wrong or you do not have the 'VMware Tools' installed.

Just some thoughts

---

