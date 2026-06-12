---
title: "Kernel compilation problems on Jaunty"
date: 2009-07-02
forum: General Help
---

### Post by aspa on 2009-07-02
Hi,

I'm trying to build a new kernel on a Ubuntu 9.04 Desktop Edition system (32-bit). The reason for doing this is that I'd like to be able to use all of the physical memory that's installed on the hardware.

I followed the instructions found in the [KernelCompile]("https://help.ubuntu.com/community/Kernel/Compile") page to compile a PAE-enabled kernel but for some reason the configuration changes I make seem to get overwritten when I regenerate or update the configs.

Here's the procedure I'm using:

[FONT="Courier New"]
[INDENT]sudo apt-get build-dep linux-image-2.6.28-13-generic
apt-get source linux-image-2.6.28-13-generic

# manually edit debian/config/i386/config.generic to add the following line:
# CONFIG_X86_PAE=y

chmod u+x debian/scripts/misc/*
bash debian/scripts/misc/oldconfig i386
[/INDENT][/FONT]

I've also tried creating my own config file (config.pae) and regenerating config files using:
[FONT="Courier New"][INDENT]debian/rules updateconfigs[/INDENT][/FONT]

but the PAE setting always gets lost from the config files.
I've also installed the kernel that I've built but it doesn't seem to be PAE-enabled.

Why do the config changes get lost?

If I use this procedure, will the resulting kernel have all the Ubuntu patches applied?

---

