---
title: "Anyone knows what GRUB does"
date: 2010-12-05
forum: General Help
---

### Post by LimaBeanss on 2010-12-05
Im a new user to Ubuntu and would like to know what 'GRUB' does

---

### Post by asmoore82 on 2010-12-05
GRUB = **[COLOR="Red"]Gr[/COLOR]**and **[COLOR="Red"]U[/COLOR]**nified **[COLOR="Red"]B[/COLOR]**ootloader

Every OS needs a bootloader to boot :lol:
But it must to be a tiny, self-contained program because it has to
run before the OS get to boot. And obviously failure is not an option.

What makes Grub particularly special is that it is capable of booting a
multitude of OS's and presents them in a nice menu. Another way of
classifying this ability is to say that Grub is a bootloader that can
even load other bootloaders.

It does, however, sort-of "cheat" to achieve this. It actually requires
installation in a partition on the hard drive. Strictly speaking, a
bootloader should only be in the boot sectors of the hard drive,
but there are no boot police. :p

The part of grub installed in your Linux partition is called "Stage 2."
The part of grub that's in the boot sectors has to be so tiny that it's
quite primitive and is "Stage 1." It's job is only to locate and load Stage 2
and to drop to a rescue prompt if it should happen to fail.

Stage 2 on a Linux system is installed in "/boot/grub/"

A common mistake is that folks who want to remove Linux and keep windows
just delete or format the Linux partition. This nukes Grub's Stage 2 and their
nice boot menu! Oops! ~time to re-install Linux or dig out the windows discs.

---

### Post by Immahazmacookie on 2010-12-06
GRUB is a bootloader for Ubuntu, it helps load the OS into the memory. GRUB is helpful as it is made for Linux, but the bootloader that came with your computer can also do the job if you don't want to install it.

---

### Post by asmoore82 on 2010-12-06
> **Immahazmacookie said:**
> GRUB is a bootloader for Ubuntu, it helps load the OS into the memory. GRUB is helpful as it is made for Linux, but the bootloader that came with your computer can also do the job if you don't want to install it.

I think you are confusing the bootloader with the BIOS.
The BIOS is embedded in the hardware and executes the bootloader.
Technically, the bootloader is always pure software.

The BIOS will load any bootloader it finds; but obviously,
the bootloader of a convicted monopolist wouldn't play well with others.

---

### Post by dcstar on 2010-12-06
> **LimaBeanss said:**
> Im a new user to Ubuntu and would like to know what 'GRUB' does

[https://secure.wikimedia.org/wikipedia/en/wiki/GNU_GRUB](https://secure.wikimedia.org/wikipedia/en/wiki/GNU_GRUB)

---

