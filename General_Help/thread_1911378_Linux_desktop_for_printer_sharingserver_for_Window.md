---
title: "Linux desktop for printer sharing/server for Windows computers"
date: 2012-01-18
forum: General Help
---

### Post by aEx155 on 2012-01-18
For a while I've had a Windows desktop serve as a sort of "print server" so that I can share a USB printer among the computers in the house by putting them all in the same workgroup.

Recently the Windows installation on the desktop malfunctioned so I booted into the Linux partition that was on there also. Unfortunately, I never found out how to share the USB printer from the Linux desktop.

We ended up buying a network printer previously so having to share the printer isn't so much a necessity anymore, but it's "less efficient" to have to print something from upstairs and pick it up downstairs. The ideal solution is to be able to pick from whichever printer is more convenient.

I do intend on re-installing Windows so that it functions but I'd like to keep Linux as its main OS (specifically, Lubuntu unless someone has a better distro) Besides its function as connecting the USB printer to the network, I will also use it to host a small Minecraft server.

Long story short: How would I go about making the USB printer connected to the Linux desktop visible to Windows computers?

---

### Post by SteveDee on 2012-01-19
> **aEx155 said:**
> ...How would I go about making the USB printer connected to the Linux desktop visible to Windows computers?

I've had a Lubuntu headless print server running for some time, but it no longer has any Windows clients that it needs to support.

I can't remember how I installed it, but it looks like you will need:-
system-config-printer-gnome (to provide a GUI)
system-config-printer-common
cups
...and any dependencies highlighted in Synaptic.

I also have Samba installed (see: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba))

...maybe this is some help.

---

