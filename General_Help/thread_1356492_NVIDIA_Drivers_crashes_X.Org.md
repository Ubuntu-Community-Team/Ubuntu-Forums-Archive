---
title: "NVIDIA Drivers crashes X.Org"
date: 2009-12-16
forum: General Help
---

### Post by alistair23 on 2009-12-16
I had this problem after upgrading from Ubuntu 8.10 to Ubuntu 9.04, but decided to wait until the next release to be bothered. I have now done a clean install of Ubuntu 9.10 (32-bit).

First I would like to say I am in Windows 7 on the same computer with NVIDIA drviers working, so there is nothing wrong with the card. I have a NVIDIA GeForce Go 7600 graphics card.

I originally installed the latest driver from the Restricted Hardware in Ubuntu, which was version 185. This caused a X.Org crash at boot, with no prompt, the OS went to a console login, which constantly flashed. I deleted the XOrg.conf file, using a live CD and then Ubuntu continued to boot.

I then installed The NVIDIA drivers by the package manager (I forget the name) and that gives the same console login. I even tried just turning on advanced effects, but that gives the same error.

I then decided to manually install the latest version from NVIDIA (version 195.42), which meant disabling X.Org and so on...
That gives me an error atleast, which says that

```
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) NVIDIA(0): Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0): additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
```

I was reading the Kernel log and it had reference to NVIDIA driver 173, which is not what I wanted to use. I then uninstaled every link to NVIDIA using the package manager. This then gave me an error saying that the NVIDIA module could not be loaded. I reinstalled the NVIDIA driver version 195.42 and returned to the error shown below.

```
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) NVIDIA(0): Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0): additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
```

I deleted the Xorg.conf to get back into Ubuntu and tried to remove the newest driver, except it does not show up under the package manager.

This is a Launch pad thread, which I have tried: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288626](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288626)
NOTE: I do have a TV tuner, which is not ever used.

---

### Post by alistair23 on 2009-12-20
This is the log from the Kernel:

```

[   21.633008] nvidia: module license 'NVIDIA' taints kernel.
[   21.924130] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   21.924146] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.924336] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.42  Tue Oct 20 20:18:32 PDT 2009

```

That is the first mention of the NVIDIA module and that is with the Xorg.conf deleted and Ubuntu booting normally (without a graphics driver).

---

