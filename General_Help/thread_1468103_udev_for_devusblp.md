---
title: "udev for /dev/usb/lp*"
date: 2010-05-01
forum: General Help
---

### Post by hammertofall on 2010-05-01
Hello, I have connected 

2 dot matrix printers
2 zebra barcode printers
1 epson laser printer

to my print server via usb and they are recognized as /dev/usb/lp*
but everytime the identifications are changing. the first connected printer goes as lp0 and the one after lp1... i want to fix every printer to a unique name or lp id. like

2 dot matrix printers - lp0 and lp1
2 zebra barcode printers - lp2 and lp3
1 epson laser printer - lp4

or

2 dot matrix printers - dot0 and dot1
2 zebra barcode printers - bar0 and bar1
1 epson laser printer - las0

i know this can be done by writing udev rules but i try alot, still no success. Any alternative solutions are welcomed too.

Can anyone please help?

Thanks and goodbye for now.

---

### Post by sisco311 on 2010-05-01
udev rules are stored in /etc/udev/rules.d/, their file name has to end with .rules.

To creat a new file and open it for editing run:
```
gksu gedit /etc/udev/rules.d/99-printer.rules
```

To get a list of all the attributes of a device run:
```
sudo udevadm info -a -p $(sudo udevadm info -q path -n **[device name]**)
```

replace **[device name]** with the device present in the system (/dev/usb/lp0, /dev/usb/lp1...).

From the output of the command find an attribute which is unique for the device (i.e. ATTRS{serial}=="xxxxxxxxxxxxxx").

A rule looks like this:
```
SUBSYSTEM=="usb", ATTRS{serial}=="xxxxxxxxxxxxxx", SYMLINK+="dot0"
```

Once you created the rule restart the udev system:
```
sudo udevadm control restart
```

Unplug and plug back in the printers. Check if the symbolic links are created:
```
ls -al /dev/dot0
...
```


If you have difficulties with writing the rules, post the output of the:
```
sudo udevadm info -a -p $(sudo udevadm info -q path -n **[device name]**)
```commands.

[http://wiki.archlinux.org/index.php/Udev#About_udev_rules](http://wiki.archlinux.org/index.php/Udev#About_udev_rules)
[http://www.reactivated.net/writing_udev_rules.html#example-printer](http://www.reactivated.net/writing_udev_rules.html#example-printer)

---

