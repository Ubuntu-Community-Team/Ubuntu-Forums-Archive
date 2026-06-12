---
title: "Ultra UPS Nut Configuartion Help  :: Ubuntu 10.04 ::"
date: 2011-07-08
forum: General Help
---

### Post by own3mall on 2011-07-08
I just bought an Ultra UPS system for my linux server, and I need help getting it set up.  It's an Ultra 700VA UPS.

Here's the device information from my syslog:

```

Jul  7 23:25:27 eric-desktop kernel: [ 3045.609066] usb 2-1: USB disconnect, address 3
Jul  7 23:25:30 eric-desktop kernel: [ 3049.073041] usb 2-1: new low speed USB device using uhci_hcd and address 4
Jul  7 23:25:30 eric-desktop kernel: [ 3049.257903] usb 2-1: configuration #1 chosen from 1 choice
Jul  7 23:25:31 eric-desktop kernel: [ 3049.671558] generic-usb 0003:0D9F:0004.0005: hiddev96,hidraw1: USB HID v1.00 Device [POWERCOM Co.,LTD HID UPS Battery] on usb-0000:00:1d.0-1/input0

```Here's my etc/nut/ups.conf file:

```

# /etc/nut/ups.conf

[Ultra]
    driver = powercom
    port = port=/dev/hidraw1
    linevoltage = 120
    manufacturer = Ultra
    modelname = ULTRA 700VA
    type = Trust
    methodOfFlowControl=dtr0rts1
    shutdownArguments = {{7,10},y}

```Here's what I get when I run sudo upsdrvctl start:

```

eric@eric-desktop:~$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.4.3
Network UPS Tools - PowerCom protocol UPS driver 0.12 (2.4.3)

Unable to open port=/dev/hidraw1: No such file or directory

Things to try:

 - Check 'port=' in ups.conf

 - Check owner/permissions of all parts of path

Fatal error: unusable configuration
Driver failed to start (exit status=1)


```

I've been following these guides:

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)
[http://www.mail-archive.com/nut-upsuser@lists.alioth.debian.org/msg05168.html](http://www.mail-archive.com/nut-upsuser@lists.alioth.debian.org/msg05168.html)

/dev/hidraw1 does exist... is this how I'm supposed to configure a USB connection between my UPS system?  What permissions need to be set on hidraw1?

Any and all help is appreciated!

---

