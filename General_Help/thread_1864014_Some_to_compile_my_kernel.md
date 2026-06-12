---
title: "Some to compile my kernel"
date: 2011-10-18
forum: General Help
---

### Post by Blasphemous on 2011-10-18
In the last 3 weeks I've been trying to compile my custom kernel, but invain.
I got at least 50 kernel panics in doing it, and now I'm here looking for help.

My question is: **is it possibile to compile a kernel on a computer, while having in mind another computer specs, removing all the useless, and finally install the .deb on the secondo PC?**

I was thinking about giving my **PC specs** and **hardware list** to someone **more experienced** than me, who is able to** remove all the removable** and than [B]give the deb back to me...

[/B]so, is it possibile?
Do you guys know any site where I can find a person like that?
I understand how pathetic is that, but I swear it is my last resort...

---

### Post by hwttdz on 2011-10-18
Installing a deb, no, but theoretically you can compile a kernel for computer b on computer a, drop it in /boot and run update-grub.  

I'd disconnect any disks that you have attached to your machine, put in a new one and follow the instructions in the debian handbook, it walks you through booting into a minimal working system to bootstrap a kernel build.  And as your original disks aren't attached no possibility of accidentally overwriting data on those.

---

### Post by flangemonkey on 2011-10-18
using make menuconfig, the config is saved to a file called .config in your /usr/src/linux directory (presuming that you symlink your kernel source directory to /usr/src/linux)

this file can be created on any computer and then copied onto yours, a .deb wouldn't work in this sense, but could be done, although as it's just the one file, I wouldn't bother.

sepcific versioning isn't important either, ideally the two computers should have the same kernel version, eg 3.0.0 but as long as you run make menuconfig with the new .config file in place on your computer, any incompatibilities should be overwritten when you save.

if anything in this post confuses you, then I would read more on linux before trying to compile a custom kernel on a distro that doesn't support it, or try Gentoo where the handbook walks you through kernel compilation as part of the install.

hth

FM

---

