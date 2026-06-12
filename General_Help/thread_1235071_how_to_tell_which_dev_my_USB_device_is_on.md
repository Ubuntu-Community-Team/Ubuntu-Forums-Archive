---
title: "how to tell which /dev/ my USB device is on?"
date: 2009-08-08
forum: General Help
---

### Post by linuxgrrl on 2009-08-08
Hello,
I am trying to create a ppp connection to  a Palm device over USB (long story).  The script I am using has "/dev/ttyusb0" as the device for the Palm, however I know that is not right because it does not exist in my setup.  How do I tell which is the correct /dev/ on my system?  My output of lsusb is below.  Thanks for any guidance!
```
root@mythbox:/proc/bus/usb# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0c16:0002 Gyration, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0830:0060 Palm, Inc. Tungsten C/E/T/T2/T3 / Zire 71
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

and from /var/log/messages (when I sync the device))):

```
Aug  8 16:01:31 mythbox kernel: [12291.182049] cx88_wakeup: 3 buffers handled (should be 1)
Aug  8 16:01:31 mythbox kernel: [12291.636043] usb 2-1: new full speed USB device using uhci_hcd and address 5
Aug  8 16:01:31 mythbox kernel: [12291.836488] usb 2-1: configuration #1 chosen from 1 choice
Aug  8 16:01:32 mythbox kernel: [12292.628557] cx88_wakeup: 2 buffers handled (should be 1)
Aug  8 16:01:38 mythbox kernel: [12297.976085] usb 2-1: USB disconnect, address 5
```

---

### Post by mcduck on 2009-08-08
One useful trick I always do in that kind of situations is to open a terminal and run "tail -f /var/log/messages" and then plug in the device. You should see the log messages about the device being detected, including the device name.

---

### Post by warp99 on 2009-08-08
```
cat /proc/bus/input/devices
```

---

### Post by warp99 on 2009-08-08
I forget one thing to ask, what's the output when you plug in the device, wait 10 seconds and run "dmesg | tail -n 25"?

---

### Post by linuxgrrl on 2009-08-08
here is the output from dmesg
```

[14077.432045] usb 2-1: new full speed USB device using uhci_hcd and address 6
[14077.614792] usb 2-1: configuration #1 chosen from 1 choice
[14078.424487] cx88_wakeup: 3 buffers handled (should be 1)
[14084.072582] usb 2-1: USB disconnect, address 6
```


cat /proc/bus/input/devices did not yield any reference to the palm ... just power buttons and speakers, etc.

I have to go now for a bit but will check back!
thx

---

