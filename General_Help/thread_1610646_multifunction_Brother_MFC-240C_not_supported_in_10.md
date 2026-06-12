---
title: "multifunction Brother MFC-240C not supported in 10.10"
date: 2010-10-31
forum: General Help
---

### Post by gdiloren on 2010-10-31
Extremely difficult to get to run this Brother multifunction machine, model MFC-240C, on Linux. I found the drivers but installing them corrupted two times my apt-get daemon and to scan I have to use sudo (elevated privileges) otherwise it says it can't connect to the USB scanner

---

### Post by plucky on 2010-11-01
> **gdiloren said:**
> Extremely difficult to get to run this Brother multifunction machine, model MFC-240C, on Linux. I found the drivers but installing them corrupted two times my apt-get daemon and to scan I have to use sudo (elevated privileges) otherwise it says it can't connect to the USB scanner

Your printer drivers are packaged in Synaptic Package Manager.
```
sudo apt-get install brother-cups-wrapper-bh7
``` which will also install the lpr-drivers.

Or search SPM for **mfc-240c** and select the drivers it finds and install.

For the scanner you need to download the relevant drivers from the [Brother website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) which for your printer is brscan2 and also follow the instructions that are there  including putting```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

``` in the file /lib/udev/rules.d/40-libsane.rules and install **sane-utils**

Good Luck

---

### Post by gdiloren on 2010-11-02
Thousand thanks. After reboot, it works. Not as automatic as windows vista (harsher) to install a scanner or let say upload a map in your Garmin nuvi 255W or using your iTune on Ubuntu. Just more complicated, don't know tomorrow...

---

