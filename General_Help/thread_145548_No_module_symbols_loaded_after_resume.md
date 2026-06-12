---
title: "No module symbols loaded after resume"
date: 2006-03-16
forum: General Help
---

### Post by anandrd on 2006-03-16
I am getting this intermittent problem on my Kubuntu Breezy (with 686 kernel) on Dell Inspiron 6000.

Suspend/Resume works fine most of the time but once in a while, the laptop fails to resume. I get a blank screen. Neither Ctrl+Alt+Backspace nor Ctrl+Alt+Del works and I have to do a hard reboot. /var/log/kern.log shows the following lines (which are absent for successful resumes)

```
 
Mar 16 09:33:37 localhost kernel: Inspecting /boot/System.map-2.6.12-10-686
Mar 16 09:33:38 localhost kernel: Loaded 28233 symbols from /boot/System.map-2.6.12-10-686.
Mar 16 09:33:38 localhost kernel: Symbols match kernel version 2.6.12.
Mar 16 09:33:38 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Mar 16 09:33:38 localhost kernel: ort range 0x10c0-0x10df has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:07: ioport range 0x900-0x90f has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:07: ioport range 0x910-0x91f has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:07: ioport range 0x920-0x92f has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:07: ioport range 0x930-0x93f has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:07: ioport range 0x940-0x97f has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0x7b0-0x7bb has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0x7c0-0x7df has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0xbb0-0xbbb has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0xbc0-0xbdf has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0xfb0-0xfbb has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0xfc0-0xfdf has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0x13b0-0x13bb has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] pnp: 00:0a: ioport range 0x13c0-0x13df has been reserved
Mar 16 09:33:38 localhost kernel: [4294672.278000] Simple Boot Flag at 0x79 set to 0x1

```

---

### Post by anandrd on 2006-03-18
UPDATE:

The problem doesn't seem to be with module symbols or anything. I always get tht message when I boot. The problem seems to be with ACPI and I have posted it in the main Ubuntu forums [http://www.ubuntuforums.org/showthread.php?p=838198#post838198](http://www.ubuntuforums.org/showthread.php?p=838198#post838198)

---

