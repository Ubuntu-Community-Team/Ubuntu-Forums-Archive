---
title: "ComplactFlash adapter for PC Card"
date: 2010-11-09
forum: General Help
---

### Post by peyre on 2010-11-09
I'm setting up my laptop with Lubuntu LTS (10.10 causes trouble on this machine).  I have an SIIG CompactFlash card adapter for the PC-Card bay, which is handy for saving files now and then.  The usual story: it works great in Windows but *buntu doesn't recognize it--whether it's in the drive on bootup or whether I insert it later.  It just never shows in Thunar or PCManFM (it has a 1GB CF card inserted).  Is there something I should be doing that I haven't been?  lspci (with the CF adapter inserted prior to bootup) gives me:

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

### Post by cavalier911 on 2010-11-10
A PCMCIA CF adapter is not going to show in thunar or pcmanfm.
Put flash card that has files on it in adapter inserted in PCMCIA socket.
Now BOOTUP
Open terminal:
```
fdisk -l
```
You should see the flash card as another drive,usually /dev/hde
```
sudo mkdir /mount.folder
```
```
sudo mount /dev/hde   /mount.folder
```
```
ls /mount.folder
```
Should see the contents of the flash card.
If this fails:
Don't shut down,leave things as they are. 
Post the output from: sudo lsmod 
                      sudo pccardctl insert
                      sudo pccardctl info 
                      sudo pccardctl ident
                      sudo pccardctl status

Open another terminal window 
Post output relevant to flash card from dmesg

---

### Post by peyre on 2010-11-11
Wow, thanks!!  fdisk -l worked like a charm.  It made the adapter appear in my file managers right away.  The change even stuck after rebooting.

---

