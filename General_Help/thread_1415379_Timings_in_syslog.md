---
title: "Timings in syslog"
date: 2010-02-24
forum: General Help
---

### Post by hansaplast on 2010-02-24
Hi,

My syslog /var/log/messages contains timing data```
Feb 25 00:20:09 mediabak kernel: [   23.147466] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb2:2
Feb 25 00:20:09 mediabak kernel: [   23.147520] usbcore: registered new interface driver lirc_mceusb
Feb 25 00:20:09 mediabak kernel: [   23.153030] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
```
see: [   23.147466] and [   23.153030] above.

Is there a way to write timing data to syslog for my own startup scripts during boot?

---

### Post by tgalati4 on 2010-02-24
apt-cache search bootchart

---

### Post by hansaplast on 2010-02-26
> **tgalati4 said:**
> apt-cache search bootchart
bootchart is already installed and working.
My boot scripts echo on stdout and log (logger) to syslog. What I've noticed is that my own log messages do not contain timing data.
```
Feb 22 15:23:30 mediabak kernel: [   27.891161] RPC: Registered tcp transport module.
Feb 22 15:23:31 mediabak kernel: [   28.261172] svc: failed to register lockdv1 RPC service (errno 97).
Feb 22 15:23:31 mediabak mythtv-backend: Waiting for video devices.
Feb 22 15:23:37 mediabak mythtv-backend: last message repeated 3 times
Feb 22 15:23:37 mediabak kernel: [   34.657210] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)

```
As you can see "mythtv-backend" log message does not contain the [timing-data]

---

### Post by tgalati4 on 2010-02-26
Perhaps look at the source code for syslogd and klogd.  I don't know how that time is captured.  But let us know when you find it.

---

