---
title: "Upgrading to Lucid Lynx - Broken Graphics"
date: 2010-05-01
forum: General Help
---

### Post by naxtek on 2010-05-01
Hi,

I upgraded to Lucid Lynx on Friday when it was released.

On the first reboot, Ubuntu said it was going into 'Basic Graphics Mode' and gave an error message stating that it couldn't initialise the graphics card.

I have tried reinstalling the nvidia drivers, also tried deleting xorg.conf but neither of these things worked.

Any ideas?  This is really bugging me.  Would a fresh install fix it?

Specs (if it helps)
PCI-Express GeForce 8600GT
Intel C2D 2.6GHz overclocked to 3 GHz
2GB RAM

Thanks,
Andrew

---

### Post by naxtek on 2010-05-01
Error message as below:

Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to solve this.

(EE) May 01 21:00:52 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) May 01 21:00:52 NVIDIA(0): Please check your system's kernel log for additional error
(EE) May 01 21:00:52 NVIDIA(0): messages and refer to Chapter 8: Common Problems in the
(EE) May 01 21:00:52 NVIDIA(0):  README for additional information.
(EE) May 01 21:00:52 NVIDIA(0):  Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

---

### Post by jbirdjavi on 2010-05-05
I have a very similar problem to naxtek.  I'm running Mythbuntu and encountered the same error after upgrading to 10.04.  I've tried blacklisting nouveau and installing the proprietary driver from the Nvidia website but I encounter the same error on the screen as naxtek does whether I use nvidia-current or the driver from Nvidia's website.

My system log shows this:
```

[    9.645679] nvidia: module license 'NVIDIA' taints kernel.
[    9.645684] Disabling lock debugging due to kernel taint
[   10.743662] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   10.743668] nvidia 0000:00:12.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22
[   10.743674] nvidia 0000:00:12.0: setting latency timer to 64
[   10.743678] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   10.744030] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010

[   23.513063] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   23.513491] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   23.513496] NVRM: rm_init_adapter(0) failed
[   23.783422] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   23.783856] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   23.783861] NVRM: rm_init_adapter(0) failed
[   24.078450] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   24.078883] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   24.078888] NVRM: rm_init_adapter(0) failed
[   24.384731] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   24.385241] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   24.385247] NVRM: rm_init_adapter(0) failed
[   24.624980] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   24.625413] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   24.625418] NVRM: rm_init_adapter(0) failed
[   24.913940] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
[   24.914406] NVRM: RmInitAdapter failed! (0x23:0xffffffff:655)
[   24.914412] NVRM: rm_init_adapter(0) failed

```

Since it said something about screens, I've tried using a different monitor with VGA output (I usually use TV out), but same thing.  I have an NVIDIA GeForce 7050PV/nForce 630a.

And for good measure, here's my xorg.conf:
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

If anyone can give me any help I'd definitely appreciate it!

---

### Post by gravies on 2010-05-13
I have the same problem.  

Enabled with jockey. Rebooted. Nouveau blacklisted and not loaded.  nvidia module loads. nvidia-xconfig makes no difference.  Same thing with fresh install and on USB stick.  TV / LCD makes no difference - tried 2 very different ones.  System was working perfectly with nvidia 
drivers on karmic.  

> 
 [ 1023.904815] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
 [ 1023.904826] NVRM: rm_init_adapter(0) failed
 WARNING: GdmDisplay: display lasted 0.904341 seconds


> 
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)


> (**) May 13 21:19:45 NVIDIA(0): Enabling RENDER acceleration
(II) May 13 21:19:45 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 13 21:19:45 NVIDIA(0):     enabled.
(EE) May 13 21:19:45 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) May 13 21:19:45 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) May 13 21:19:45 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) May 13 21:19:45 NVIDIA(0):     README for additional information.
(EE) May 13 21:19:45 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by gravies on 2010-05-13
Looks like I might have found a fix from this page:

[http://ubuntuforums.org/showthread.php?t=1125400&page=32](http://ubuntuforums.org/showthread.php?t=1125400&page=32)

I followed the instruction about adding  vmalloc=192M to the end of "GRUB_CMD_LINE_LINUX_DEFAULT" in /etc/default/grub and now I have nvidia 195.36.15 working after a reboot (so far!).

---

### Post by jbirdjavi on 2010-05-13
Score!  You rock, gravies!  Since I'm on grub 1 still, I had to modify /boot/grub/menu.lst, but that did it.  Thanks!

---

