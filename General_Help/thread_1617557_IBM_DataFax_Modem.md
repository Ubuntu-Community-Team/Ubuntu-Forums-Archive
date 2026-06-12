---
title: "IBM Data/Fax Modem"
date: 2010-11-09
forum: General Help
---

### Post by peyre on 2010-11-09
I'm setting up this old laptop.  It has a built-in Agere WinModem, which I got working (woohoo--thanks martian!).  But I also have an IBM Data/Fax Modem FRU 04K0054 (originally X2, but flashed to V.90), which would be a nice extra to have around as a backup.  It doesn't seem to install though, even if it was plugged in before bootup.  Here's my lspci readout:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/MX-MV (rev 11)
```

---

