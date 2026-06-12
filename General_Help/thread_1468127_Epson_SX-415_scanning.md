---
title: "Epson SX-415 scanning"
date: 2010-05-01
forum: General Help
---

### Post by telecoda on 2010-05-01
The one thing that has stopped me switching over to Ubuntu was getting my scanner to work.

I finally resolved this issue.  Here are the set I followed to get it working.

When trying to scan with XSane I would get the device not found alert.

Using the **sane-find-scanner** command would find the scanner as a USB device.

[I]found USB scanner (vendor=0x04b8, product=0x0851) at libusb:001:006
[/I]
I amended the "rules" file for xsane

/lib/udev/rules.d/40-libsane.rules

added the two following lines

[I]# Epson SX-415
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0851", ENV{libsane_matched}="yes"
[/I]
I also amended the /etc/sane.d/epson2.conf file 

# epson2.conf
#
# here are some examples for how to configure the EPSON2 backend

# SCSI
#scsi EPSON
# for the GT-6500:
#scsi "EPSON SC"

# Parallel port
#pio 0x278
#pio 0x378
#pio 0x3BC

# USB
usb

# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
usb 0x4b8 0x0851

# Network
# 
# net 192.168.1.123
#net autodiscovery

and restarted.  

Now I have a fully working colour scanner, bye bye windows ;)

---

### Post by Sparckus on 2010-05-01
Worked a treat, thanks :)

---

### Post by radek35 on 2010-09-01
Thank you very much, works like a charm:)

---

### Post by jgkellt001 on 2010-09-20
Excellent stuff. Thanks for such an easy quick solution. My scanner's up and running.

Cheers.

---

### Post by Chris Sharman on 2010-10-25
Ubuntu 10.10 - just added "usb 0x4b8 0x0851" to /etc/sane.d/epson2.conf (using sudo gedit /etc/sane.d/epson2.conf) and rebooted.

Don't appear to need the other edit.

Thanks
Chris

---

### Post by Roaban on 2011-01-09
Just added the line Chris Mentioned for Ubuntu 10.10 scanner now works a treat :)

---

### Post by Foxbat1155 on 2011-06-02
Worked for me so far, thankyou.

---

### Post by LondonSteve on 2012-01-22
I am loosing the will to live with this issue!! I have an Epson CX7400 that worked great with 8.04. I've spent days trying all solutions with Maverick 10.10. I just can't seem to get the scanner to work. Printer works great. I tried the idea above and to no avail.

WTF!!!!

lsusb output
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04b8:0838 Seiko Epson Corp. CX7300/CX7400/DX7400
Bus 001 Device 003: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

