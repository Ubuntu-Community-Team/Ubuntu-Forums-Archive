---
title: "Cannot hibernate - Bluetooth USB errors"
date: 2009-07-16
forum: General Help
---

### Post by Richardcavell on 2009-07-16
Hi, all.

I have Ubuntu 64-bit 9.04 on a MacBook generation 2, which has a Bluetooth device attached to the USB. I understand that most MacBook innards are connected via USB. If I try to hibernate via "/usr/sbin/pm-hibernate", or selecting it from the login menu, I get errors. The screen goes black, and then it turns on again with a blinking cursor at the top-left of screen. Then some errors appear:

[328.685635] btusb_intr_complete: hci0 urb fff8800a078d80 failed to resubmit (1)

and two more just like it. Then I get a blinking cursor below all that text. After about 60 seconds, the CPU fan starts up, implying that the CPU is working hard. I need to do a reboot to get my computer back.

I tried 'sudo rmmod btusb', but I get 'ERROR: Module btusb is in use.'  'lsmod  | grep usb' returns 'btusb 21784 2' and 'usbhid 47040 0'.

In case, it's relevant, I have a script called /etc/pm/sleep.d/99-macbook.sh that has this in it:

> #!/bin/bash
case $1 in
    resume)
        /etc/init.d/bluetooth stop
        /etc/init.d/bluetooth start
        ;;
    thaw)
        modprobe -r appletouch
        modprobe appletouch
        ;;
esac

Any ideas?

TIA,

Richard

---

### Post by Bertran on 2009-10-02
Hey 
 
I get a similar issue but it doesn't affect my laptop's ability to hibernate. I use a VAIO and I notice that switching off my bluetooth/wireless hardware (using a switch on the side of my laptop) allows me to hibernate without getting that message. 
 
I am unable to use my bluetooth hardware to detect any bluetooth device in Ubuntu so I've reported a bug here [https://bugs.launchpad.net/ubuntu/+bug/439808/](https://bugs.launchpad.net/ubuntu/+bug/439808/)

---

