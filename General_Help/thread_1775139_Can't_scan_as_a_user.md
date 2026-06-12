---
title: "Can't scan as a user"
date: 2011-06-04
forum: General Help
---

### Post by Anonymouslemming on 2011-06-04
Hi all,

I have just installed 11.04 (64-bit) and I cannot scan as a user. Scanning as root works fine. My device is a Brother MFC-7420.

I've installed the brscan2-0.2.5-1.amd64.deb package from the brother page. After installing this, I can run xsane as root and scan perfectly.

I could not find any instructions for enabling this as a user on 11.04, so I followed the instructions for 10.04 at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10") and added the following between libsane_usb_rules_begin and libsane_usb_rules_end
```

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```

I then restarted udev, turned my device off and on again and tried to run xsane. I get the following error:
```
"Failed to open dvice `brother2:bus3;dev1': Invalid argument
```

I looked at what the rules were trying to do when libsane_matched is set to yes, and found that setfacl was not installed on my box. I installed this and changed the line to read
```
ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:saned:rw $env{DEVNAME}"
```

I then added my user to the saned group and rebooted. I still cannot scan as a user with xsane and still get the same message.

Any assistance would be much appreciated!

---

### Post by Anonymouslemming on 2011-06-14
Sorry to bump this, but I've still not resolved this. If anyone can point me to a resource as to how I debug this, I'd really appreciate it.

---

### Post by desertdog on 2011-06-14
[https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

---

### Post by Anonymouslemming on 2011-06-15
Thanks, but I've tried all of those options with the correct device and manufacturer IDs for my multi function device. None of them worked :(

---

### Post by plucky on 2011-06-15
> **Anonymouslemming said:**
> Thanks, but I've tried all of those options with the correct device and manufacturer IDs for my multi function device. None of them worked :(

Please post output of ```
lsusb | grep -i Brother
```

Then run ```
sudo chmod a+w /dev/bus/usb/004/002
``` where 004 is the output for the Bus in the lsusb command and 002 is the output for the Device in the lsusb command.

Try a scan and see if it works.

Good Luck

---

