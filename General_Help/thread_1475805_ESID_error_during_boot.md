---
title: "ESID error during boot"
date: 2010-05-07
forum: General Help
---

### Post by Packrat73 on 2010-05-07
I get errors during boot here is the dmesg output


[  105.827461] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 172
[  105.827470] [drm:edid_is_valid] *ERROR* Raw EDID:
[  105.827479] <3>00 ff ff ff ff ff ff 00 22 64 25 03 ff ad 00 00  ........"d%.....
[  105.827485] <3>00 12 01 03 80 14 0b 78 0a 80 36 9a 5e 5d 91 28  .......x..6.^].(
[  105.827491] <3>20 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01   OT.............
[  105.827497] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[  105.827503] <3>45 00 c3 71 00 00 00 19 00 00 00 fd 00 37 41 22  E..q.........7A"
[  105.827509] <3>29 05 00 0a 20 20 20 20 20 20 00 00 00 fc 00 48  )...      .....H
[  105.827515] <3>53 44 30 38 39 49 46 57 31 0a 20 20 00 00 00 10  SD089IFW1.  ....
[  105.827520] <3>00 0a 20 20 20 20 20 20 20 20 20 20 20 20 00 74  ..            .t
[  105.827525] 
[  105.827531] i915 0000:00:02.0: LVDS-1: EDID invalid.

This is on an Asus EEE 900ha netbook with UNR 10.04 on it. I know this has something to do with the Intel video chipset, but I cant find a fix for it. Its a minor annoyance as it boots up after that fine and I dont seem to have any problems so far, but just checking to see if there was something I was or wasnt doing. This has the GMA 950 video chipset in it. THanks for any help

---

