---
title: "Howto edit Kernel Boot Parameters?"
date: 2010-06-18
forum: General Help
---

### Post by held7over on 2010-06-18
Ubuntu 10.04 Gnome  IBM Thinkpad 600e.

I am trying to get sound going in my 600e which has the wrong chips in the sound card. I found some notes from 2008 that said in one of the steps to add the following to my kernel boot parameters:  noapci nolapci notsc acpi=off pnpbios=off pci=noacpi

It said to hit the Esc key when I see the Grub Count on boot up to get into the kernel boot parameter's editor. However, I am not seeing any Grub Count and pressing the Esc key every second during boot up doesn't seem to get me there either. 

I have been searching for how to edit the boot parameters but no luck so far.

How is this done? Thanks!

---

### Post by sisco311 on 2010-06-18
Hold down the Shift key during bootup, highlight the kernel, press e for edit, append the *linux* line with the kernel parameters & press Ctrl=x to boot.

---

### Post by drs305 on 2010-06-18
And once you find kernel options that work, to make them permanent add them to the end of this line (and whatever else you have there, such as *quiet splash*) in /etc/default/grub:
> GRUB_CMDLINE_LINUX_DEFAULT=

Don't forget to run "sudo update-grub" after saving the file.

---

### Post by held7over on 2010-06-18
Thanks! That should help a lot!

---

