---
title: "Xsane scanner found, but GUI does not find device"
date: 2011-07-21
forum: General Help
---

### Post by tarahmarie on 2011-07-21
I can find the HP Office Jet 6500 scanner using sane-find-scanner as you can see below, but sudo xsane finds no devices.

What am I doing wrong?

```

/ Hello! $su                                                                                                                          
Password: 
root@tarahmarie-desktop-home:/# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bb4, product=0x0c97) at libusb:002:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
root@tarahmarie-desktop-home:/# xsane
No protocol specified

(xsane:18206): Gtk-WARNING **: cannot open display: :0
root@tarahmarie-desktop-home:/# exit
exit
/ Hello! $sudo xsane
[sudo] password for tarahmarie: 


```

---

### Post by hellblazer on 2011-11-06
I have the exact same problem, will update if I find a fix.

---

### Post by hellblazer on 2011-11-06
ok got the scanner working. this is what I did:
run the following command as root:
```
/etc/init.d/udev restart
```
this will ensure that your ubuntu knows where the scanner is plugged in.

now xsane still doesn't work, but GIMP that I tried earlier without success is now scanning through it's SANE backend without any problems.

hope this helps

---

### Post by pqwoerituytrueiwoq on 2011-11-06
run [FONT=Courier New]sane-find-scanner[/FONT] or [FONT=Courier New]scanimage -L[/FONT] without root access and see if it sees it

---

### Post by hellblazer on 2011-11-06
just to add more info, running ```
sane-find-scanner
``` as a normal user finds the scanner, but it appears that ```
xsane
``` has a problem with GTK

---

