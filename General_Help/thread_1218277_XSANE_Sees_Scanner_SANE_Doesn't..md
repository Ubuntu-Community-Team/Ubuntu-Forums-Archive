---
title: "XSANE Sees Scanner SANE Doesn't."
date: 2009-07-20
forum: General Help
---

### Post by lvleph on 2009-07-20
I have an HP PSC 1510 All in one printer scanner. XSANE is able to see and scan, but sane is not. I cannot figure out what the problem is.

---

### Post by lvleph on 2009-07-20
Bump

---

### Post by lvleph on 2009-07-21
Bump.

---

### Post by SuperSonic4 on 2009-07-21
xsane is a frontend to sane so sane can see it. Perhaps it's something to do with the driver

---

### Post by lvleph on 2009-07-21
Result of sane-find-scanner
```
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0, product=0x4c11) at libusb:005:003
found USB scanner (vendor=0x0471, product=0x0815) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
Result of sudo scanimage -L
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```
So SANE does find it, but scanimage doesn't.

EDIT:

/etc/sane.d/hp.conf
```
scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
# USB-scanners supported by the hp-backend
# HP ScanJet 4100C
usb 0x03f0 0x0101
# HP ScanJet 5200C
usb 0x03f0 0x0401
# HP ScanJet 62X0C
usb 0x03f0 0x0201
# HP ScanJet 63X0C
usb 0x03f0 0x0601
# HP PSC1510
usb 0x03f0 0x4c11
#
# Uncomment the following if your scanner is connected by USB,
# but you are not using libusb
# /dev/usb/scanner0
#   option connect-device
```

/etc/sane.d/dll.conf
```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epson
epson2
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

hpoj
hpaio
```

---

### Post by lvleph on 2009-07-21
delete

---

### Post by lvleph on 2009-07-22
Someone must know what the problem is.

---

### Post by lvleph on 2009-07-22
Okay I am getting closer. Using sudo I get more results.

sudo sane-find-scanner
```
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x4c11 [PSC 1500 series]) at libusb:005:003
found USB scanner (vendor=0x0471 [Philips], product=0x0815 [eHome Infrared Transceiver]) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

sudo scanimage -L seems to hang.

EDIT: Eventually, sudo scanimage -L results in
```
device `hpaio:/usb/PSC_1500_series?serial=MY59AD93X00498' is a Hewlett-Packard PSC_1500_series all-in-one

```

Now I need to get scanimage -L to see it.

---

### Post by lvleph on 2009-07-23
Here was the solution to my problem.
```

sudo chmod 777 /dev/bus/usb/005/003
```

---

