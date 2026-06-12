---
title: "Help with MTRRs"
date: 2011-06-05
forum: General Help
---

### Post by gnaservicesinc on 2011-06-05
I am posting because I fixed a problem but don't really understand why the fix worked or what the problem really was and I am hoping to be able to learn something here. 

The problem was that on boot a problem with my GPU's driver's (Intel Z68 HD X3000) was being reported, a quick google search came up with a fix that "might" work. I tried it and it worked just fine, it was to add enable_mtrr_cleanup mtrr_spare_reg_nr=1 to grub's boot options. 

If you understand MTRRs can you help explain what is going on here or if you know of a good resource to learn more about them please share.

Thanks in advanced and here is some more info that may be of use to someone wishing to help:

Here is what is reported on boot now that the problem is fixed,

```
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8Z68-V PRO, BIOS 0501 05/09/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x42fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FC0000000 write-back
[    0.000000]   2 base 0C7800000 mask FFF800000 uncachable
[    0.000000]   3 base 0C8000000 mask FF8000000 uncachable
[    0.000000]   4 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   6 base 42FE00000 mask FFFE00000 uncachable
[    0.000000]   7 base 430000000 mask FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3192MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3200MB, range: 128MB, type UC
[    0.000000] reg 4, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 5, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 6, base: 17150MB, range: 2MB, type UC
[    0.000000] reg 7, base: 17152MB, range: 256MB, type UC
[    0.000000] total RAM covered: 16246M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3192MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16GB, range: 512MB, type WB
[    0.000000] reg 7, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 8, base: 17150MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000c7800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcdd0] fcdd0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7000000
[    0.000000]  0000000000 - 00c7000000 page 2M
[    0.000000] kernel direct mapping tables up to c7000000 @ c6ffb000-c7000000
[    0.000000] init_memory_mapping: 0000000100000000-000000042fe00000
[    0.000000]  0100000000 - 042fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 42fe00000 @ 42fdee000-42fe00000
[    0.000000] RAMDISK: 365e8000 - 372ec000
[    0.000000] Reserving 128MB of memory at 736MB for crashkernel (System RAM: 17150MB)
```
And when the driver problem is gone, alto it still reports a second problem about "GMBUS" but the graphics seems to be working great.

```

[    2.880650] [drm] Initialized drm 1.1.0 20060810
[    2.948786] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.948787] [drm] Driver supports precise vblank timestamp query.
[    3.201831] [drm] GMBUS timed out, falling back to bit banging on pin 7 [i915 gmbus dpd]
[    3.220806] fbcon: inteldrmfb (fb0) is primary device
[    3.386046] fb0: inteldrmfb frame buffer device
[    3.386047] drm: registered panic notifier
[    3.386784] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
```

---

### Post by lithopsian on 2011-06-05
MTRRs are registers on your CPU.  They can be used, and are used by Intel graphics drivers, to control access to system memory.  This is something that is critical to onboard graphics cards.  There are all sorts of fixups for glitches with these registers, depending on the kernel and driver version.

About your error, I would have said that your graphics weren't working great at all, but if it is only drm then you might not notice it in normal applications.  Or it might be that this is just a console modesetting issue and everything is fine once X starts.  Check your Xorg log and see if DRM is loading OK.

These issues are suspiciously like the things that were common around about Karmic time when KMS was new and drivers and kernels didn't always see eye to eye on who was doing what.  Newer kernels and newer drivers have mostly made these problems go away.

---

