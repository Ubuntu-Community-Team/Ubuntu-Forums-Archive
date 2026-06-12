---
title: "HP Scanjet N6350"
date: 2011-12-01
forum: General Help
---

### Post by majalee on 2011-12-01
We have a HP Scanjet N6350 which can be used as a USB scanner as well as a network scanner. When I connect it to my system (Ubuntu 9.10 (64-bit) and execute the command, lsusb the result is this :

Bus 001 Device 004: ID 03f0:4805 Hewlett-Packard

the output the last two lines of "dmesg" is this :


[12262.510019] usb 1-2: new high speed USB device using ehci_hcd and address 5
[12262.685326] usb 1-2: configuration #1 chosen from 1 choice

but, xsane is unable to detect the scanner.

the output of "sane-find-scanner" was this :

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0, product=0x4805, chip=GL843?) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


============
I would be grateful if someone can help out. THanks in advance.

Aaditya

---

### Post by n1v0la on 2011-12-10
Hello [majalee]("http://ubuntuforums.org/member.php?u=215237").

Just a few ideas what you could try:

1.) Check /etc/sane.d/dll.conf
-> see if your scanner appears and whether it is commented out

2.) Add your user to the scanner and saned groups
-> sudo adduser "username" saned
-> sudo adduser "username" scanner

3.) Trying to get more information
-> use "lsusb -v" to get more info about your device
-> I think you could get additional info with lsscsi -v

4.) You might have to create a rules file in /etc/udev/rules.d
-> udevadm info -a -n "device" should give you detailed information that you can use to define your rule

I hope this helps a bit.

---

### Post by tyrian on 2012-02-05
Hi majalee, I am thinking of buying one of these scanners and wondered how you went?

I would prefer to hook the scanner directly to the network.  Did you try that at all?

---

