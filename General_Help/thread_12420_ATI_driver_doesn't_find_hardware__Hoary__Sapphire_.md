---
title: "ATI driver doesn't find hardware / Hoary / Sapphire Radeon 9600"
date: 2005-01-24
forum: General Help
---

### Post by ember on 2005-01-24
O.k. I'm bringing this up again with partial success. I have 2D-accleration via the fglrx-driver now, forcing chipset-id to 4E50 with
ChipID 0x4E50
in my XFree-Configfile.

However I cannot find any documentation of parameters for the kernel module, that still fails to load. And I haven't been able to locate the place where the Vendor-IDs are coded in the binary file (tried with ghex).

Anyone has a clue about that kernel params?

Best,
Ember


***

Hi,

I'm currently trying to install the new ATI-drivers on a relatively fresh Hoary install. Yet it seems, the driver doesn't recognize my Sapphire Card (Radeon 9600, AGP, 256 MB) as it prints out:

root@sleipnir:/usr/src/linux # modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.10-2-386/kernel/drivers/video/fglrx.ko): No such device

And dmesg gives me:

ata1: no device found (phy stat 00000000)
scsi0 : sata_sil
usb 2-1: khubd timed out on ep0in
ata2: no device found (phy stat 00000000)
scsi1 : sata_sil
usb 2-1: device descriptor read/64, error -110
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bb400009b11]
usb 2-1: khubd timed out on ep0in
usb 2-1: device descriptor read/64, error -110
usb 2-1: new full speed USB device using ohci_hcd and address 3
usb 2-1: khubd timed out on ep0in
usb 2-1: device descriptor read/64, error -110
usb 2-1: khubd timed out on ep0in
usb 2-1: device descriptor read/64, error -110
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02ed360(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8: BIOS error - no PSB
eth0: no IPv6 routers present
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
[fglrx] Maximum main memory to use for locked dma buffers: 805 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!


Additionally I ran lspci -v lately and got:
0000:02:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4e51 (prog-if 00 [VGA])
        Subsystem: PC Partner Limited: Unknown device 0200
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:02:00.1 Display controller: ATI Technologies Inc: Unknown device 4e71
        Subsystem: PC Partner Limited: Unknown device 0201
        Flags: 66MHz, medium devsel
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2


Any idea what I can do about that? 

Best,
ember

---

### Post by ember on 2005-02-13
(just pushing it up again in hope for someone to know this time)

---

