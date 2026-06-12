---
title: "GUI broken after xorg-edgers radeon install, then system updates"
date: 2012-07-19
forum: General Help
---

### Post by sabersong on 2012-07-19
I broke my GUI.

I'm using Kubuntu 12.04.

Trying to get Lord of the Rings Online working under wine last night, I got it mostly running, but it was really choppy. I found a suggestion on Google about installing the radeon package from xorg-edgers ppa, which made the problem better but didn't fix it.

This morning I was notified of system updates, most of which involved xorg. I applied the update, restarted my computer, and immediately ran into trouble. The KDE splash screen (may not be the right terminology) --- the one with the gear and the blue dots that turn white as the system loads --- came up fine, but then it dropped into a terminal session. If I let it sit, the screen that tells me what's loaded flashes on for a second, then drops back to terminal. Eventually, I hit CTRL+C to stop that from happening, and stay in terminal mode.

dmesg does report errors:
```

[   13.938727] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160(bits) (20120320/dsopcode-236)
[   13.983747] ACPI Error: Method parse/execution failed [\_sb_.WMID.HWCD] (Node ffff880101e02d0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   13.983772] ACPI Error: Method parse/execution failed [\_sb_.WMID.WMAD] (Node ffff880101e0b18), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   13.985503] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160(bits) (20120320/dsopcode-236)
[   13.985521] ACPI Error: Method parse/execution failed [\_sb_.WMID.HWCD] (Node ffff880101e02d0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   13.985546] ACPI Error: Method parse/execution failed [\_sb_.WMID.WMAD] (Node ffff880101e0b18), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   14.084622] microcode: failed to load file amd-ucode/microcode_amd.bin
[   14.084649] microcode: CPU1: patch_level=0x05000101
[   14.255969] microcode: failed to load file amd-ucode/microcode_amd.bin
[   14.256102] microcode: Microcode Update Driver: v2.00 <tigran@aivazain.fsnet.co.uk>, Peter Oruba
[  14.327498] kvm: disabled by bios
[  14.411743] r8169 000:06:00:0: link down
[  14.412937] IPv6 ADDRCONF(NETDEV_UP): eth0: link is not ready
[  14.413794] IPv6 ADDRCONF(NETDEV_UP): eth0: link is not ready
[  14.461770] kvm: disabled by bios
[  16.496437] init: plymouth-stop pre-start process (1395) terminated with status 1
```

The laptop is an HP 2000, with AMD E-300 APU.

I don't know how to revert to before i did the update this morning, but I think I'll avoid xorg-edgers until Iknow more about what I'm doing. In the meantime, any suggestions as to how I might fix this?

---

### Post by dino99 on 2012-07-19
purge edgers ppa :

[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

as you got acpi errors, the latest kernel has fixed lot of them, so install it from this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

and check workaround about the game on winehq database

---

### Post by sabersong on 2012-07-19
Thanks, dino! My system's working normally again.

---

