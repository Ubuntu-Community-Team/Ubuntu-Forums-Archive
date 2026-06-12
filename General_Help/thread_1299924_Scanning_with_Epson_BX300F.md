---
title: "Scanning with Epson BX300F"
date: 2009-10-24
forum: General Help
---

### Post by gmh04 on 2009-10-24
Hello

I'm getting the error "Failed to start scanner: Operation not supported"
when I run attempt Acquire Preview in xsane, both as root and as normal user.

The scanner is being recognised:

$ sane-find-scanner
USB scanner (vendor=0x04b8, product=0x0848) at libusb:001:003

$ scanimage -L
device `epson:libusb:001:003' is a Epson NX300 flatbed scanner

And the permissions are correct:

$ ls -l /dev/bus/usb/001/003 
crw-rw-r-- 1 root scanner 189, 2 2009-10-24 17:24 /dev/bus/usb/001/003

I'm running Ubuntu 9.04.

Any thoughts, appreciated?

Cheers

---

### Post by gmh04 on 2009-10-25
I found the problem.

Install the iscan driver at

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

update /etc/sane.d/epkowa.conf with the line

```
usb 0x04b8 0x0848
```

select the epkowa driver when xsane starts up.

---

### Post by tuiger on 2010-07-28
Hallo


I downloaded and installed the .deb file for my machine, but I don't have a **epkowa.conf** configurationfile in /etc/sane.d/ where I can copy the code
```
usb 0x04b8 0x0848
```

What else I did:

After installing the downloaded file iscan must be in the file / etc / sane.d / dll.conf under the entry "epson(2)" epkowa type (with root-right) and save. Look after the file  / lib / udev/rules.d/40-libsane.rules following entries are added:

# Epson stylus BX300F
ATTRS{idVendor}==&#8221;04b8&#8243;, ATTRS{idProduct}==&#8221;0848&#8243;, ENV{libsane_matched}=&#8221;yes&#8221;

Finally, a restart of the system and the scanner (Epson Stylus BX300F) still dosn't works  

Thank you for help :D:D

---

### Post by retrozoneorg on 2010-07-30
Hi There,

I have tried everything in these posts.
I have altered the epkowa.conf, dll.conf & epson2.conf files with the code from these posts but Xsane can still not find the scanner.

According to the xsane website the printer and scanner are supported.
Has anyone figured out how to enable scanning for the BX300F yet?

Please let me know... This is the 3rd time I've tried to convert to linux (2nd time for ubuntu) and away from M$. I need this scanner for work use and if I can't get it working I will have to go back to XP.

---

### Post by ellgor on 2010-07-31
Hi,

If you have downloaded the Imagescan app use that instead of Xsane, works perfectly well by itself, its icon will be in the graphics section or start it from a terminal, 

sudo imagescan

Regards, Ellgor.

---

