---
title: "Big problems with 11.1 server installation"
date: 2011-11-23
forum: General Help
---

### Post by 3dmaker on 2011-11-23
Hey guys, I just did a clean install of 11.1 onto my home server machine. I am having big trouble with it. After setting everything up, I can't seem to get the computer to run without turning on GDM. I installed the xubuntu-desktop package, and the xserver doesn't load right. I have tried this in 2 virtual machines, and after installing the xubuntu-desktop package on the VM they broke also. My monitor keeps getting an "out of range" error, and I can't seem to find a way to configure the new xserver. Also, I can't figure out a way for the machine to boot up without booting into xserver. I edited the /etc/default/grub file and set GRUB_CMDLINE_LINUX_DEFAULT to quiet and still no good. 

On my VM machines, everytime I type in startx it just start blinking like crazy untill I hit ctrl+c

Not sure what to do, I don't want to go back to a proper version of ubuntu, but this isn't working for me. 

Also, I compiled my own kernel, and when booting it says I need to add AppArmor support. I don't know what that is and would like to disable it

---

