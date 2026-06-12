---
title: "Need help exporting a VirtualBox machine from laptop to PC (WIRELESS)"
date: 2012-05-17
forum: General Help
---

### Post by rugbert on 2012-05-17
So I simply copied and pasted some VMs (VirtualBox) from my laptop to my PC but I cant run either of them. Whenever I try I get the following error:
> Failed to open/create the internal network. 'HostinterfaceNetworking-wlan0' (you might need to modprobe vboxnetfit to make it accessible)
(VERR_OMTMET_FLT_IF_NOT_FOUND).

So I guess the problem is that my VM was created using a wireless adapter which my PC does not have.

Im running Ubuntu 12.04 32 bit

---

### Post by dabl on 2012-05-17
I'm a VMware user, but I have used VBox in the past.

Can you temporarily connect your laptop to your ethernet network with a cable?  Or if not, do you have a hard disk drive with enough free space that you could temporarily connect to the laptop?  Because I think what you'll need to do is change the network interface on the laptop VM first, then copy it over to the PC.

---

