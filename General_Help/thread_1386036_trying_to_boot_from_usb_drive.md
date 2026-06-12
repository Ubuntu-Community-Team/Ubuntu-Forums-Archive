---
title: "trying to boot from usb drive"
date: 2010-01-20
forum: General Help
---

### Post by proevofanatik on 2010-01-20
im trying to boot from my usb drive to boot up kubuntu 9.10.

but i cant seem to get it to work. ive tried it on other pcs and ive managed to change the boot device in bios and get it booted. but on this certain pc i cant get it booted.

here are the boot options i have.

floppy
LS120
HDD-0
SCSI
CDROM
HDD-1
HDD-2
HDD-3
ZIP100
USB-FDD
CARD READER
USB-CDROM
USB-HDD
LAN
DISABLED

ive tried usb-fdd and usb hdd and both dont work

please help

---

### Post by oldfred on 2010-01-20
On my desktop I had a lot of choices like that and tried every USB one and nothing worked. I gave up but left it plugged in. Several days later I chose boot from hard drive in BIOS and there it was. It was a hard drive not a USB device even though it was a USB.

---

### Post by mechro on 2010-01-20
> **oldfred said:**
> ... It was a hard drive not a USB device even though it was a USB.

Yeah, that's a bit like my BIOS. There is an item to choose First/Second/Third Boot device but there's also an item to select Hard Disk Boot Priority and my USB drive turns up in there.

---

### Post by proevofanatik on 2010-01-20
> **mechro said:**
> Yeah, that's a bit like my BIOS. There is an item to choose First/Second/Third Boot device but there's also an item to select Hard Disk Boot Priority and my USB drive turns up in there.

yes m8 that happened on the other pc i tried. that one worked no problem. this pc tho has a different bios. ill need to try all the other hard drive ones.
ill let you know how i get on. it might not be tonight as its my works pc that im trying to do it to. and im finnishing soon.

---

### Post by proevofanatik on 2010-01-20
ok i tried all hard drive options and none worked. whats very strange too is i disabled all boot devices and it still boots from the hard drive. the grub loader loads up with my dual boot every time.

any ideas?

---

### Post by mechro on 2010-01-20
Try a different usb cable? Try a different usb socket?

If you post your pc's spec and BIOS program then somebody with the same kit might chip in with a solution.

---

