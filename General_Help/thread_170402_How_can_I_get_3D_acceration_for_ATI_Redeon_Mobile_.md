---
title: "How can I get 3D acceration for ATI Redeon Mobile 9200 IGP?"
date: 2006-05-04
forum: General Help
---

### Post by cloudeye on 2006-05-04
I v work on it for week but still no luck. :(

Ubuntu 5.10, Notebook Toshiba Satellite A20
Ubuntu tells that I have a video card ATI Radeon Mobility 9200 IGP (Rv250), but after I install xorg-driver-fglrx from repository and load fglrx in Xorg.conf, X fail to start, complain that "No such device".
So I add chipID to xorg.conf as below:

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	ChipID		0x5835
EndSection

This time xorg recognize that the video card is a Radeon Mobile 9100 IGP and X start, but still no 3D:

(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Anyone help, thanks. 
Xorg.0.log attached.

---

### Post by cloudeye on 2006-05-05
~~~~

---

### Post by richbarna on 2006-05-05
I,m not sure you can get acceleration for ATI, in fact, so many people (including me) sacrifised the acceleration by using the "vesa" driver instead of "ati" because of ati driver problems.

---

