---
title: "Ti 89 titanium, tilp problem"
date: 2006-01-26
forum: General Help
---

### Post by Udziuolo on 2006-01-26
Hello there!

I've just bought a new Ti-89 titanium calc and I'm trying to connect it to my Ubuntu laptop via USB (SilverLink). I've downloaded and compiled tiglusb module, then modprobed it.

Finally I've created the node (because the module didn't do so):
```
sudo mknod /dev/tiusb0 c 115 16
sudo chmod 777 /dev/tiusb0 
```

And after setting tilp to connect, I'm getting the following:

```
*** TiLP logfile (/tmp/tilp_log.WcB7Gy) ***

tilp    : TiLP - Version 6.80, (C) 1999-2005 Romain Lievin
tilp    : THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
tilp    : PLEASE READ THE DOCUMENTATION FOR DETAILS
tilp    : built on Jan 23 2006 16:57:07
tilp    : initialized in command line mode.
tilp    : err: msg_box: Error, Configuration file error at line 11.

tilp    : err: msg_box: Error, Configuration file error at line 47.

tilp    : err: msg_box: Error, Configuration file error at line 65.

tilp    : err: msg_box: Error, Configuration file error at line 71.

tilp    : err: rcfile, 0x000
tilp    : setlocale: <pl_PL>
tilp    : bindtextdomain: </usr/local/share/locale/>
tilp    : textdomain: <tilp>
ticables: ticables library version 3.9.6
ticables: setlocale: <pl_PL>
ticables: bindtextdomain: </usr/local/share/locale>
ticables: textdomain: <libticables>
ticables: built for __LINUX__ target.
ticables: checking resources:
ticables:   IO_API: found at compile time (HAVE_TERMIOS_H)
ticables:   IO_ASM: found at compile time (HAVE_ASM_IO_H).
ticables:   IO_TIPAR: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TISER: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_TIUSB: found at compile time (HAVE_LINUX_TICABLE_H)
ticables:   IO_LIBUSB: not found at compile time (HAVE_LIBUSB)
ticables: quick search for parallel/serial ports:
ticables:   serial port found at 0x2f8
ticables:   serial port found at 0x3f8
ticables: search for all ports:
ticables:   /dev/ttyS0 at 0x3f8
ticables:   /dev/ttyS1 at 0x2f8
ticables:   /dev/ttyS2 at 0x3e8
ticables:   /dev/ttyS3 at 0x2e8
ticables: getting method from resources (automatic):
ticables:   check for tty usability:
ticables:     node /dev/ttyS0: exists
ticables:     permissions/user/group: -rw-rw---- root dialout
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: GrayLink
ticables:   port: serial port #2
ticables:   method: direct access (api)
ticables:   device name: /dev/ttyS1
ticables:   delay value: 10
tifiles : tifiles library version 0.6.6
tifiles : setlocale: <pl_PL>
tifiles : bindtextdomain: </usr/local/share/locale>
tifiles : textdomain: <libtifiles>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : ticalcs library version 4.6.1
ticalcs : setlocale: <pl_PL>
ticalcs : bindtextdomain: </usr/local/share/locale>
ticalcs : textdomain: <libticalcs>
tifiles : settings:
tifiles :   calc type: TI92
ticalcs : settings:
ticalcs :   calc type: TI92
tilp    : initialized in GTK+ mode.
tilp    : scanning plug-ins... Done !
tilp    : scanning registry... Done !
ticables: getting method from resources (automatic):
ticables:   check for tiusb usability:
ticables:     using devfs: no
ticables:     node /dev/tiusb0: exists
ticables:     permissions/user/group: -rwxrwxrw- root root
ticables:     is user can r/w on device: yes
ticables:     module: loaded
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: kernel mode (module)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: TI89t
ticalcs : settings:
ticalcs :   calc type: TI89t
ticables: err: unable to open this device: /dev/tiusb0
```

I've also tried the tilp-2 program:
```
TiLP - Version 0.02, (C) 1999-2005 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Jan 23 2006 19:43:15
tilp-INFO: setlocale: <pl_PL>
tilp-INFO: bindtextdomain: </usr/local/share/locale/>
tilp-INFO: textdomain: <tilp2>
ticables-INFO: cables library version 0.0.1
ticables-INFO: setlocale: <pl_PL>
ticables-INFO: bindtextdomain: </usr/local/share/locale>
ticables-INFO: textdomain: <libticables2>
tifiles-INFO: tifiles library version 0.0.1
tifiles-INFO: setlocale: <pl_PL>
tifiles-INFO: bindtextdomain: </usr/local/share/locale>
tifiles-INFO: textdomain: <libtifiles2>
ticalcs-INFO: ticalcs library version 0.0.1
ticalcs-INFO: setlocale: <pl_PL>
ticalcs-INFO: bindtextdomain: </usr/local/share/locale>
ticalcs-INFO: textdomain: <libticalcs2>
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:     node /proc/bus/usb/devices: exists
ticables-INFO:     permissions/user/group: -r--r--r-- root root
ticables-INFO:     is user can r/w on device: yes
tilp-INFO: msg_box: Error, Msg: illegal operation or argument.
Cause: the program which uses this library is buggy. Fire-up the developer !
System: Niewlasciwy ioctl dla urzadzenia (errno = 25)
{Translation: Not valid ioctl for device (errno = 25)}

```

Is someone able to help me with the connection?

---

### Post by Udziuolo on 2006-02-04
<bump>

Anyone? It's important for me:)
Texas Instrument's Ti Connect works under wine, but it can't access USB ports.

---

### Post by 1/0 on 2007-10-22
Did you ever figure it out? I've got the same calculator and just problems connecting via tilp.

---

### Post by Udziuolo on 2007-11-04
No I haven't. Actually, I've done all the connections via Vmware. Now I don't need it so badly, so I've given up.

---

