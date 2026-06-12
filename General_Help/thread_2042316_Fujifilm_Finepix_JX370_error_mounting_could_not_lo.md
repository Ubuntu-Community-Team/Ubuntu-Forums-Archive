---
title: "Fujifilm Finepix JX370 error mounting could not lock the device"
date: 2012-08-14
forum: General Help
---

### Post by afrodeity on 2012-08-14
I am getting this error popping up:

```
error mounting could not lock the device
```

The camera does appear, I can see my pictures, just unable to copy them to my pictures folder.

```

lsusb
Bus 001 Device 012: ID 04cb:0250 Fuji Photo Film Co., Ltd
```

---

### Post by afrodeity on 2012-08-14
```

 gphoto2 --list-config
                                                                               
*** Error ***              
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
*** Error (-60: 'Could not lock the device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --list-config

Please make sure there is sufficient quoting around the arguments.

```
```


 gphoto2 --debug 
0.000016 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000048 main(2): gphoto2 2.4.11
0.000055 main(2): gphoto2 has been compiled with the following options:
0.000060 main(2):  + gcc (C compiler used)
0.000064 main(2):  + popt (mandatory, for handling command-line parameters)
0.000068 main(2):  + exif (for displaying EXIF information)
0.000073 main(2):  + cdk (for accessing configuration options)
0.000077 main(2):  + aa (for displaying live previews)
0.000081 main(2):  + jpeg (for displaying live previews in JPEG format)
0.000085 main(2):  + readline (for easy navigation in the shell)
0.000092 main(2): libgphoto2 2.4.13
0.000099 main(2): libgphoto2 has been compiled with the following options:
0.000103 main(2):  + gcc (C compiler used)
0.000107 main(2):  + ltdl (for portable loading of camlibs)
0.000112 main(2):  + EXIF (for special handling of EXIF files)
0.000116 main(2): libgphoto2_port 0.8.0
0.000123 main(2): libgphoto2_port has been compiled with the following options:
0.000128 main(2):  + gcc (C compiler used)
0.000132 main(2):  + ltdl (for portable loading of camlibs)
0.000136 main(2):  + USB (libusb, for USB cameras)
0.000140 main(2):  + serial (for serial cameras)
0.000144 main(2):  + no resmgr (serial port access and locking)
0.000149 main(2):  + no ttylock (serial port locking)
0.000153 main(2):  + no lockdev (serial port locking)
0.000157 main(2): CAMLIBS env var not set, using compile-time default instead
0.000162 main(2): IOLIBS env var not set, using compile-time default instead
0.000173 setting/gphoto2-setting.c(2): Creating $HOME/.gphoto
0.000204 setting/gphoto2-setting.c(2): Loading settings from file "/home/afrodeity/.gphoto/settings"
0.000283 gp-camera(2): Freeing camera...
0.000294 gphoto2-port(2): Freeing port...
0.000302 gphoto2-filesystem(2): resetting filesystem
0.000306 libgphoto2/gphoto2-filesys.c(2): Clearing fscache LRU list...
0.000311 libgphoto2/gphoto2-filesys.c(2): fscache LRU list already empty
0.000315 gphoto2-filesystem(2): Internally deleting all folders from '/'...
0.000320 gphoto2-filesystem(2): Lookup folder '/'...
0.000324 gphoto2-filesystem(2): Found! / is 0x94dfca0
0.000329 gphoto2-filesystem(2): Recurse delete folder 0x94dfca0//

```

---

### Post by afrodeity on 2012-08-14
This posting is helpful, but still some issues.
[http://efreedom.com/Question/3-148412/Remove-Kernel-Lock-Unmounted-Mass-Storage-USB-Device-Command-Line-Linux](http://efreedom.com/Question/3-148412/Remove-Kernel-Lock-Unmounted-Mass-Storage-USB-Device-Command-Line-Linux)

[http://ubuntuforums.org/showthread.php?t=76706](http://ubuntuforums.org/showthread.php?t=76706)

I've tried to unload the usb_storage module:
 
 rmmod usb_storage

gphoto2 -l

An error occurred in the io-library ('Unspecified error'): The supplied vendor or product id (0x0,0x0) is not valid

---

