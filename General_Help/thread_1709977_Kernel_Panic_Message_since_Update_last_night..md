---
title: "Kernel Panic Message since Update last night."
date: 2011-03-19
forum: General Help
---

### Post by Stylesmarino on 2011-03-19
Hi Folks.

I am getting this:

 **[######]Kernel panic - not syncing: VFS : Unable to mount root fs on unknow-block (0,0)**

When I switch on.
Its coming up after my BIOS screen but before the splash.
Can do nothing from there.

Only found it when switching on this morning having shut down after updating last night.
So I assume its a kernel update problem?

So I have little to no idea what to do here. The only thing that I seem to be able to do is going in to the BIOS set up before this occurs.

Dell 8600
BIOS A11
Ubuntu Lucid.

What in the name of Coffee do I do?

---

### Post by Stylesmarino on 2011-03-19
I'm bumping this because I am in the dark.
I ran a live cd of Lucid.

Here is the contents of /boot

> abi-2.6.32-24-generic          memtest86+.bin
abi-2.6.32-25-generic          System.map-2.6.32-24-generic
abi-2.6.32-26-generic          System.map-2.6.32-25-generic
abi-2.6.32-27-generic          System.map-2.6.32-26-generic
abi-2.6.32-28-generic          System.map-2.6.32-27-generic
abi-2.6.32-29-generic          System.map-2.6.32-28-generic
abi-2.6.32-30-generic          System.map-2.6.32-29-generic
config-2.6.32-24-generic      System.map-2.6.32-30-generic
config-2.6.32-25-generic      vmcoreinfo-2.6.32-24-generic
config-2.6.32-26-generic      vmcoreinfo-2.6.32-25-generic
config-2.6.32-27-generic      vmcoreinfo-2.6.32-26-generic
config-2.6.32-28-generic      vmcoreinfo-2.6.32-27-generic
config-2.6.32-29-generic      vmcoreinfo-2.6.32-28-generic
config-2.6.32-30-generic      vmcoreinfo-2.6.32-29-generic
grub                  vmcoreinfo-2.6.32-30-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-25-generic  vmlinuz-2.6.32-25-generic
initrd.img-2.6.32-26-generic  vmlinuz-2.6.32-26-generic
initrd.img-2.6.32-27-generic  vmlinuz-2.6.32-27-generic
initrd.img-2.6.32-28-generic  vmlinuz-2.6.32-28-generic
initrd.img-2.6.32-29-generic  vmlinuz-2.6.32-29-generic
initrd.img-2.6.32-30-generic  vmlinuz-2.6.32-30-generic

Can anyone see anything here?
Or at least suggest what I may be looking for?

Just thinking, should this be in "Installation and Upgrades"?
Could a mod Oblige me by moving it?
Thanks in advance.

---

### Post by Stylesmarino on 2011-03-19
Its definately the new kernel (2.6 .32.30)
I booted up an earlier kernel and it works.

Can anybody suggest how I might fix the new one?

---

