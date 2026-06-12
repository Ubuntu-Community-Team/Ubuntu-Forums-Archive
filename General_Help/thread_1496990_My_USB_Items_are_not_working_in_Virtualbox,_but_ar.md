---
title: "My USB Items are not working in Virtualbox, but are not greyed out."
date: 2010-05-30
forum: General Help
---

### Post by Frozencurrent on 2010-05-30
So I have virtualbox with a fresh install of Windows XP running in it (no service packs) and when I plug in a USB Item it shows up on the device list and it is not greyed out, but nothing happens I cannot access the device through windows XP. It was greyed out before but then I logged in as root and started virtual box and it is not greyed out anymore but nothing happens when I plug in a USB item.

---

### Post by dcstar on 2010-05-30
> **Frozencurrent said:**
> So I have virtualbox with a fresh install of Windows XP running in it (no service packs) and when I plug in a USB Item it shows up on the device list and it is not greyed out, but nothing happens I cannot access the device through windows XP. It was greyed out before but then I logged in as root and started virtual box and it is not greyed out anymore but nothing happens when I plug in a USB item.

All VM questions should be in the Virtualization forum.

---

### Post by windfix on 2010-05-30
> **dcstar said:**
> All VM questions should be in the Virtualization forum.

Did you add USB "filters" for each device you want used in that VM prior to starting it?  Do this from the Settings section of Virtualbox prior to launching the VM

---

### Post by hok00age on 2010-05-30
> **Frozencurrent said:**
> So I have virtualbox with a fresh install of Windows XP running in it (no service packs) and when I plug in a USB Item it shows up on the device list and it is not greyed out, but nothing happens I cannot access the device through windows XP. It was greyed out before but then I logged in as root and started virtual box and it is not greyed out anymore but nothing happens when I plug in a USB item.

What version of VirtualBox you're using? PUEL or OSE? Check it via Help > About VirtualBox ...
You should use PUEL version to get full USB support

Regards :)

---

### Post by mcooke1 on 2010-05-30
Have you done this:- system>administration>users/groups>manage groups>vboxusers>properties>tick the box beside your name ?

---

### Post by Frozencurrent on 2010-05-30
Solved it, the problem was that Service Pack 2 was not installed and my computer is from the Vista era. It naturally did not have the adequate drivers to activate the USB HUB without Service Pack 2.

Thank you all for your help.

---

