---
title: "MAME Version .119"
date: 2011-06-21
forum: General Help
---

### Post by EMABrad on 2011-06-21
I'll keep this short and sweet.  The ROMs that I have I KNOW work for version .119, because it works on Windows.  NONE of them work for .139 (they're all missing something or another), OR I'm just doing something wrong, so I want to get .119, but I just can't find it.

They're Neo Geo ROMs, and I have the Neo Geo BIOS.  Help/suggestions?

---

### Post by veggen on 2011-06-21
I googled a bit and wasn't very successful... Have you tried finding the newer ROM versions? That usually helped me.

---

### Post by EMABrad on 2011-06-21
I've tried, but I don't know where or HOW I could get "new" ROM versions.  I'm aiming for primarily the Neo Geo fighting games.

---

### Post by EMABrad on 2011-06-21
When I run "mame -verifyroms kof2002", for example, I get the following:

```
kof2002 : 000-lo.lo (131072 bytes) - INCORRECT LENGTH: 65536 bytes
kof2002 : sfix.sfix (131072 bytes) - NOT FOUND (BIOS)
kof2002 : sp1.jipan.1024 (131072 bytes) - NOT FOUND (BIOS)
kof2002 : sp-45.sp1 (524288 bytes) - NOT FOUND (BIOS)
kof2002 : japan-j3.bin (131072 bytes) - NOT FOUND (BIOS)
kof2002 : sp-1v1_3db8c.bin (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_2_3.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_2_3o.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_2_2.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_2_1.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_2_0.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_1_3.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_1_2.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_1_2o.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_1_1.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : uni-bios_1_0.rom (131072 bytes) - NOT FOUND (BIOS)
kof2002 : sm1.sm1 (131072 bytes) - INCORRECT CHECKSUM:
EXPECTED: CRC(94416d67) SHA1(42f9d7ddd6c0931fd64226a60dc73602b2819dcf)
   FOUND: CRC(97cf998b)
romset kof2002 [neogeo] is bad
1 romsets found, 0 were OK.

```

Basically every single thing that could possibly be wrong is wrong.

---

### Post by EMABrad on 2011-06-21
It basically says that for every ROM.

---

### Post by EMABrad on 2011-06-21
Solved!  I apparently had an old Neo Geo BIOS.  If anyone else has this problem, the new BIOS can be found here: [http://rghost.net/2341022](http://rghost.net/2341022)

---

