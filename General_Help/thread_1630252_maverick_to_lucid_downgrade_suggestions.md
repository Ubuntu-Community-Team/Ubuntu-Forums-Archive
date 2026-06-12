---
title: "maverick to lucid downgrade suggestions"
date: 2010-11-24
forum: General Help
---

### Post by acadios on 2010-11-24
maverick is the is the OS that should of never made it past **Release Candidate**.

I know Canonical wants to release a new version of Ubuntu every 6 months, but WOW, maverick is crashing on anything, it's not fit to call a **Release**.

I can tolerate some bugs in a Linux OS, but I doubt maverick will be fit for use any-time soon.

I'm downloading the Lucid 10.04 LTS Desktop CD even as I'm typing this.

Any suggestions for downgrading short of reformatting my EXT4 partition?

It's not just me, this new Ubuntu release has a lot of users agitated & annoyed from what I've read via Google searches.

---

### Post by Quackers on 2010-11-24
Welcome to UF.
It may be your pc has issues with Maverick.
I know of no way to downgrade. I believe a re-install is the only way.

---

### Post by boot_sectorz on 2010-11-24
I don't think it is just his PC, because you will have to add mine and my mates laptop! Seriously, I have never had such random freezes. My own post has had no solution and I'm downloading 10.04! I have had the worse experience with this 'Release' than any other OS.

---

### Post by acadios on 2010-11-24
> **Quackers said:**
> Welcome to UF.
It may be your pc has issues with Maverick.
I know of no way to downgrade. I believe a re-install is the only way.
Ubuntu lucid & karmic ran fine on my Samsung netbook, which by the way is pretty standard hardware by now.

From what the Google searches show me, maverick 10.10 is unstable across the board for every version, Ubuntu, Kubuntu, 32bit, 64bit, etc... etc...

A reinstall is fine by me, as long as it preserves my home folder.

---

### Post by Quackers on 2010-11-24
From what I've read, regular freezes tend to be as a result of ram problems, HDD problems or graphics driver problems. I could be wrong, of course, that's happened before :-)

---

### Post by acadios on 2010-11-24
I've been getting those random freezes too that crash maverick too.

If I wasn't using a netbook, then sure I'd agree maybe it's the hardware, but this netbook ran perfectly fine on lucid.  My netbook is pretty typical netbook hardware that requires NO special drivers.

lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by Artemis3 on 2010-11-24
Backup /home and reinstall (unless yours is in a separate partition and you do know how to manual partition in the install).

No problems with 10.10 in 7+ machines i use/know, including netbook/laptops. I know you might have problems with 10.10 if your video is intel 8xx.., some other hardware is problematic due to lack or obsolete support.

---

### Post by Quackers on 2010-11-24
Actually another cause can be the fan not working or not working hard enough which can lead to the processors' shutdown due to overheating. This can be an acpi problem, amongst other things.

---

### Post by boot_sectorz on 2010-11-25
I have downgraded to 10.04, so far, been running for 8hrs with not problem!
I'm still wondering what 10.10 has which made it so unstable!

---

