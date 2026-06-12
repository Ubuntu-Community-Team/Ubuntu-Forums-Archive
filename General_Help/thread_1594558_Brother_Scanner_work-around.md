---
title: "Brother Scanner work-around"
date: 2010-10-12
forum: General Help
---

### Post by Mark_in_Hollywood on 2010-10-12
I have a Brother MFC-240C inkjet printer & scanner. On installation of Maverick Meerkat v. 10.10, my scanner function failed.

I added the same line into the file as for Lucid Lynx v. 10.04 and the scanner has scanned perfectly.

The lines Brother gives are for the following file:

Ubuntu 9.10, 10.04
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

above is found at:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

---

### Post by jandriel on 2010-10-16
I've had the same problem with getting mine working on 10.10, too. Worked very well in 10.04, and I'm not sure what might have changed this functionality between these versions.

Some instructions say that since one of the Ubuntu 9.x versions, the Brother instructions are out of date as some files were moved. I've been digging around for what that might be, but have had no luck.

---

### Post by colossus73 on 2010-10-18
It's a S H A M E that every time a new version of Ubuntu comes out there are regressions like this! I have the same problem while on 9.04 it worked!

By the I followed the above but still even root can't see the scanner:


gt[~]$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x018c) at libusb:001:004

But then:
gt[~]$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
gt[~]$

gt[~]$ tail /lib/udev/rules.d/40-libsane.rules
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5105", ENV{libsane_matched}="yes"
# Dell Dell MFP Laser Printer 1815dn
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5124", ENV{libsane_matched}="yes"
# Dell 1600n
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes"
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power/level && echo on > /sys/$env{DEVPATH}/power/level'"
LABEL="libsane_rules_end"
gt[~]$

---

### Post by zazootheparrot on 2010-11-07
I have exactly the same problem with my scanner. I've recently upgrade to 10.10 but it used to work fine on 10.04 :((

Any help?
Thanks in advace

Device: DCP-375CW
Laptop: Sony Vaio VGN-SZ740

---

### Post by colossus73 on 2010-11-07
> **zazootheparrot said:**
> 
Any help?
Thanks in advace


Yes. I discovered that the brscan2 DEB package MUST be downloaded and installed from Brother web site ;)

Bye,

---

### Post by robbielink on 2010-11-22
**Update** - solved for me, now.
My model uses brscan2 which I have had installed all along. I checked installed packages and found that brscan was also installed. Synaptic says this is the CUPS package but it is actually another version of the scanner package for different models. You can't have 2 installed. Removing brscan solved the problem. I don't know how it got installed - possibly as part of my update to Maverick. I did not install it myself.

NOT solved for me. I have the same output as in Post #3. 
sane-find-scanner correctly finds my scanner.
scanimage -L says no scanners were identified
doesn't work as root, either.
group settings are correct.
I have the correct line in 40-libsane-rules
I've reinstalled the brscan2 deb package.

Everything worked great in 10.04 - upgrade to 10.10 killed scanner though printer still works fine.

Brother MFC 420CN on USB

---

### Post by scottie_z on 2011-03-22
I got mine working by installing new drivers from Brother's website.  Uninstall your existing packages, and then get the ones released on 2011.Feb.04.

---

### Post by the.jxc on 2012-01-01
I had the same problem with my DCP-250C when upgrading from 9.04 32-bit to 11.10 (Oneiric Ocelot) under 64-bit.  

It had worked pretty well with the Brother brscan2 32-bit driver.  However, it no longer worked after a clean install of 11.10 64-bit with the 64-bit brscan2 driver.

I found the problem.  The brscan2 package had installed the drivers into /usr/lib64/sane (all by themselves) instead of /usr/lib/sane (where the other sane drivers live).

Here is a cheat sheet for full instructions on installing brscan2 under Oneiric Ocelot 64-bit.  Perform ALL actions as root:

1) Download and install ONE ONLY of brscan/brscan2/brscan3 drivers from 

```
http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html
```

Ensure that you have the 64-bit driver.  Ensure you have the brscan package to match your device.

```
# dpkg --install brscan2-0.2.5-1.amd64.deb
```

2) Check that your device is connected.

```
# sane-find-scanner
found USB scanner (vendor=0x04f9, product=0x01d0) at libusb:001:006
```

Your product number will differ if you don't have the same model as me.


3) Add your device to the usb RULES file.

```
# vi /lib/udev/rules.d/40-libsane.rules
```

(at end of libsane_matched rules, add line)

```
# Brother scanner DCP-350C
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01d0", ENV{libsane_matched}="yes"
```

Use YOUR matching vendor and product IDs, of course!


4) Check that the Brother DLL has been added to the list by the package install.

```
# tail -1 /etc/sane.d/dll.conf
brother2
```

(Should say "brother2" as the last line)


4) REBOOT!


5) Now at this point, you would be able to scan as "root" under 32-bit.  However, under 64-bit the driver dll is probably in the wrong directory.  Let's demonstrate that.

```
# export SANE_DEBUG_DLL=128
# scanimage -L
```

The output may say:

```
[dll] load: trying to load `/usr/lib/sane/libsane-brother2.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-brother2.so.1' (No such file or directory)
```

and

```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

If so, you have the problem that I found.  It's easy to fix!

6) Link the driver to the correct directory.

```
cd /usr/lib
ln -s ../lib64/libbrscandec2.so.1.0.0 .
ln -s ../lib64/libbrcolm2.so.1.0.1 .
ln -s ../lib64/libbrcolm2.so .
ln -s ../lib64/libbrscandec2.so.1 .
ln -s ../lib64/libbrscandec2.so .
ln -s ../lib64/libbrcolm2.so.1
cd sane
ln -s ../../lib64/sane/libsane-brother2.so.1.0.7 .
ln -s ../../lib64/sane/libsane-brother2.so.1 .
ln -s ../../lib64/sane/libsane-brother2.so .
```

Now try again.

```
# scanimage -L
device `brother2:bus5;dev2' is a Brother DCP-350C USB scanner
```

You should now be able to scan as root user.  Now just follow the instructions provider by Brother on how to make the usb device world readable so that normal users can scan too.

---

### Post by Tristan Schmelcher on 2012-03-10
Thanks the.jxc, your post helped me get my Brother MFC-7220 / brscan2 scanner working on Oneiric 64-bit. In my case, I was able to scan as both root and non-root without any additional work.

FYI for others, instead of rebooting in step 4 can also just run "sudo udevadm control --reload-rules" and then unplug and re-plug the device.

Also, instead of making all those symlinks manually in step 6, you can just uninstall brscan2, create one symlink with "ln -sT /usr/lib /usr/lib64", and then reinstall brscan2. That symlink used to be there in previous versions of Ubuntu, which is why this problem only started recently.

---

### Post by martinro on 2012-05-02
> **Tristan Schmelcher said:**
> Thanks the.jxc, your post helped me get my Brother MFC-7220 / brscan2 scanner working on Oneiric 64-bit. In my case, I was able to scan as both root and non-root without any additional work.

FYI for others, instead of rebooting in step 4 can also just run "sudo udevadm control --reload-rules" and then unplug and re-plug the device.

Also, instead of making all those symlinks manually in step 6, you can just uninstall brscan2, create one symlink with "ln -sT /usr/lib /usr/lib64", and then reinstall brscan2. That symlink used to be there in previous versions of Ubuntu, which is why this problem only started recently.
Tristan - this also fixed same problem with Brother DCP 7010 with brscan2 under Ubuntu 12.04 64 bit

Thanks

---

### Post by Paulgirardin on 2012-08-19
This worked for me too.
Ubuntu 12.04 AMD64
Brother MFC 3220 C
driver: brscan 

Cheers

---

