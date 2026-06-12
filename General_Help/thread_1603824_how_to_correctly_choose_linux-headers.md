---
title: "how to correctly choose linux-headers"
date: 2010-10-23
forum: General Help
---

### Post by psihokiller4 on 2010-10-23
I'd like to choose correct linux-headers but I'm blind here

it could be that I don't haave appropriete drivers for my machine (don't know)
it's true sound and video works but when it comes to gaming everything works soo slow and I get multy freezes from wine + "log out" problems with some games
not like from windows (dual boot)

now I saw some linux headers from synaptic but I don't know witch to choose as I'm afraid I could damage my OS again

```

military@dusanlaptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

```

---

### Post by drs305 on 2010-10-23
Are you looking for a specific header, or just want to install the one for your current kernel? If the latter:

In Synaptic's search bar, type in "linux-image" and see if it's installed (green check box). Note the kernel version. You may have "linux-image-generic" as well.

Now in a terminal, enter the following to see if your running kernel matches the "linux image" version:
```
uname -r
```
If the two versions match, install "linux-headers" / "linux-headers-generic", which will install the 'current' version.

If they don't match, pick the "linux-headers-2.6.3X..." that matches the version number from the uname command.

---

### Post by psihokiller4 on 2010-10-23
ok
synaptic:

linux-image: (installed)
```

alsa base
linux-image-2.6.31-14-generic
linux-image-2.6.31-22-generic
linux-image-generic
sane-utilis
xsane

```
uname -r

```

2.6.31-22-generic

```
synaptic:

linux-header: (installed)
```

libltdl-dev
libselinux1-dev
linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic
linux-headers-2.6.31-22
linux-headers-2.6.31-22-generic

```I found
synaptic:

linux-header: (not installed)
```

linux-headers-2.6.31-22-386
linux-headers-2.6.31-22-generic-pae

```linux-image: (not installed)
```

linux-image-2.6.31-22-386
linux-image-2.6.31-22-virtual

```should I install any of them?


ps.
I have 32 bit proc

---

### Post by drs305 on 2010-10-23
> **psihokiller4 said:**
> should I install any of them?

ps.
I have 32 bit proc

No. You are currently running the 2.6.31-22-generic kernel and have the associated linux headers installed.

Background only:
One note about 32-bit processors though. The PAE kernel will allow you to access higher amounts of RAM (4GB+) while the non-PAE kernel limits the amount of usable RAM. 

On new 32-bit installs, Ubuntu appears to automatically select the PAE kernel if it detects large amounts of RAM.

I only bring this up because there is a PAE header version available, but the PAE kernel isn't listed for you. It would only be something to investigate if you had a large amount of RAM...

---

### Post by psihokiller4 on 2010-10-23
ok thanks for informing me

---

