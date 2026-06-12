---
title: "the disappearing desktop"
date: 2009-11-03
forum: General Help
---

### Post by jerome schatten on 2009-11-03
I have configured a new machine as follows:
Asus P5Q-EM-DO MoBo with Intel EB8400 dual core processor
4 GB Ram; 2ea 500 GB SATA2 HD's and a Pioneer DVR-218-R SATA drive
(sr0). Windows XP on one hd sda; Ubuntu 9.10 on sdb1 and 9.04 on sdb3.

Grub is the bootloader; all three systems work flawlessly except for one
thing:

Ubuntu (either 9.10 or 9.04) will NOT play an audio CD without segfaulting according to dmesg.

It works OK with windows and it works ok with data CD's with Ubuntu.
Here's what happens:

Ubuntu boots up. All is well. Put a CD in the tray, and the drive starts
to work. In about 5 seconds, all of the icons on the desktop disappear
-- gonzo!  Nothing but the panels are left. I tried bringing 'em back, but
nada. If I bring up Banshee, it will play the CD. Although the icons are
gone, the menus still work and you can more or less carry on.

If I bring up a terminal, I can kill the Xorg process and force Xorg to
restart, at which point the icons come back. If the disk is still in the
tray, the icons disappear a few seconds later. If the disk is not in the
tray, everything is normal.

dmesg looks like it's capturing a segfault event, but I'm not skilled
enough to make a whole lot of sense out of what it's telling me.

Here's what dmesg is saying after the CD is inserted:

[  562.258333] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  562.258338] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  562.258343] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  562.258348] end_request: I/O error, dev sr0, sector 128
[  562.258353] Buffer I/O error on device sr0, logical block 16
[  562.258357] Buffer I/O error on device sr0, logical block 17
[  562.258360] Buffer I/O error on device sr0, logical block 18
[  562.258363] Buffer I/O error on device sr0, logical block 19
[  562.258366] Buffer I/O error on device sr0, logical block 20
[  562.258368] Buffer I/O error on device sr0, logical block 21
[  562.258371] Buffer I/O error on device sr0, logical block 22
[  562.258373] Buffer I/O error on device sr0, logical block 23
[  562.258376] Buffer I/O error on device sr0, logical block 24
[  562.258378] Buffer I/O error on device sr0, logical block 25
[  562.259784] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  562.259788] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  562.259792] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  562.259798] end_request: I/O error, dev sr0, sector 128
[  562.434999] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  562.435004] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  562.435009] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  562.435015] end_request: I/O error, dev sr0, sector 0
[  562.436634] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  562.436638] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  562.436642] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  562.436647] end_request: I/O error, dev sr0, sector 0
[  562.438655] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  562.438659] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  562.438663] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  562.438668] end_request: I/O error, dev sr0, sector 0
[  568.680740] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  568.680744] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  568.680749] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  568.680755] end_request: I/O error, dev sr0, sector 128
[  568.680758] __ratelimit: 14 callbacks suppressed
[  568.680761] Buffer I/O error on device sr0, logical block 16
[  568.680766] Buffer I/O error on device sr0, logical block 17
[  568.680768] Buffer I/O error on device sr0, logical block 18
[  568.680771] Buffer I/O error on device sr0, logical block 19
[  568.680774] Buffer I/O error on device sr0, logical block 20
[  568.680777] Buffer I/O error on device sr0, logical block 21
[  568.680779] Buffer I/O error on device sr0, logical block 22
[  568.680782] Buffer I/O error on device sr0, logical block 23
[  568.680785] Buffer I/O error on device sr0, logical block 24
[  568.680787] Buffer I/O error on device sr0, logical block 25
[  568.716024] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  568.716029] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  568.716033] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  568.716039] end_request: I/O error, dev sr0, sector 128
[  569.435393] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  569.435398] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  569.435402] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  569.435408] end_request: I/O error, dev sr0, sector 0
[  569.510380] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  569.510385] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  569.510390] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  569.510396] end_request: I/O error, dev sr0, sector 0
[  569.585242] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  569.585247] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  569.585251] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  569.585257] end_request: I/O error, dev sr0, sector 0
[  584.744952] __ratelimit: 14 callbacks suppressed
[  584.744957] nautilus[27995]: segfault at 931d008 ip 00e2fae0 sp
b43e7f10 error 4 in libbrasero-media.so.0.2.0[e1f000+24000]
[  624.997243] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  624.997248] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  624.997252] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  624.997258] end_request: I/O error, dev sr0, sector 128
[  624.997261] Buffer I/O error on device sr0, logical block 16
[  625.167684] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  625.167689] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  625.167693] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  625.167699] end_request: I/O error, dev sr0, sector 0
[  625.167703] Buffer I/O error on device sr0, logical block 0
[  625.169525] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  625.169530] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  625.169533] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  625.169539] end_request: I/O error, dev sr0, sector 0
[  625.169541] Buffer I/O error on device sr0, logical block 0
[  660.558419] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  660.558424] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  660.558428] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  660.558434] end_request: I/O error, dev sr0, sector 128
[  660.558438] Buffer I/O error on device sr0, logical block 16
[  660.750047] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  660.750052] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  660.750057] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  660.750062] end_request: I/O error, dev sr0, sector 0
[  660.750067] Buffer I/O error on device sr0, logical block 0
[  660.753398] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE
[  660.753402] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[  660.753406] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  660.753411] end_request: I/O error, dev sr0, sector 0
[  660.753415] Buffer I/O error on device sr0, logical block 0

Suggestions appreciated!
jerome

---

### Post by jerome schatten on 2009-11-10
Well it was a config problem. I thought everything worked ok under XP, but when I tried to copy an audio CD, XP hung. I brought the new machine back to the dealer whom I know personally, and he did the following:

1. Replaced the optical drive with one that could support both IDE and SATA and hooked it up as an IDE drive;
2. Using AHCI, set up the two SATA HD's as emulated PATA drives (not sure if I have all the terminology correct).

According to my man, little or no effect on performance. All systems happy. 

My thanks to those that took the time to have a look at the problem, even though no-one responded. I hope this helps someone else!

jerome

---

