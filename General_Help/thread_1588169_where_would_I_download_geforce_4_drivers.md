---
title: "where would I download geforce 4 drivers?"
date: 2010-10-04
forum: General Help
---

### Post by Dustin2128 on 2010-10-04
I need to get the linux drivers for my geforce Ti 4200. Ordinarily, this wouldn't be a problem thanks to the hardware drivers manager in ubuntu and mint, but this machine has no net connection. From what I've read, graphics cards older than the FX series were relegated to a legacy driver status, and I can't find any download links for the geforce 4 series on nvidia's site. Where would I download the driver (to stick it on a flash drive and install it)?

---

### Post by andrewthomas on 2010-10-04
WARNING: The NVIDIA GeForce4 Ti 4200 with AGP8X GPU installed in this system
is supported through the NVIDIA 1.0-96xx legacy Linux graphics
drivers. Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
more information.


[http://www.nvidia.com/object/linux_display_amd64_1.0-9639.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9639.html)

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)

---

### Post by Dustin2128 on 2010-10-04
> **andrewthomas said:**
> WARNING: The NVIDIA GeForce4 Ti 4200 with AGP8X GPU installed in this system
is supported through the NVIDIA 1.0-96xx legacy Linux graphics
drivers. Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
more information.


[http://www.nvidia.com/object/linux_display_amd64_1.0-9639.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9639.html)

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)
thanks, looks like it was just what I was looking for. Be back after install.
Something I've always wondered though, why is it that there are proprietary drivers? It seems like one of those niches where it doesn't matter if a piece of software is free or not.

---

### Post by Dustin2128 on 2010-10-04
OK, now its refusing to work (even when I ctrl-alt-F1) because I have X open in the background. How do I login without starting x, or kill it from the terminal?

---

### Post by andrewthomas on 2010-10-04
press e at the grub screen and  remove quiet splash add single to the linux line

---

### Post by Mark Phelps on 2010-10-04
> **Dustin2128 said:**
> ...Something I've always wondered though, why is it that there are proprietary drivers? It seems like one of those niches where it doesn't matter if a piece of software is free or not.

It's not a matter of "free"; it's a matter of access to the source.

Companies like Nvidia and AMD/ATI spend a lot of time and dollars developing custom drivers for their products.  By making these drivers proprietary, they don't have to publicly release the source code.  Thus, they view this as protecting their "intellectual property".

---

### Post by Dustin2128 on 2010-10-04
> **Mark Phelps said:**
> It's not a matter of "free"; it's a matter of access to the source.

Companies like Nvidia and AMD/ATI spend a lot of time and dollars developing custom drivers for their products.  By making these drivers proprietary, they don't have to publicly release the source code.  Thus, they view this as protecting their "intellectual property".
free as in freedom, e.g. open source. Meh, nevermind, topic for another thread.

---

### Post by Dustin2128 on 2010-10-04
> **andrewthomas said:**
> press e at the grub screen and  remove quiet splash add single to the linux line
EDIT: never mind, good 'ol ctrl-alt-backspace worked. *facepalm*
still going to have to download and transfer yet another dependency though. I thought that gcc was installed in almost every linux distro?

---

