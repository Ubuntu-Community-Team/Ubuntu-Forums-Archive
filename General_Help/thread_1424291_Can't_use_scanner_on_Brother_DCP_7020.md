---
title: "Can't use scanner on Brother DCP 7020"
date: 2010-03-07
forum: General Help
---

### Post by clark14 on 2010-03-07
I'm using 9.10 on x86 architecture.  I've searched the forums and anything related to scanning talks about editing /etc/udev/rules.d/45-libsane.rules  which doesn't seem to exist on my system.  Judging from the dates most of these posts probably relate to intrepid or jaunty.  XSane just says 'no devices available'.  Printing works fine.  Any ideas?

---

### Post by TopEnder on 2010-03-07
G'Day,  Have a look in the Forum - Installation & Upgrades for  "[COLOR="Blue"]Lost scanner in upgrade to karmic 9.10[/COLOR]" by [COLOR="Blue"]BigJules[/COLOR], hopefully it will help you solve your problem.  Your reference that you edited is not correc [COLOR="Red"]/etc/udev/rules.d/45-libsane.rules[/COLOR] or have a look at the Brother site [COLOR="Blue"]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10[/COLOR].  If still having problem then post again.

---

### Post by clark14 on 2010-03-08
Ah, yes, thank you for bringing that to my attention.  /lib/udev/rules.d/40-libsane.rules is the correct path/file (not etc).
Unfortunately, after editing the file and restarting as specified on the brother site xsane still insists it cannot find the scanner.

lsusb returns:
```
Bus 003 Device 002: ID 04f9:0183 Brother Industries, Ltd DCP-7020
```

BUT, sane find-scanner returns:
```
No command 'sane' found, did you mean:
 Command 'sage' from package 'sagemath' (universe)
 Command 'save' from package 'atfs' (universe)
 Command 'saned' from package 'sane-utils' (main)
 Command 'xsane' from package 'xsane' (main)
sane: command not found
```

---

### Post by plucky on 2010-03-08
Have you installed the scanner drivers?

Post output from a terminal for ```
dpkg -l | grep brother
dpkg -l | grep brscan
```

The scanner drivers have to be downloaded from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

Good Luck

---

### Post by Vermicelli on 2010-05-14
I can report the same problem with the same device. I was able to scan using xsane on Ubuntu 8.10, but xsane (and Simple Scan) can't find the device under 10.04. I have brscan2 installed and I've edited the file as specified.

---

### Post by Vermicelli on 2010-05-14
Actually, never mind! I had a slightly outdated version of brscan2. I just updated it and scanning works perfectly.

---

### Post by donhdtv on 2010-10-03
HOW TO INSTALL BROTHER DCP-7020 SCANNER IN UBUNTU.


Download and install brscan2 32bit debian and scan-key-tool 32bit debian from the Brother website. The debian installer installs it for you.


From a terminal window you may verify the drivers are installed by
sudo dpkg  -l  |  grep  Brother


If the driver is detected then for

Ubuntu 9.10, 10.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list.

    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Simple scan should now work.

Recommend installing the xsane image scanner for a more robust application.

---

