---
title: "Create /proc/bus/usb in ubuntu 10.10"
date: 2010-12-18
forum: General Help
---

### Post by Hrsda on 2010-12-18
I am trying to use eciadsl in ubuntu 10.10 in order to connect my Prolink H9601 USB ADSL modem(Conexant based) to the internet.eciadsl worked to some extent in ubuntu 9.10 but in ubuntu 10.10 it returns 
[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is missing... trying to mount
Preliminary USB device filesystem: failed to load
/usr/bin/eciadsl-start: line 263: fatal: command not found
cat: /proc/bus/usb/devices: No such file or directory
Loading UHCI support... Warning: uhci-hcd module doesn't exist
Warning: tun/tap module does not exist

[EciAdsl 2/5] Uploading firmware...

grep: /proc/bus/usb/devices: No such file or directory
grep: /proc/bus/usb/devices: No such file or directory
ERROR: modem not found
I presume this is because ubuntu 10.10 does not mount USB device filesytem (usbfs) in /proc/bus/usb folder and i can't manually create this folder therefore making it impossible to mount usbfs manually into this folder.
Could someone help me to create this folder or suggest an alternative to connecting my modem to the internet?

---

### Post by lexl on 2011-01-02
I have similar problem with you. My ADSL Dlink DSL-200 doesn't work at Linux kernels older than 2.6.31-17. It take place because USB file system (usbfs) was replaced by device manager (udev). But in different cases, problem solved using next code:
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices 
In my case it doesn't work. May be you will be luckier.:guitar:

---

### Post by lexl on 2011-01-07
You should find next line in your linux config-file '# CONFIG_USB_DEVICEFS is not set' and replace it with 'CONFIG_USB_DEVICEFS=y' and recompile your kernel. It is not correct but it works ):P

---

### Post by xenon202 on 2011-01-25
where is linux config-file ?
how replace '# CONFIG_USB_DEVICEFS is not set' with 'CONFIG_USB_DEVICEFS=y' ?
What to do?

---

