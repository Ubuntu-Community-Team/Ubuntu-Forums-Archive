---
title: "Can you help with this install error...please"
date: 2011-02-05
forum: General Help
---

### Post by hopelessone on 2011-02-05
Hi All,

Im trying to install lirc by following this tutorial I made my own IR reciever: [http://lnx.manoweb.com/lirc/?partType=section&partName=lirc](http://lnx.manoweb.com/lirc/?partType=section&partName=lirc)

the web site says: > and start the semi-graphical setup:
./setup

and heres what i get:

```
some@one:~/LIRC/lirc-0.8.7$ sudo su
[sudo] password for some: 
root@one:/home/some/LIRC/lirc-0.8.7# ./setup.sh && make install
dialog not found!
root@one:/home/some/LIRC/lirc-0.8.7# ./setup
bash: ./setup: No such file or directory
root@one:/home/some/LIRC/lirc-0.8.7# ./setup.sh
dialog not found!

```

I'm on a 64bit 10.04 with kernel 2.6.32-24...Any ideas how i can get to work?

Thanks very much...

---

### Post by 3rdalbum on 2011-02-05
sudo apt-get install dialog

A confusing error message, quite ambiguous.

---

### Post by hopelessone on 2011-02-05
Ahhh...it was a tricky one..Thanks budy..

OK almost done and I get to here with an error:

```
modprobe lirc_serial
```

```
some@one:~/LIRC/lirc-0.9.0-pre1$ sudo setserial /dev/ttyS0 uart none
some@one:~/LIRC/lirc-0.9.0-pre1$ sudo modprobe lirc-serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.32-24-generic/misc/lirc_serial.ko): Input/output error


```

OK i understand its busy...so how can install the module?

Thanks

[edit] here is dmesg:
> [103552.401499] lirc_dev: IR Remote Control driver registered, major 61 
[103552.403609] lirc_serial: port 03f8 already in use
[103552.403614] lirc_serial: use 'setserial /dev/ttySX uart none'
[103552.403617] lirc_serial: or compile the serial port driver as module and
[103552.403620] lirc_serial: make sure this module is loaded first
[103601.545278] lirc_serial: port 03f8 already in use
[103601.545284] lirc_serial: use 'setserial /dev/ttySX uart none'
[103601.545287] lirc_serial: or compile the serial port driver as module and
[103601.545290] lirc_serial: make sure this module is loaded first
[103825.841172] lirc_serial: port 03f8 already in use
[103825.841178] lirc_serial: use 'setserial /dev/ttySX uart none'
[103825.841181] lirc_serial: or compile the serial port driver as module and
[103825.841184] lirc_serial: make sure this module is loaded first
[103892.290041] lirc_serial: auto-detected active low receiver
[103892.290048] lirc_register_driver: dev pointer not filled in!
[103892.290052] lirc_serial: register_chrdev failed!
[103945.270030] lirc_serial: auto-detected active low receiver
[103945.270037] lirc_register_driver: dev pointer not filled in!
[103945.270041] lirc_serial: register_chrdev failed!
[104067.190027] lirc_serial: auto-detected active low receiver
[104067.190035] lirc_register_driver: dev pointer not filled in!
[104067.190039] lirc_serial: register_chrdev failed!
[104101.320020] lirc_serial: auto-detected active low receiver
[104101.320027] lirc_register_driver: dev pointer not filled in!
[104101.320031] lirc_serial: register_chrdev failed!
root@one:/home/some/LIRC/lirc-0.9.0-pre1# 


---

