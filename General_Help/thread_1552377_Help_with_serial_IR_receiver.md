---
title: "Help with serial IR receiver"
date: 2010-08-13
forum: General Help
---

### Post by alda2 on 2010-08-13
HI,
I made IR receiver via this manual  : [http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)
Connected is in serial port under ubuntu 9.10
My installation steps :
 
sudo dpkg-reconfigure lirc
than 
Home-brew (16x50 UART compatible serial port) a transmitter none and  /dev/ttyS0

sudo /etc/init.d/lirc stop
 
irrecord -d /dev/ttyS0 lirc.conf.myremote ( I am not sure if ttys0 is correct )

but here I have this message :

root@XBMCLive:~# irrecord -d /dev/ttyS0 lirc.conf.myremote

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus([EMAIL="lirc@bartelmus.de"]lirc@bartelmus.de[/EMAIL])

irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/ttyS0 is 4
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyS0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

than I tried :

root@XBMCLive:~# sudo service lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ]
 * Loading LIRC modules                                                  [ OK ]
 * Starting remote control daemon(s) : LIRC                              [ OK ]

a skusil znovu irrecord :

root@XBMCLive:~# irrecord -d /dev/ttyS0 lirc.conf.myremote

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus([EMAIL="lirc@bartelmus.de"]lirc@bartelmus.de[/EMAIL])

irrecord: could not get hardware features
irrecord: this device driver does not support the LIRC ioctl interface
irrecord: major number of /dev/ttyS0 is 4
irrecord: LIRC major number is 61
irrecord: check if /dev/ttyS0 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
root@XBMCLive:~#

Please help 
what I can do ?

THX ALda

---

