---
title: "USB to Serial Communication"
date: 2010-06-30
forum: General Help
---

### Post by ce_picapart11 on 2010-06-30
Hello,

I wasn't sure exactly what forum to post my problem in so I chose this one, General Help. 

My problem is with using gtkterm. I am listening to a microcontroller via usb-to-serial and I am not getting the data I should be. Using Windows XP and Putty I am able to see exactly what I should be. When I run Ubuntu and Gtkterm I get complete garbage. It has random directories and strings all through the capture.

My settings are the same for Gtkterm as they are when I use Putty. I'm thinking maybe my usb-to-serial configuration is setup wrong. Maybe the generic converter isn't cutting it?

I attached a sample of the data I'm getting in Ubuntu with Gtkterm. Maybe someone has had my problem before and knows something to fix it.

If it means anything, the usb-serial device I have is FTDI.

Any and all help is much appreciated.

-Kevin

---

### Post by byStanderone on 2010-07-01
...hope there's something here:

[http://ubuntuforums.org/showthread.php?t=434829](http://ubuntuforums.org/showthread.php?t=434829)

---

### Post by ce_picapart11 on 2010-07-01
I installed lirc, removed the usbserial command in /etc/modules pertaining to the device, and restarted by computer. It seems to work fine now. Thanks.

-Kevin

---

