---
title: "Using GRUB to inject custom DSDT table?"
date: 2011-06-12
forum: General Help
---

### Post by mdmayfield on 2011-06-12
Hi all,

I'm trying to use this process:

[http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/](http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/)

to debug some laptop issues using custom DSDT tables. Intel's compiler iasl shows lots of errors, which I have now fixed. I'd like to use the modified tables without recompiling the kernel.

Nothing seems to happen when I use the method outlined in the blog link, though. What might I be missing, and should I be able to see anything is dmesg if it works?

Thanks,

Matt

---

### Post by drs305 on 2011-06-12
When you run update-grub do you see "Found custom ACPI Table" as the command is run in terminal? That means at least the script is being added to the grub configuration file (/boot/grub/grub.cfg). 

If you don't see that message, make sure the script is executable in /etc/grub.d

I don't know if the script will do what the author states; I'm only commenting on how additional scripts are incorporated into Grub 2.

---

### Post by mockingbird on 2011-06-12
No, you have to recompile and specify the new file in the menuconfig.  Including in Grub was only possible with less newer kernels.

---

### Post by mdmayfield on 2011-06-12
> **mockingbird said:**
> No, you have to recompile and specify the new file in the menuconfig.  Including in Grub was only possible with less newer kernels.

Are you sure this is true of GRUB? I know that the option to use initrd for this purpose was removed from the kernel, but as far as I have read, this is a different method that should be unaffected by the kernel version.

---

### Post by mdmayfield on 2011-06-13
I've downloaded the kernel source and built a .HEX file in C format of the corrected DSDT. So far I'm not finding many resources on how to either compile the DSDT directly into the kernel, or patch the kernel so I can boot with acpi injection.

Are there any resources you can point me to?

Thanks,

Matt

---

### Post by psusi on 2011-06-13
When you build the kernel there is an option in the menuconfig to specify a file to use for the dsdt.

---

### Post by mdmayfield on 2011-06-13
Got it. Thanks! Make is running now; first time compiling a kernel. How exciting.

---

