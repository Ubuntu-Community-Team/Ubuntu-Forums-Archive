---
title: "Grub problems"
date: 2012-01-22
forum: General Help
---

### Post by Lockheed on 2012-01-22
My grub (not grub2) seems to be ignoring some of the options I give it in kernel loading line. Here's an extract:

```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 


timeout   2
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

## additional options to use with the default boot option, but not with the
 ## alternatives
 ## e.g. defoptions=vga=791 resume=/dev/hda5
 # defoptions=quiet acpi_enforce_resources=lax
 # kopt=quiet acpi_enforce_resources=lax
 
# (0) Arch Linux
title  Arch
root   (hd0,2)
kernel /vmlinuz26 acpi_enforce_resources=lax resume=/dev/sda2 resume_offset=1748992 ro quiet vga=785 sr0=ide-scsi root=/dev/sda2
initrd /kernel26.img


# (2) Windows
title Windows
rootnoverify (hd0,3)
makeactive
chainloader +1

```

The two main issues I have with it are:
1. 'quiet' takes no effect. My boot screen is absolutely littered with useless verbose messages, each displayed with it's own millisecond value (time since boot).
2. 'acpi_enforce_resources=lax' which is supposed to enable lm_sensors to display voltages, does not work, either. I still am unable to see any Voltage values

---

### Post by dcstar on 2012-01-23
> **Lockheed said:**
> My grub (not grub2) seems to be ignoring some of the options I give it in kernel loading line. Here's an extract:
..........

So why are you posting a question about Arch Linux in the Ubuntu forums?

---

### Post by Lockheed on 2012-01-23
Because they can't help me. Linux is linux, no?

---

