---
title: "Upgrade To Karmic Broke Ability To Scan"
date: 2010-01-15
forum: General Help
---

### Post by settntrenz on 2010-01-15
Upgrading from 9.04 -> 9.10 broke my ability to scan using iscan. 

Scanner:Epson NX100 (all in one connected via usb)
Arch:386
iscan:2.23.0-3.ltdl7 (latest .deb from avasys)
xsane:0.996-2ubuntu1.1
xsane-common:0.996-2ubuntu1.1
sane:1.0.14-7
libsane:1.0.20-4ubuntu3

```

user@box:~$ lsusb | grep seiko -i
Bus 002 Device 005: ID 04b8:0841 Seiko Epson Corp. 

```
```

user@box:~$ sane-find-scanner | grep found | grep -v "#"
found USB scanner (vendor=0x04b8, product=0x0841) at libusb:002:005

```
```

user@box:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `epkowa:usb:002:005' is a Epson (unknown model) flatbed scanner

```
```

user@box:~$ cat /etc/sane.d/epkowa.conf | grep -v "#"
usb
scsi

```
I tried adding the specific vendor and product id's after usb in /etc/sane.d/epkowa.conf to no avail.
```

user@box:~$ iscan
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

```
Window pops up and says ,"Could not send command to scanner. Check the scanner's status."

Attemping to run xsane as unprivileged user pops up windows saying ,"failed to open device: `epkowa:usb:002:005': Access to resource has been denied."

If I attempt to run as with escalated privileges, I don't get the error pop up window, but the window goes dark as if it stops responding and then it just closes with no stdout except ,"WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
"

I'm out of ideas here so any input would be greatly appreciated. This was working famously until I decided (against my better judgement) to upgrade.

---

### Post by Dirjel on 2010-01-16
Try this.  I had the same problem, but following the instructions in this thread fixed it for me.

[http://ubuntuforums.org/showthread.php?t=1138906&highlight=epkowa](http://ubuntuforums.org/showthread.php?t=1138906&highlight=epkowa)

---

### Post by settntrenz on 2010-01-16
That seems to have done the trick. Thanks for the help!

---

### Post by dave100 on 2010-01-18
Karmic is the worse release ever? Almost everything has been broken after installing 9.10 (Kubuntu). Now scanning also, there was some default plugin to import image from scanner but it was slow and after all did not produce the image (Epson 2400).After two hours of googling I finally got it working with iscan. Still not working with multiple user sessions.

Ubuntu folks, what are you trying to do, scare people away? Things should be better after upgrade, not totally broken.

---

### Post by ogfomk on 2010-04-01
I had to go to my elbow with this, but the above works.  At first only root worked.

---

