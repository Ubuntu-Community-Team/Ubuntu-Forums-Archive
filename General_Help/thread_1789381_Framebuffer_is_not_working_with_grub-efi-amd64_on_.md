---
title: "Framebuffer is not working with grub-efi-amd64 on Natty Narwhal"
date: 2011-06-23
forum: General Help
---

### Post by fr_ank on 2011-06-23
Dear all,

I am struggling almost the entire day with getting framebuffer working on my fresh installed system.

I have a Intel DH67BL Mainboard and a Intel Pentium G620T CPU+IGP.

When I power on the system I can see this messages:

```
error: no suitable mode found
error: no suitable mode found
booting however
```

I have already tried a few things in /etc/default/grub.
Here are the actual settings:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="hpet=disable quiet reboot=a,w"
GRUB_CMDLINE_LINUX=""

GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=800x600
```

I have tested with GRUB_CMDLINE_LINUX_DEFAULT video=efifb:off and i915.modeset=1 and GRUB_GFXPAYLOAD_LINUX=keep and so on, but nothing worked for me.

After installation I saw this message, but only once:
```
htpc kernel: [    3.331602] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
```

```
root@htpc:~# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.ealWiwZz1JF
  Hardware Class: framebuffer
  Model: "Intel(R)Sandybridge Desktop Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Sandybridge Desktop Graphics Controller"
  SubVendor: "Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

```
root@htpc:~# dpkg --get-selections | grep -i grub
grub-common					install
grub-efi					install
grub-efi-amd64					install
```

dmesg shows the following:
```
dmesg | grep -Ei "(frame|fb)"
[    1.646604] Console: switching to colour frame buffer device 128x48
[    1.648510] fb0: inteldrmfb frame buffer device
```

I found some solutions for similar problems, but I had no luck:
- [https://wiki.archlinux.org/index.php/GRUB2#Correct_GRUB2_Video_Mode_problems_in_UEFI](https://wiki.archlinux.org/index.php/GRUB2#Correct_GRUB2_Video_Mode_problems_in_UEFI)
- [https://help.ubuntu.com/community/UEFIBooting#Selecting%20the%20%28U%29EFI%20Graphic%20Protocol](https://help.ubuntu.com/community/UEFIBooting#Selecting%20the%20%28U%29EFI%20Graphic%20Protocol)

Any hints?

---

### Post by srs5694 on 2011-06-23
My suggestion is to try a different boot loader. In my experience, GRUB 2 on UEFI systems is finicky and unreliable. IMHO, [ELILO](http://sourceforge.net/projects/elilo/) is much more reliable. There is an Ubuntu package, but I'm using a binary from the ELILO project. I don't recall offhand if the Ubuntu package installs directly to the EFI System Partition (normally mounted at /boot/efi) or elsewhere. If the latter, or if you download a non-Ubuntu version, you'll need to create a subdirectory in /boot/efi/EFI to hold the ELILO installation. You'll also need to copy your Linux kernel (such as /boot/vmlinuz-2.6.38-8-generic) and initial RAM disk (such as /boot/initrd.img-2.6.38-8-generic) into whatever directory you create for ELILO. You'll also need to create an ELILO configuration file. Mine looks something like this:

```

prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda4
        append="reboot=a,w"

```

This example boots the specified kernel, using the Linux root (/) filesystem on /dev/sda4. The "reboot=a,w" kernel option is required on my system or rebooting results in a kernel panic. Not all computers suffer from this bug, but a significant number do, no matter what boot loader is used.

Once you've set everything up, you should be able to use your board's firmware to select the new boot loader and set it as a default; or if your firmware is limited on that score, you can use the efibootmgr utility in Ubuntu.

Be aware that if you're dual-booting with Windows, ELILO can't redirect the boot process to another boot loader. Thus, you'll have to rely on either your firmware's built-in boot manager or another one, such as [rEFIt.](http://refit.sourceforge.net) You might not be able to use the rEFIt binaries from its site, though; those seem to be unreliable except on Macs. Ubuntu includes a rEFIt package with a purely 64-bit version that works on most non-Mac UEFI systems, although graphics are sometimes iffy. (You can uncomment a line in the configuration file to enable a text-mode display.)

---

### Post by fr_ank on 2011-06-24
Thank you for your answer, but after another day of struggle with this issue, I've had enough. 
I went back to grub-pc, because of my board is capable of both UEFI and "legacy".

---

