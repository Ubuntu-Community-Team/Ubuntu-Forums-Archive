---
title: "Ubuntu running on VM does not login into GUI"
date: 2009-12-22
forum: General Help
---

### Post by kartiknatarajan on 2009-12-22
Hi All, 

I am running an Ubuntu in a VM. Due to shortage of space I wanted to delete some packages and after doing a dpkg -get--selections, I found Python and its dependent packages are occupying over 800MB of space and by mistake without realizing its purpose I ended up uninstalling the package. Since then I am not able to login to my Ubuntu in GUI mode and neither am I able to mount a USB drive so that I can back my data up before deleting the VM. I have some very important things stuck in there. 

Can you please help me with a way I can either restore my VM (by re-installing the deleted packages) or atleast take a backup of my data.

Many thanks

---

### Post by kartiknatarajan on 2009-12-22
Bump!

---

### Post by dcstar on 2009-12-22
> **kartiknatarajan said:**
> Hi All, 

I am running an Ubuntu in a VM. Due to shortage of space I wanted to delete some packages and after doing a dpkg -get--selections, I found Python and its dependent packages are occupying over 800MB of space and by mistake without realizing its purpose I ended up uninstalling the package. Since then I am not able to login to my Ubuntu in GUI mode and neither am I able to mount a USB drive so that I can back my data up before deleting the VM. I have some very important things stuck in there. 

Can you please help me with a way I can either restore my VM (by re-installing the deleted packages) or atleast take a backup of my data.

Many thanks

Log into it in text mode (as with any system where the GUI is not functional) and reinstall the packages using apt-get.

It is irrelevant that it runs in a VM, just do what others have had to do in similar circumstances (there are already many posts in the forums on this).

---

