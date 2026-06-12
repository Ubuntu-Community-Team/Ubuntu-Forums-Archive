---
title: "Help with mtrr_cleanup"
date: 2012-02-09
forum: General Help
---

### Post by gnaservicesinc on 2012-02-09
I am getting errors on boot,

```
 [    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
```I googled it and I have been trying different boot options like  mtrr_spare_reg_nr=1
 and CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1  but nothing seems to help.

Any suggestions?

Here is my dmesg


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-15-generic (buildd@crested) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-12ubuntu1) ) #24-Ubuntu SMP Tue Feb 7 22:32:19 UTC 2012 (Ubuntu 3.2.0-15.24-generic 3.2.5)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.2.0-15-generic root=UUID=36156e4a-3cbb-42c0-9ea3-ccde190fa388 ro crashkernel=384M-2G:64M,2G-:128M quiet splash apparmor=0 acpi_osi=Linux CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1 mtrr_spare_reg_nr=1 vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000ae5ce000 (usable)
[    0.000000]  BIOS-e820: 00000000ae5ce000 - 00000000ae628000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ae628000 - 00000000aeb36000 (reserved)
[    0.000000]  BIOS-e820: 00000000aeb36000 - 00000000aeb39000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aeb39000 - 00000000aed9f000 (reserved)
[    0.000000]  BIOS-e820: 00000000aed9f000 - 00000000aedb0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aedb0000 - 00000000aedc7000 (reserved)
[    0.000000]  BIOS-e820: 00000000aedc7000 - 00000000aedc9000 (usable)
[    0.000000]  BIOS-e820: 00000000aedc9000 - 00000000aedca000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aedca000 - 00000000aedd2000 (reserved)
[    0.000000]  BIOS-e820: 00000000aedd2000 - 00000000aeddc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aeddc000 - 00000000aee38000 (reserved)
[    0.000000]  BIOS-e820: 00000000aee38000 - 00000000aee7b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000aee7b000 - 00000000af000000 (usable)
[    0.000000]  BIOS-e820: 00000000af800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000082fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8Z68-V PRO, BIOS 1101 11/23/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x82fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 800000000 write-back
[    0.000000]   1 base 800000000 mask FC0000000 write-back
[    0.000000]   2 base 0AF800000 mask FFF800000 uncachable
[    0.000000]   3 base 0B0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   5 base 82FE00000 mask FFFE00000 uncachable
[    0.000000]   6 base 830000000 mask FF0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 32GB, type WB
[    0.000000] reg 1, base: 32GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2808MB, range: 8MB, type UC
[    0.000000] reg 3, base: 2816MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3GB, range: 1GB, type UC
[    0.000000] reg 5, base: 33534MB, range: 2MB, type UC
[    0.000000] reg 6, base: 33536MB, range: 256MB, type UC
[    0.000000] total RAM covered: 32246M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 2M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1022M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 766M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: 6M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1018M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 262M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 22M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1002M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 150M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: 54M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: -970M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 10      lose cover RAM: 118M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 10      lose cover RAM: 118M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 10      lose cover RAM: 118M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 10      lose cover RAM: 118M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 10      lose cover RAM: 118M
[    0.000000] *BAD*gran_size: 64M     chunk_size: 2G     num_reg: 10      lose cover RAM: -906M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 8      lose cover RAM: 246M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 10      lose cover RAM: 246M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 10      lose cover RAM: 246M
[    0.000000] *BAD*gran_size: 128M     chunk_size: 2G     num_reg: 10      lose cover RAM: -778M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 502M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 6      lose cover RAM: 502M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 8      lose cover RAM: 502M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 9      lose cover RAM: 502M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 6      lose cover RAM: 502M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 8      lose cover RAM: 502M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 9      lose cover RAM: 502M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 1526M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 1526M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 4      lose cover RAM: 1526M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820 update range: 00000000af800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xaf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fce70] fce70
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000af000000
[    0.000000]  0000000000 - 00af000000 page 2M
[    0.000000] kernel direct mapping tables up to af000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000082fe00000
[    0.000000]  0100000000 - 082fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 82fe00000 @ aefde000-af000000
[    0.000000] RAMDISK: 363e8000 - 371ec000
[    0.000000] Reserving 128MB of memory at 736MB for crashkernel (System RAM: 33534MB)
[    0.000000] ACPI: RSDP 00000000000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000ae61d068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000ae627250 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000ae61d140 0A10B (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000aedd3f80 00040
[    0.000000] ACPI: APIC 00000000ae627348 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000ae6273e0 001D6 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000ae6275b8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000ae6275f8 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000082fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000082fe00000
[    0.000000]   NODE_DATA [000000082fdfb000 - 000000082fdfffff]
[    0.000000]  [ffffea0000000000-ffffea0020bfffff] PMD -> [ffff88080fc00000-ffff88082f3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0082fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000ae5ce
[    0.000000]     0: 0x000aedc7 -> 0x000aedc9
[    0.000000]     0: 0x000aee7b -> 0x000af000
[    0.000000]     0: 0x00100000 -> 0x0082fe00
[    0.000000] On node 0 totalpages: 8249570
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 693141 pages, LIFO batch:31
[    0.000000]   Normal zone: 117752 pages used for memmap
[    0.000000]   Normal zone: 7418376 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000ae5ce000 - 00000000ae628000
[    0.000000] PM: Registered nosave memory: 00000000ae628000 - 00000000aeb36000
[    0.000000] PM: Registered nosave memory: 00000000aeb36000 - 00000000aeb39000
[    0.000000] PM: Registered nosave memory: 00000000aeb39000 - 00000000aed9f000
[    0.000000] PM: Registered nosave memory: 00000000aed9f000 - 00000000aedb0000
[    0.000000] PM: Registered nosave memory: 00000000aedb0000 - 00000000aedc7000
[    0.000000] PM: Registered nosave memory: 00000000aedc9000 - 00000000aedca000
[    0.000000] PM: Registered nosave memory: 00000000aedca000 - 00000000aedd2000
[    0.000000] PM: Registered nosave memory: 00000000aedd2000 - 00000000aeddc000
[    0.000000] PM: Registered nosave memory: 00000000aeddc000 - 00000000aee38000
[    0.000000] PM: Registered nosave memory: 00000000aee38000 - 00000000aee7b000
[    0.000000] PM: Registered nosave memory: 00000000af000000 - 00000000af800000
[    0.000000] PM: Registered nosave memory: 00000000af800000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:2f31c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88082fa00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 8115429
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-15-generic root=UUID=36156e4a-3cbb-42c0-9ea3-ccde190fa388 ro crashkernel=384M-2G:64M,2G-:128M quiet splash apparmor=0 acpi_osi=Linux CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1 mtrr_spare_reg_nr=1 vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 32253864k/34338816k available (6546k kernel code, 1340536k absent, 744416k reserved, 6647k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 264241152 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3411.313 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6822.62 BogoMIPS (lpj=13645252)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000022] AppArmor: AppArmor disabled by boot time parameter
[    0.000023] Yama: becoming mindful.
[    0.001983] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
[    0.006910] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.008910] Mount-cache hash table entries: 256
[    0.008987] Initializing cgroup subsys cpuacct
[    0.008990] Initializing cgroup subsys memory
[    0.008995] Initializing cgroup subsys devices
[    0.008997] Initializing cgroup subsys freezer
[    0.008998] Initializing cgroup subsys blkio
[    0.009001] Initializing cgroup subsys perf_event
[    0.009020] CPU: Physical Processor ID: 0
[    0.009021] CPU: Processor Core ID: 0
[    0.009024] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.009025] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.009027] mce: CPU supports 9 MCE banks
[    0.009037] CPU0: Thermal monitoring enabled (TM1)
[    0.009042] using mwait in idle threads.
[    0.010788] ACPI: Core revision 20110623
[    0.466385] ftrace: allocating 26984 entries in 106 pages
[    0.473686] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.513346] CPU0: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz stepping 07
[    0.619974] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.619978] PEBS disabled due to CPU errata.
[    0.619979] ... version:                3
[    0.619980] ... bit width:              48
[    0.619981] ... generic registers:      4
[    0.619981] ... value mask:             0000ffffffffffff
[    0.619982] ... max period:             000000007fffffff
[    0.619983] ... fixed-purpose events:   3
[    0.619984] ... event mask:             000000070000000f
[    0.620088] NMI watchdog enabled, takes one hw-pmu counter.
[    0.620136] Booting Node   0, Processors  #1
[    0.620137] smpboot cpu 1: start_ip = 98000
[    0.728003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.728065]  #2
[    0.728066] smpboot cpu 2: start_ip = 98000
[    0.835928] NMI watchdog enabled, takes one hw-pmu counter.
[    0.835986]  #3
[    0.835987] smpboot cpu 3: start_ip = 98000
[    0.943848] NMI watchdog enabled, takes one hw-pmu counter.
[    0.943906]  #4
[    0.943907] smpboot cpu 4: start_ip = 98000
[    1.051749] NMI watchdog enabled, takes one hw-pmu counter.
[    1.051817]  #5
[    1.051818] smpboot cpu 5: start_ip = 98000
[    1.159680] NMI watchdog enabled, takes one hw-pmu counter.
[    1.159741]  #6
[    1.159742] smpboot cpu 6: start_ip = 98000
[    1.267604] NMI watchdog enabled, takes one hw-pmu counter.
[    1.267662]  #7 Ok.
[    1.267662] smpboot cpu 7: start_ip = 98000
[    1.375524] NMI watchdog enabled, takes one hw-pmu counter.
[    1.375550] Brought up 8 CPUs
[    1.375552] Total of 8 processors activated (54577.19 BogoMIPS).
[    1.382319] devtmpfs: initialized
[    1.383603] EVM: security.selinux
[    1.383604] EVM: security.SMACK64
[    1.383605] EVM: security.capability
[    1.383620] PM: Registering ACPI NVS region at ae5ce000 (368640 bytes)
[    1.383625] PM: Registering ACPI NVS region at aeb36000 (12288 bytes)
[    1.383626] PM: Registering ACPI NVS region at aed9f000 (69632 bytes)
[    1.383628] PM: Registering ACPI NVS region at aedc9000 (4096 bytes)
[    1.383630] PM: Registering ACPI NVS region at aedd2000 (40960 bytes)
[    1.383631] PM: Registering ACPI NVS region at aee38000 (274432 bytes)
[    1.384122] print_constraints: dummy:
[    1.384149] RTC time: 18:35:50, date: 02/09/12
[    1.384169] NET: Registered protocol family 16
[    1.384235] Trying to unpack rootfs image as initramfs...
[    1.384236] ACPI: bus type pci registered
[    1.384278] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    1.384280] PCI: not using MMCONFIG
[    1.384281] PCI: Using configuration type 1 for base access
[    1.385067] bio: create slab <bio-0> at 0
[    1.385112] ACPI: Added _OSI(Module Device)
[    1.385113] ACPI: Added _OSI(Processor Device)
[    1.385114] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.385116] ACPI: Added _OSI(Processor Aggregator Device)
[    1.385117] ACPI: Added _OSI(Linux)
[    1.385947] ACPI: EC: Look up EC in DSDT
[    1.386730] ACPI: Executed 1 blocks of module-level executable AML code
[    1.388258] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
[    1.388262] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110623/nsinit-349)
[    1.388441] ACPI: SSDT 00000000aedd2818 0079C (v01    AMI      IST 00000001 MSFT 03000001)
[    1.388722] ACPI: Dynamic OEM Table Load:
[    1.388723] ACPI: SSDT           (null) 0079C (v01    AMI      IST 00000001 MSFT 03000001)
[    1.388751] ACPI: SSDT 00000000aedd9a18 0021C (v01    AMI      CST 00000001 MSFT 03000001)
[    1.388973] ACPI: Dynamic OEM Table Load:
[    1.388974] ACPI: SSDT           (null) 0021C (v01    AMI      CST 00000001 MSFT 03000001)
[    1.389467] ACPI: Interpreter enabled
[    1.389470] ACPI: (supports S0 S1 S3 S4 S5)
[    1.389482] ACPI: Using IOAPIC for interrupt routing
[    1.389496] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    1.389530] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    1.400885] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
[    1.404087] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    1.404194] ACPI: No dock devices found.
[    1.404195] HEST: Table not found.
[    1.404197] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.404304] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.404426] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.404428] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.404429] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.404431] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
[    1.404432] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xffffffff]
[    1.404435] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000c8000-0x000dffff] (conflicts with Video ROM [mem 0x000c0000-0x000cdfff])
[    1.404442] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    1.404469] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    1.404492] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.404494] pci 0000:00:01.0: PME# disabled
[    1.404508] pci 0000:00:02.0: [8086:0122] type 0 class 0x000300
[    1.404515] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
[    1.404520] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.404524] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    1.404569] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.404590] pci 0000:00:16.0: reg 10: [mem 0xfe629000-0xfe62900f 64bit]
[    1.404660] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.404663] pci 0000:00:16.0: PME# disabled
[    1.404689] pci 0000:00:19.0: [8086:1503] type 0 class 0x000200
[    1.404706] pci 0000:00:19.0: reg 10: [mem 0xfe600000-0xfe61ffff]
[    1.404714] pci 0000:00:19.0: reg 14: [mem 0xfe628000-0xfe628fff]
[    1.404721] pci 0000:00:19.0: reg 18: [io  0xf080-0xf09f]
[    1.404779] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    1.404783] pci 0000:00:19.0: PME# disabled
[    1.404804] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.404823] pci 0000:00:1a.0: reg 10: [mem 0xfe627000-0xfe6273ff]
[    1.404908] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.404912] pci 0000:00:1a.0: PME# disabled
[    1.404933] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.404947] pci 0000:00:1b.0: reg 10: [mem 0xfe620000-0xfe623fff 64bit]
[    1.405010] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.405013] pci 0000:00:1b.0: PME# disabled
[    1.405033] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.405107] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.405110] pci 0000:00:1c.0: PME# disabled
[    1.405132] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.405206] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.405210] pci 0000:00:1c.1: PME# disabled
[    1.405231] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    1.405305] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.405308] pci 0000:00:1c.2: PME# disabled
[    1.405331] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    1.405404] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.405408] pci 0000:00:1c.4: PME# disabled
[    1.405430] pci 0000:00:1c.6: [8086:244e] type 1 class 0x000604
[    1.405504] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.405507] pci 0000:00:1c.6: PME# disabled
[    1.405533] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.405553] pci 0000:00:1d.0: reg 10: [mem 0xfe626000-0xfe6263ff]
[    1.405637] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.405641] pci 0000:00:1d.0: PME# disabled
[    1.405663] pci 0000:00:1f.0: [8086:1c44] type 0 class 0x000601
[    1.405780] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    1.405796] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    1.405803] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    1.405810] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    1.405817] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    1.405824] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    1.405831] pci 0000:00:1f.2: reg 24: [mem 0xfe625000-0xfe6257ff]
[    1.405873] pci 0000:00:1f.2: PME# supported from D3hot
[    1.405876] pci 0000:00:1f.2: PME# disabled
[    1.405891] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.405905] pci 0000:00:1f.3: reg 10: [mem 0xfe624000-0xfe6240ff 64bit]
[    1.405924] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    1.405963] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.406006] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.406082] pci 0000:03:00.0: [1b21:1042] type 0 class 0x000c03
[    1.406109] pci 0000:03:00.0: reg 10: [mem 0xfe500000-0xfe507fff 64bit]
[    1.406253] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    1.406259] pci 0000:03:00.0: PME# disabled
[    1.411453] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.411459] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    1.411505] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.411579] pci 0000:05:00.0: [1b21:1042] type 0 class 0x000c03
[    1.411607] pci 0000:05:00.0: reg 10: [mem 0xfe400000-0xfe407fff 64bit]
[    1.411751] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    1.411756] pci 0000:05:00.0: PME# disabled
[    1.419447] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    1.419453] pci 0000:00:1c.4:   bridge window [mem 0xfe400000-0xfe4fffff]
[    1.419513] pci 0000:06:00.0: [1b21:1080] type 1 class 0x000604
[    1.419633] pci 0000:00:1c.6: PCI bridge to [bus 06-07] (subtractive decode)
[    1.419643] pci 0000:00:1c.6:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.419644] pci 0000:00:1c.6:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.419646] pci 0000:00:1c.6:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.419647] pci 0000:00:1c.6:   bridge window [mem 0xcfa00000-0xffffffff] (subtractive decode)
[    1.419758] pci 0000:06:00.0: PCI bridge to [bus 07-07] (subtractive decode)
[    1.419780] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.419781] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.419782] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.419784] pci 0000:06:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.419785] pci 0000:06:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.419786] pci 0000:06:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.419788] pci 0000:06:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.419789] pci 0000:06:00.0:   bridge window [mem 0xcfa00000-0xffffffff] (subtractive decode)
[    1.419825] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.419883] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.419900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.419915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    1.419929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    1.419945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    1.419961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    1.419976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6.BR24._PRT]
[    1.420058]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.420173]  pci0000:00: ACPI _OSC control (0x1c) granted
[    1.422479] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.422508] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    1.422535] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.422561] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0
[    1.422588] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.422614] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.422641] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.422668] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.422737] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.422742] vgaarb: loaded
[    1.422743] vgaarb: bridge control possible 0000:00:02.0
[    1.422799] i2c-core: driver [aat2870] using legacy suspend method
[    1.422800] i2c-core: driver [aat2870] using legacy resume method
[    1.422837] SCSI subsystem initialized
[    1.422868] libata version 3.00 loaded.
[    1.422897] usbcore: registered new interface driver usbfs
[    1.422902] usbcore: registered new interface driver hub
[    1.422914] usbcore: registered new device driver usb
[    1.422958] PCI: Using ACPI for IRQ routing
[    1.424326] PCI: pci_cache_line_size set to 64 bytes
[    1.424392] reserve RAM buffer: 000000000009d800 - 000000000009ffff
[    1.424394] reserve RAM buffer: 00000000ae5ce000 - 00000000afffffff
[    1.424397] reserve RAM buffer: 00000000aedc9000 - 00000000afffffff
[    1.424398] reserve RAM buffer: 00000000af000000 - 00000000afffffff
[    1.424400] reserve RAM buffer: 000000082fe00000 - 000000082fffffff
[    1.424461] NetLabel: Initializing
[    1.424462] NetLabel:  domain hash size = 128
[    1.424463] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.424469] NetLabel:  unlabeled traffic allowed by default
[    1.424499] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.424502] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.426513] Switching to clocksource hpet
[    1.430345] pnp: PnP ACPI init
[    1.430355] ACPI: bus type pnp registered
[    1.430443] pnp 00:00: [bus 00-ff]
[    1.430445] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.430446] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.430447] pnp 00:00: [io  0x0d00-0xffff window]
[    1.430449] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.430451] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    1.430452] pnp 00:00: [mem 0xcfa00000-0xffffffff window]
[    1.430453] pnp 00:00: [mem 0x00000000 window]
[    1.430504] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.430547] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    1.430548] pnp 00:01: [mem 0xe0000000-0xe3ffffff]
[    1.430549] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    1.430550] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    1.430551] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    1.430577] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    1.430579] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    1.430580] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.430582] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.430583] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    1.430585] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.430622] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    1.430623] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    1.430624] pnp 00:02: [io  0x0290-0x029f]
[    1.430626] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    1.430646] system 00:02: [io  0x0290-0x029f] has been reserved
[    1.430648] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.430656] pnp 00:03: [dma 4]
[    1.430657] pnp 00:03: [io  0x0000-0x000f]
[    1.430658] pnp 00:03: [io  0x0081-0x0083]
[    1.430659] pnp 00:03: [io  0x0087]
[    1.430660] pnp 00:03: [io  0x0089-0x008b]
[    1.430661] pnp 00:03: [io  0x008f]
[    1.430662] pnp 00:03: [io  0x00c0-0x00df]
[    1.430676] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.430681] pnp 00:04: [io  0x0070-0x0071]
[    1.430688] pnp 00:04: [irq 8]
[    1.430700] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.430704] pnp 00:05: [io  0x0061]
[    1.430717] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.430726] pnp 00:06: [io  0x0010-0x001f]
[    1.430727] pnp 00:06: [io  0x0022-0x003f]
[    1.430728] pnp 00:06: [io  0x0044-0x005f]
[    1.430729] pnp 00:06: [io  0x0063]
[    1.430730] pnp 00:06: [io  0x0065]
[    1.430731] pnp 00:06: [io  0x0067-0x006f]
[    1.430732] pnp 00:06: [io  0x0072-0x007f]
[    1.430733] pnp 00:06: [io  0x0080]
[    1.430733] pnp 00:06: [io  0x0084-0x0086]
[    1.430734] pnp 00:06: [io  0x0088]
[    1.430735] pnp 00:06: [io  0x008c-0x008e]
[    1.430736] pnp 00:06: [io  0x0090-0x009f]
[    1.430737] pnp 00:06: [io  0x00a2-0x00bf]
[    1.430738] pnp 00:06: [io  0x00e0-0x00ef]
[    1.430739] pnp 00:06: [io  0x04d0-0x04d1]
[    1.430761] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    1.430763] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.430767] pnp 00:07: [io  0x00f0-0x00ff]
[    1.430771] pnp 00:07: [irq 13]
[    1.430784] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.430942] pnp 00:08: [io  0x0400-0x0453]
[    1.430943] pnp 00:08: [io  0x0458-0x047f]
[    1.430944] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    1.430947] pnp 00:08: [io  0x0500-0x057f]
[    1.430948] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    1.430949] pnp 00:08: [mem 0xfec00000-0xfecfffff]
[    1.430950] pnp 00:08: [mem 0xfed08000-0xfed08fff]
[    1.430951] pnp 00:08: [mem 0xff000000-0xffffffff]
[    1.430972] system 00:08: [io  0x0400-0x0453] has been reserved
[    1.430974] system 00:08: [io  0x0458-0x047f] has been reserved
[    1.430975] system 00:08: [io  0x0500-0x057f] has been reserved
[    1.430977] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.430979] system 00:08: [mem 0xfec00000-0xfecfffff] could not be reserved
[    1.430981] system 00:08: [mem 0xfed08000-0xfed08fff] has been reserved
[    1.430983] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    1.430984] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.431005] pnp 00:09: [io  0x0454-0x0457]
[    1.431025] system 00:09: [io  0x0454-0x0457] has been reserved
[    1.431027] system 00:09: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.431102] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    1.431125] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.431216] pnp: PnP ACPI: found 11 devices
[    1.431217] ACPI: ACPI bus type pnp unregistered
[    1.437066] PCI: max bus depth: 2 pci_try_num: 3
[    1.437116] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.437120] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.437131] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.437136] pci 0000:00:1c.1:   bridge window [mem 0xfe500000-0xfe5fffff]
[    1.437143] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.437153] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    1.437158] pci 0000:00:1c.4:   bridge window [mem 0xfe400000-0xfe4fffff]
[    1.437165] pci 0000:06:00.0: PCI bridge to [bus 07-07]
[    1.437184] pci 0000:00:1c.6: PCI bridge to [bus 06-07]
[    1.437203] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.437205] pci 0000:00:01.0: setting latency timer to 64
[    1.437213] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.437216] pci 0000:00:1c.0: setting latency timer to 64
[    1.437222] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.437226] pci 0000:00:1c.1: setting latency timer to 64
[    1.437233] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.437237] pci 0000:00:1c.2: setting latency timer to 64
[    1.437242] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.437246] pci 0000:00:1c.4: setting latency timer to 64
[    1.437252] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.437255] pci 0000:00:1c.6: setting latency timer to 64
[    1.437262] pci 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.437267] pci 0000:06:00.0: setting latency timer to 64
[    1.437272] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.437273] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.437274] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.437275] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xffffffff]
[    1.437277] pci_bus 0000:03: resource 1 [mem 0xfe500000-0xfe5fffff]
[    1.437278] pci_bus 0000:05: resource 1 [mem 0xfe400000-0xfe4fffff]
[    1.437280] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    1.437281] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    1.437282] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    1.437284] pci_bus 0000:06: resource 7 [mem 0xcfa00000-0xffffffff]
[    1.437285] pci_bus 0000:07: resource 8 [io  0x0000-0x0cf7]
[    1.437286] pci_bus 0000:07: resource 9 [io  0x0d00-0xffff]
[    1.437287] pci_bus 0000:07: resource 10 [mem 0x000a0000-0x000bffff]
[    1.437289] pci_bus 0000:07: resource 11 [mem 0xcfa00000-0xffffffff]
[    1.437307] NET: Registered protocol family 2
[    1.437571] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.438293] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.439312] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.439431] TCP: Hash tables configured (established 524288 bind 65536)
[    1.439432] TCP reno registered
[    1.439467] UDP hash table entries: 16384 (order: 7, 524288 bytes)
[    1.439562] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
[    1.439677] NET: Registered protocol family 1
[    1.439688] pci 0000:00:02.0: Boot video device
[    1.439831] PCI: CLS 64 bytes, default 64
[    1.439832] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.439834] Placing 64MB software IO TLB between ffff8800aa5ce000 - ffff8800ae5ce000
[    1.439835] software IO TLB at phys 0xaa5ce000 - 0xae5ce000
[    1.440244] audit: initializing netlink socket (disabled)
[    1.440250] type=2000 audit(1328812548.768:1): initialized
[    1.487857] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.555121] VFS: Disk quotas dquot_6.5.2
[    1.555154] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.555436] fuse init (API version 7.17)
[    1.555486] msgmni has been set to 32768
[    1.555692] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.555709] io scheduler noop registered
[    1.555710] io scheduler deadline registered
[    1.555726] io scheduler cfq registered (default)
[    1.555788] pcieport 0000:00:01.0: setting latency timer to 64
[    1.555806] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.555848] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.555885] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.555940] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.555976] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.556032] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.556069] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    1.556124] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.556160] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    1.556223] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.556225] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.556239] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.556243] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.556256] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.556258] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.556262] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    1.556275] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    1.556279] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    1.556292] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    1.556293] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    1.556297] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    1.556306] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.556319] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.556348] intel_idle: MWAIT substates: 0x1120
[    1.556349] intel_idle: v0.4 model 0x2A
[    1.556350] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.556417] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.556421] ACPI: Power Button [PWRB]
[    1.556445] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.556447] ACPI: Power Button [PWRF]
[    1.559921] ERST: Table is not found!
[    1.559923] GHES: HEST is not enabled!
[    1.559964] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.641677] Freeing initrd memory: 14352k freed
[    1.774711] Linux agpgart interface v0.103
[    1.774764] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.774869] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.776214] agpgart-intel 0000:00:00.0: detected 524288K stolen memory
[    1.776306] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.777131] brd: module loaded
[    1.777554] loop: module loaded
[    1.777631] ahci 0000:00:1f.2: version 3.0
[    1.777647] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.777680] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.790351] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.790356] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst
[    1.790363] ahci 0000:00:1f.2: setting latency timer to 64
[    1.830607] scsi0 : ahci
[    1.830659] scsi1 : ahci
[    1.830702] scsi2 : ahci
[    1.830747] scsi3 : ahci
[    1.830790] scsi4 : ahci
[    1.830832] scsi5 : ahci
[    1.830917] ata1: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625100 irq 45
[    1.830919] ata2: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625180 irq 45
[    1.830922] ata3: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625200 irq 45
[    1.830924] ata4: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625280 irq 45
[    1.830926] ata5: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625300 irq 45
[    1.830929] ata6: SATA max UDMA/133 abar m2048@0xfe625000 port 0xfe625380 irq 45
[    1.831161] Fixed MDIO Bus: probed
[    1.831170] tun: Universal TUN/TAP device driver, 1.6
[    1.831171] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.831198] PPP generic driver version 2.4.2
[    1.831256] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.831270] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.831280] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.831283] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.831307] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.831328] ehci_hcd 0000:00:1a.0: debug port 2
[    1.835215] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.835225] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfe627000
[    1.850278] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.850396] hub 1-0:1.0: USB hub found
[    1.850398] hub 1-0:1.0: 2 ports detected
[    1.850436] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.850444] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.850447] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.850475] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.850492] ehci_hcd 0000:00:1d.0: debug port 2
[    1.854367] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.854370] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe626000
[    1.866267] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.866375] hub 2-0:1.0: USB hub found
[    1.866377] hub 2-0:1.0: 2 ports detected
[    1.866411] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.866417] uhci_hcd: USB Universal Host Controller Interface driver
[    1.866436] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.866452] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.866456] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.866483] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    1.927584] xhci_hcd 0000:03:00.0: irq 17, io mem 0xfe500000
[    1.927634] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.927638] xhci_hcd 0000:03:00.0: irq 47 for MSI/MSI-X
[    1.927642] xhci_hcd 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.927645] xhci_hcd 0000:03:00.0: irq 49 for MSI/MSI-X
[    1.927649] xhci_hcd 0000:03:00.0: irq 50 for MSI/MSI-X
[    1.927651] xhci_hcd 0000:03:00.0: irq 51 for MSI/MSI-X
[    1.927654] xhci_hcd 0000:03:00.0: irq 52 for MSI/MSI-X
[    1.927657] xhci_hcd 0000:03:00.0: irq 53 for MSI/MSI-X
[    1.927789] xHCI xhci_add_endpoint called for root hub
[    1.927791] xHCI xhci_check_bandwidth called for root hub
[    1.927805] hub 3-0:1.0: USB hub found
[    1.927812] hub 3-0:1.0: 2 ports detected
[    1.927844] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.927874] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
[    1.927929] xHCI xhci_add_endpoint called for root hub
[    1.927930] xHCI xhci_check_bandwidth called for root hub
[    1.927943] hub 4-0:1.0: USB hub found
[    1.927949] hub 4-0:1.0: 2 ports detected
[    1.978203] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.978232] xhci_hcd 0000:05:00.0: setting latency timer to 64
[    1.978237] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.978291] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 5
[    2.039407] xhci_hcd 0000:05:00.0: irq 16, io mem 0xfe400000
[    2.039456] xhci_hcd 0000:05:00.0: irq 54 for MSI/MSI-X
[    2.039459] xhci_hcd 0000:05:00.0: irq 55 for MSI/MSI-X
[    2.039462] xhci_hcd 0000:05:00.0: irq 56 for MSI/MSI-X
[    2.039464] xhci_hcd 0000:05:00.0: irq 57 for MSI/MSI-X
[    2.039467] xhci_hcd 0000:05:00.0: irq 58 for MSI/MSI-X
[    2.039469] xhci_hcd 0000:05:00.0: irq 59 for MSI/MSI-X
[    2.039473] xhci_hcd 0000:05:00.0: irq 60 for MSI/MSI-X
[    2.039476] xhci_hcd 0000:05:00.0: irq 61 for MSI/MSI-X
[    2.039610] xHCI xhci_add_endpoint called for root hub
[    2.039611] xHCI xhci_check_bandwidth called for root hub
[    2.039626] hub 5-0:1.0: USB hub found
[    2.039632] hub 5-0:1.0: 2 ports detected
[    2.039667] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    2.039693] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 6
[    2.039746] xHCI xhci_add_endpoint called for root hub
[    2.039747] xHCI xhci_check_bandwidth called for root hub
[    2.039760] hub 6-0:1.0: USB hub found
[    2.039765] hub 6-0:1.0: 2 ports detected
[    2.082193] usbcore: registered new interface driver libusual
[    2.082230] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.084669] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.084672] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.084741] mousedev: PS/2 mouse device common for all mice
[    2.084826] rtc_cmos 00:04: RTC can wake from S4
[    2.084909] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.084934] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.084976] device-mapper: uevent: version 1.0.3
[    2.085015] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.085120] cpuidle: using governor ladder
[    2.085281] cpuidle: using governor menu
[    2.085282] EFI Variables Facility v0.08 2004-May-17
[    2.085392] TCP cubic registered
[    2.085446] NET: Registered protocol family 10
[    2.085677] NET: Registered protocol family 17
[    2.085686] Registering the dns_resolver key type
[    2.085768] PM: Hibernation image not present or could not be loaded.
[    2.085778] registered taskstats version 1
[    2.119089] hpet1: lost 1 rtc interrupts
[    2.124295]   Magic number: 0:589:594
[    2.124417] rtc_cmos 00:04: setting system clock to 2012-02-09 18:35:50 UTC (1328812550)
[    2.125330] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.125331] EDD information not available.
[    2.150125] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.150152] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.150174] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.150207] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.150224] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.151247] ata4.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    2.151249] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.151276] ata6.00: ATA-8: ST3750528AS, CC49, max UDMA/133
[    2.151278] ata6.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.151438] ata5.00: ATA-8: ST3500418AS, CC49, max UDMA/133
[    2.151440] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.151778] ata2.00: ATA-9: INTEL SSDSC2CW180A3, 400i, max UDMA/133
[    2.151783] ata2.00: 351651888 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.152600] ata4.00: configured for UDMA/133
[    2.152646] ata6.00: configured for UDMA/133
[    2.152722] ata3.00: ATAPI: ASUS    DRW-24B3LT, 1.00, max UDMA/100
[    2.152738] ata5.00: configured for UDMA/133
[    2.153563] ata3.00: configured for UDMA/100
[    2.154120] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.154442] ata1.00: ATA-7: INTEL SSDSA2M080G2GN, 2CV102M3, max UDMA/133
[    2.154443] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.154895] ata1.00: configured for UDMA/133
[    2.154975] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2M080 2CV1 PQ: 0 ANSI: 5
[    2.155086] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.155104] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.155126] sd 0:0:0:0: [sda] Write Protect is off
[    2.155129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.155140] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.157240]  sda: sda1 sda2 sda3 sda4
[    2.157659] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.161713] ata2.00: configured for UDMA/133
[    2.161922] scsi 1:0:0:0: Direct-Access     ATA      INTEL SSDSC2CW18 400i PQ: 0 ANSI: 5
[    2.161978] sd 1:0:0:0: [sdb] 351651888 512-byte logical blocks: (180 GB/167 GiB)
[    2.162003] sd 1:0:0:0: [sdb] Write Protect is off
[    2.162005] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.162013] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.162023] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.162333]  sdb: unknown partition table
[    2.162461] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.163161] scsi 2:0:0:0: CD-ROM            ASUS     DRW-24B3LT       1.00 PQ: 0 ANSI: 5
[    2.166954] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.166957] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.167122] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.167198] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.167333] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    2.167437] sd 3:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.167465] sd 3:0:0:0: [sdc] Write Protect is off
[    2.167466] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.167478] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.167480] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.167628] scsi 4:0:0:0: Direct-Access     ATA      ST3500418AS      CC49 PQ: 0 ANSI: 5
[    2.167689] sd 4:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.167710] sd 4:0:0:0: [sdd] Write Protect is off
[    2.167712] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.167720] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.167736] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    2.167914] scsi 5:0:0:0: Direct-Access     ATA      ST3750528AS      CC49 PQ: 0 ANSI: 5
[    2.168014] sd 5:0:0:0: [sde] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.168040] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    2.168042] sd 5:0:0:0: [sde] Write Protect is off
[    2.168044] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.168057] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.174098] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.175475]  sde: sde1 sde2 sde3 sde4
[    2.175998] sd 5:0:0:0: [sde] Attached SCSI disk
[    2.193190]  sdc: sdc1 sdc2 sdc3
[    2.193546] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.214142]  sdd: sdd1 sdd2 sdd3 sdd4 sdd5 sdd6 sdd7 sdd8 sdd9
[    2.214894] sd 4:0:0:0: [sdd] Attached SCSI disk
[    2.215786] Freeing unused kernel memory: 920k freed
[    2.215853] Write protecting the kernel read-only data: 12288k
[    2.218829] Freeing unused kernel memory: 1628k freed
[    2.221084] Freeing unused kernel memory: 1204k freed
[    2.230934] udevd[122]: starting version 175
[    2.239891] Btrfs loaded
[    2.247785] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.247787] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.247810] e1000e 0000:00:19.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.247819] e1000e 0000:00:19.0: setting latency timer to 64
[    2.247923] e1000e 0000:00:19.0: irq 62 for MSI/MSI-X
[    2.310486] hub 1-1:1.0: USB hub found
[    2.310592] hub 1-1:1.0: 6 ports detected
[    2.421913] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.437901] Refined TSC clocksource calibration: 3411.127 MHz.
[    2.437906] Switching to clocksource tsc
[    2.554324] hub 2-1:1.0: USB hub found
[    2.554431] hub 2-1:1.0: 8 ports detected
[    2.559377] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f4:6d:04:42:97:57
[    2.559379] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.559425] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    2.721729] usb 5-2: new low-speed USB device number 2 using xhci_hcd
[    2.741443] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
[    2.743159] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
[    2.744148] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
[    2.744390] usb 5-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.749482] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1c.4/0000:05:00.0/usb5/5-2/5-2:1.0/input/input2
[    2.749546] generic-usb 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:05:00.0-2/input0
[    2.749553] usbcore: registered new interface driver usbhid
[    2.749554] usbhid: USB HID core driver
[    2.825863] usb 2-1.2: new full-speed USB device number 3 using ehci_hcd
[    2.925830] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
[    2.925932] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:1d.0-1.2/input0
[    2.931416] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input4
[    2.931594] generic-usb 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:1d.0-1.2/input1
[    2.946816] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input5
[    2.947025] generic-usb 0003:045E:0745.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:1d.0-1.2/input2
[    2.974498] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    3.017652] usb 2-1.3: new high-speed USB device number 4 using ehci_hcd
[    3.111129] hub 2-1.3:1.0: USB hub found
[    3.111450] hub 2-1.3:1.0: 4 ports detected
[    4.524437] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.531354] udevd[428]: starting version 175
[    4.540208] Adding 1000k swap on /dev/sdd7.  Priority:-1 extents:1 across:1000k
[    4.541614] lp: driver loaded but no devices found
[    4.661790] wmi: Mapper loaded
[    4.667815] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    4.668098] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.668105] mei 0000:00:16.0: setting latency timer to 64
[    4.668156] mei 0000:00:16.0: irq 63 for MSI/MSI-X
[    4.669669] [drm] Initialized drm 1.1.0 20060810
[    4.700688] ip_tables: (C) 2000-2006 Netfilter Core Team
[    4.700891] device-mapper: multipath: version 1.3.0 loaded
[    4.704728] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    4.719141] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    4.721414] asus_wmi: ASUS WMI generic driver loaded
[    4.722131] asus_wmi: Initialization: 0x0
[    4.722155] asus_wmi: BIOS WMI version: 0.9
[    4.722194] asus_wmi: SFUN value: 0x0
[    4.722475] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input6
[    4.723403] asus_wmi: Backlight controlled by ACPI video driver
[    4.768060] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.768067] i915 0000:00:02.0: setting latency timer to 64
[    4.811585] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    4.811587] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    4.811774] i915 0000:00:02.0: irq 64 for MSI/MSI-X
[    4.811778] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.811778] [drm] Driver supports precise vblank timestamp query.
[    4.811798] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.246387] fbcon: inteldrmfb (fb0) is primary device
[    5.246448] Console: switching to colour frame buffer device 240x67
[    5.246467] fb0: inteldrmfb frame buffer device
[    5.246467] drm: registered panic notifier
[    5.247016] fixme: max PWM is zero.
[    5.247085] acpi device:42: registered as cooling_device8
[    5.247227] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    5.247278] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.247321] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.247354] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.247397] snd_hda_intel 0000:00:1b.0: irq 65 for MSI/MSI-X
[    5.247417] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    5.802016] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[    5.802060] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.802107] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.802141] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.802172] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    5.802202] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    5.802232] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    5.802262] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    5.802291] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    5.802321] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    6.819454] EXT4-fs (sda3): re-mounted. Opts: discard,errors=remount-ro
[    6.848194] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: discard
[    6.853543] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: discard
[    6.916743] EXT4-fs (sdd2): warning: maximal mount count reached, running e2fsck is recommended
[    6.918010] EXT4-fs (sdd2): mounted filesystem with ordered data mode. Opts: (null)
[    7.169644] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    7.288209] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    7.377589] EXT4-fs (sdd5): warning: maximal mount count reached, running e2fsck is recommended
[    7.378900] EXT4-fs (sdd5): mounted filesystem with ordered data mode. Opts: (null)
[    7.424578] EXT4-fs (sde4): warning: maximal mount count reached, running e2fsck is recommended
[    7.424952] EXT4-fs (sde4): mounted filesystem with ordered data mode. Opts: (null)
[    7.491682] EXT4-fs (sdd6): mounted filesystem with ordered data mode. Opts: (null)
[    7.525173] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[    7.652154] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[    7.794465] EXT4-fs (sdd4): mounted filesystem with ordered data mode. Opts: (null)
[    7.826958] EXT4-fs (sdd8): mounted filesystem with ordered data mode. Opts: (null)
[    7.928123] EXT4-fs (sdd9): mounted filesystem with ordered data mode. Opts: (null)
[    7.935796] RPC: Registered named UNIX socket transport module.
[    7.935798] RPC: Registered udp transport module.
[    7.935799] RPC: Registered tcp transport module.
[    7.935800] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    7.937986] FS-Cache: Loaded
[    7.941250] FS-Cache: Netfs 'nfs' registered for caching
[    7.945599] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    7.966700] ppdev: user-space parallel port driver
[    7.970734] Bluetooth: Core ver 2.16
[    7.970749] NET: Registered protocol family 31
[    7.970750] Bluetooth: HCI device and connection manager initialized
[    7.970752] Bluetooth: HCI socket layer initialized
[    7.970754] Bluetooth: L2CAP socket layer initialized
[    7.970758] Bluetooth: SCO socket layer initialized
[    7.972175] Bluetooth: RFCOMM TTY layer initialized
[    7.972179] Bluetooth: RFCOMM socket layer initialized
[    7.972181] Bluetooth: RFCOMM ver 1.11
[    7.979491] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.979493] Bluetooth: BNEP filters: protocol multicast
[    7.991534] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x23
[    7.993014] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x23
[    7.993711] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x23
[    7.994396] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x23
[    7.995069] microcode: CPU4 sig=0x206a7, pf=0x2, revision=0x23
[    7.995794] microcode: CPU5 sig=0x206a7, pf=0x2, revision=0x23
[    7.996507] microcode: CPU6 sig=0x206a7, pf=0x2, revision=0x23
[    7.997153] microcode: CPU7 sig=0x206a7, pf=0x2, revision=0x23
[    7.997781] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.015521] microcode: CPU0 updated to revision 0x25, date = 2011-10-11
[    8.015841] microcode: CPU1 updated to revision 0x25, date = 2011-10-11
[    8.016159] microcode: CPU2 updated to revision 0x25, date = 2011-10-11
[    8.016475] microcode: CPU3 updated to revision 0x25, date = 2011-10-11
[    8.016773] microcode: CPU4 updated to revision 0x25, date = 2011-10-11
[    8.017098] microcode: CPU5 updated to revision 0x25, date = 2011-10-11
[    8.017415] microcode: CPU6 updated to revision 0x25, date = 2011-10-11
[    8.017732] microcode: CPU7 updated to revision 0x25, date = 2011-10-11
[    8.031515] init: failsafe main process (1270) killed by TERM signal
[    8.036561] init: gdm main process (1470) killed by TERM signal
[    8.142323] e1000e 0000:00:19.0: irq 62 for MSI/MSI-X
[    8.198231] e1000e 0000:00:19.0: irq 62 for MSI/MSI-X
[    8.198951] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.725592] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   11.726282] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```
Here is cat /proc/meminfo
```
MemTotal:       32271968 kB
MemFree:        21204312 kB
Buffers:          267520 kB
Cached:          7185412 kB
SwapCached:            0 kB
Active:          2616120 kB
Inactive:        5767004 kB
Active(anon):     940016 kB
Inactive(anon):   285328 kB
Active(file):    1676104 kB
Inactive(file):  5481676 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:          1000 kB
SwapFree:           1000 kB
Dirty:                12 kB
Writeback:             0 kB
AnonPages:        930236 kB
Mapped:           126452 kB
Shmem:            295204 kB
Slab:             212100 kB
SReclaimable:     178636 kB
SUnreclaim:        33464 kB
KernelStack:        3456 kB
PageTables:        26704 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    15088408 kB
Committed_AS:    2897984 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      410736 kB
VmallocChunk:   34359323420 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:    1024
HugePages_Free:     1024
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       79872 kB
DirectMap2M:    32931840 kB

```Here is cat /proc/mtrr
```
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x800000000 (32768MB), size= 1024MB, count=1: write-back
reg02: base=0x0af800000 ( 2808MB), size=    8MB, count=1: uncachable
reg03: base=0x0b0000000 ( 2816MB), size=  256MB, count=1: uncachable
reg04: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg05: base=0x82fe00000 (33534MB), size=    2MB, count=1: uncachable
reg06: base=0x830000000 (33536MB), size=  256MB, count=1: uncachable
```Here is cat /proc/cpuinfo
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.62
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.07
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.09
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.07
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6822.07
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```Here is my dmidecode
```
# dmidecode 2.11
SMBIOS 2.6 present.
101 structures occupying 3566 bytes.
Table at 0x000EAFB0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1101
    Release Date: 11/23/2011
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 8192 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: System manufacturer
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    UUID: *******************************
    Wake-up Type: Power Switch
    SKU Number: To be filled by O.E.M.
    Family: To be filled by O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P8Z68-V PRO
    Version: Rev 1.xx
    Serial Number: *******************************
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Chassis Manufacture
    Type: Desktop
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Asset-1234567890
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
    Socket Designation: LGA1155
    Type: Central Processor
    Family: Core 2 Duo
    Manufacturer: Intel           
    ID: *******************************
    Signature: Type 0, Family 6, Model 42, Stepping 7
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz      
    Voltage: 1.0 V
    External Clock: 100 MHz
    Max Speed: 3800 MHz
    Current Speed: 3441 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 4
    Core Enabled: 1
    Thread Count: 2
    Characteristics:
        64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 kB
    Maximum Size: 1024 kB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 8192 kB
    Maximum Size: 8192 kB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 16-way Set-associative

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Keyboard
    Internal Connector Type: None
    External Reference Designator: PS/2 Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB9_10
    Internal Connector Type: None
    External Reference Designator: USB9_10
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB11_12
    Internal Connector Type: None
    External Reference Designator: USB11_12
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: GbE LAN
    Internal Connector Type: None
    External Reference Designator: GbE LAN
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AUDIO
    Internal Connector Type: None
    External Reference Designator: AUDIO
    External Connector Type: Other
    Port Type: Audio Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA1
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA2
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA3
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA4
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA5
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA6
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB1_2
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB3_4
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB5_6
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB7_8
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AAFP
    Internal Connector Type: Mini Jack (headphones)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CPU_FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CHA_FAN1
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PWR_FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PATA_IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: F_ESATA
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001D, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIEX16_1
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:01.0

Handle 0x001E, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIEX1_1
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.3

Handle 0x001F, DMI type 9, 17 bytes
System Slot Information
    Designation: PCIEX1_2
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.4

Handle 0x0020, DMI type 9, 17 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.6

Handle 0x0021, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Onboard Ethernet

Handle 0x0022, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.

Handle 0x0023, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0024, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: No Error
    Number Of Devices: 4

Handle 0x0025, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0026, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x007FFFFFFFF
    Range Size: 32 GB
    Physical Array Handle: 0x0024
    Partition Width: 1

Handle 0x0027, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Undefined   
    Serial Number: 0000000
    Asset Tag: AssetTagNum0
    Part Number: F3-10666CL9-8GBXL
    Rank: 2

Handle 0x0028, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0029, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x0027
    Memory Array Mapped Address Handle: 0x0026
    Partition Row Position: 1

Handle 0x002A, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Undefined   
    Serial Number: 0000000
    Asset Tag: AssetTagNum1
    Part Number: F3-10666CL9-8GBXL
    Rank: 2

Handle 0x002B, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x002C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00200000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x002A
    Memory Array Mapped Address Handle: 0x0026
    Partition Row Position: 1

Handle 0x002D, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Undefined   
    Serial Number: 0000000
    Asset Tag: AssetTagNum2
    Part Number: F3-10666CL9-8GBXL
    Rank: 2

Handle 0x002E, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x002F, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00400000000
    Ending Address: 0x005FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x002D
    Memory Array Mapped Address Handle: 0x0026
    Partition Row Position: 1

Handle 0x0030, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x0024
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Undefined   
    Serial Number: 0000000
    Asset Tag: AssetTagNum3
    Part Number: F3-10666CL9-8GBXL
    Rank: 2

Handle 0x0031, DMI type 18, 23 bytes
32-bit Memory Error Information
    Type: OK
    Granularity: Unknown
    Operation: Unknown
    Vendor Syndrome: Unknown
    Memory Array Address: Unknown
    Device Address: Unknown
    Resolution: Unknown

Handle 0x0032, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00600000000
    Ending Address: 0x007FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x0030
    Memory Array Mapped Address Handle: 0x0026
    Partition Row Position: 1

Handle 0x0033, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0034, DMI type 34, 11 bytes
Management Device
    Description: LM78-1
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port

Handle 0x0035, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0036, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0037, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0034
    Component Handle: 0x0034
    Threshold Handle: 0x0035

Handle 0x0038, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0039, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x003A, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0034
    Component Handle: 0x0037
    Threshold Handle: 0x0038

Handle 0x003B, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x0038
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x003C, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x003D, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0034
    Component Handle: 0x003A
    Threshold Handle: 0x003B

Handle 0x003E, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x0038
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x003F, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0040, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0034
    Component Handle: 0x003D
    Threshold Handle: 0x003E

Handle 0x0041, DMI type 29, 22 bytes
Electrical Current Probe
    Description: ABC
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0042, DMI type 36, 16 bytes
Management Device Threshold Data

Handle 0x0043, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0034
    Component Handle: 0x0040
    Threshold Handle: 0x003E

Handle 0x0044, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.
    Max Power Capacity: Unknown
    Status: Not Present
    Type: <OUT OF SPEC>
    Input Voltage Range Switching: <OUT OF SPEC>
    Plugged: Yes
    Hot Replaceable: No
    Input Voltage Probe Handle: 0x0035
    Cooling Device Handle: 0x003B
    Input Current Probe Handle: 0x0041

Handle 0x0045, DMI type 34, 16 bytes
Management Device
    Description: 2
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port

Handle 0x0046, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78B
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0047, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 7
    Upper Non-critical Threshold: 8
    Lower Critical Threshold: 8
    Upper Critical Threshold: 10
    Lower Non-recoverable Threshold: 11
    Upper Non-recoverable Threshold: 12

Handle 0x0048, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x0045
    Threshold Handle: 0x0046

Handle 0x0049, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78B
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x004A, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 13
    Upper Non-critical Threshold: 14
    Lower Critical Threshold: 15
    Upper Critical Threshold: 16
    Lower Non-recoverable Threshold: 17
    Upper Non-recoverable Threshold: 18

Handle 0x004B, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x0048
    Threshold Handle: 0x0049

Handle 0x004C, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78B
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x004D, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x004E, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x004B
    Threshold Handle: 0x004C

Handle 0x004F, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x004C
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x0050, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0051, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x004E
    Threshold Handle: 0x004F

Handle 0x0052, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78B
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0053, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0054, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x0051
    Threshold Handle: 0x0052

Handle 0x0055, DMI type 27, 14 bytes
Cooling Device
    Temperature Probe Handle: 0x0052
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating

Handle 0x0056, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0057, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x0054
    Threshold Handle: 0x0055

Handle 0x0058, DMI type 29, 22 bytes
Electrical Current Probe
    Description: DEF
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0059, DMI type 36, 16 bytes
Management Device Threshold Data

Handle 0x005A, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x0057
    Threshold Handle: 0x0055

Handle 0x005B, DMI type 29, 22 bytes
Electrical Current Probe
    Description: GHI
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x005C, DMI type 36, 16 bytes
Management Device Threshold Data

Handle 0x005D, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0045
    Component Handle: 0x005A
    Threshold Handle: 0x0055

Handle 0x005E, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.
    Max Power Capacity: Unknown
    Status: Not Present
    Type: <OUT OF SPEC>
    Input Voltage Range Switching: <OUT OF SPEC>
    Plugged: Yes
    Hot Replaceable: No
    Input Voltage Probe Handle: 0x0035
    Cooling Device Handle: 0x003B
    Input Current Probe Handle: 0x0041

Handle 0x005F, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard IGD
    Type: Video
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:02.0

Handle 0x0060, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard LAN
    Type: Ethernet
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:19.0

Handle 0x0061, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard 1394
    Type: Other
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:03:1c.2

Handle 0x0062, DMI type 139, 54 bytes
OEM-specific Type
    Header and Data:
        8B 36 62 00 00 1F C6 00 00 12 2A 06 04 04 32 55
        F8 00 A2 02 A1 00 40 63 43 10 FE 81 03 DF 40 B2
        00 20 00 73 3C 10 08 00 00 00 00 00 00 00 00 00
        00 00 00 00 00 01
    Strings:
        V1394GUID

Handle 0x0063, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 8
        eng
        fra
        spa
        ger
        rus
        chs
        chi
        jpn
    Currently Installed Language: eng

Handle 0x0064, DMI type 127, 4 bytes
End Of Table

```Any help of suggestions would be welcome because I have googled and so far come up empty handed.

Thanks in advance

---

### Post by aasdfasdfg on 2012-02-09
Are you running Ubuntu, or are you running Linaro? It looks like the version of the kernel you are using is from the 3.2 series, which has not hit vanilla Ubuntu users yet. Could you explain your setup briefly?

---

### Post by gnaservicesinc on 2012-02-10
I am running the development version, Ubuntu precise  12.04. I actually just did a clean install with the 2/9/2012 daily build because I got a new HDD.  The problem is the still their. 

If you have any more questions just let me know.

---

### Post by gnaservicesinc on 2012-02-10
It seems that turning the amount of RAM reserved for the GPU in the BIOS down to 256 fixes the problem, I had it set to 512 before.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930007](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930007)

---

