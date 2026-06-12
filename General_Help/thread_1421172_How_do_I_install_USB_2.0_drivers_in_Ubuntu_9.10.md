---
title: "How do I install USB 2.0 drivers in Ubuntu 9.10?"
date: 2010-03-03
forum: General Help
---

### Post by Ordinary12 on 2010-03-03
Hey Guys:

I noticed that every time I attached a usb device to my laptop the speeds never exceeded 5MB per second.  This is very slow to me so I typed the following command into my terminal:

lsmod | grep ehci_hcd

I read in another article that if I had the usb 2.0 driver installed I would have seen some kind of output from this command.  I saw nothing.  Can someone please tell me how to install usb 2.0?

---

### Post by flippo on 2010-03-03
You most likely have USB 2.0 installed, its part of the default kernel.  If you have an issue it is most likely because ubuntu does not associate the correct driver with the usb device.

What device are you experiencing slow speeds on, and what is the output of:```
sudo lsusb
```

Additionally, a common fix, if module ehci_hcd is not being loaded correctly would be to type this into a terminal```
sudo modprobe -r ehci_hcd
sudo modprobe -a ehci_hcd
```

---

### Post by Ordinary12 on 2010-03-04
Here's the output of that command:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


When ever I attach a usb hard drive I get extremely slow speeds.

Here is the out put from the two other commands:

kendall@Prisoner1:~$ sudo modprobe -r ehci_hcd
FATAL: Module ehci_hcd not found.
kendall@Prisoner1:~$ 
kendall@Prisoner1:~$ sudo modprobe -a ehci_hcd
WARNING: Module ehci_hcd not found.

---

### Post by flippo on 2010-03-04
Okay, that's kindof odd.  What is the output of ```
sudo dmesg | grep echi_hcd
```If that doesn't give anything also attach the output of ```
sudo dmesg | grep usb
```

---

### Post by El Zoido on 2010-03-04
Both my Karmic pc's behave practically the same, neither shows any output for ```
sudo dmesg | grep echi_hcd
```

Also both show only one USB2.0 for ```
sudo lsusb
```

Still, as far as I can tell, transfer rates for my devices seem reasonable.
Are you sure this tests are correct to determine USB 2.0 availability?

---

### Post by Ordinary12 on 2010-03-04
The first command:

sudo dmesg | grep echi_hcd

Nothing was displayed.

Here's the second command:

kendall@Prisoner1:~$ sudo dmesg | grep usb
[    0.212182] usbcore: registered new interface driver usbfs
[    0.212182] usbcore: registered new interface driver hub
[    0.212182] usbcore: registered new device driver usb
[    0.948133] usb usb1: configuration #1 chosen from 1 choice
[    0.948507] usb usb2: configuration #1 chosen from 1 choice
[    0.948784] usb usb3: configuration #1 chosen from 1 choice
[    0.949061] usb usb4: configuration #1 chosen from 1 choice
[    0.949351] usb usb5: configuration #1 chosen from 1 choice
[    1.260073] usb 1-8: new high speed USB device using ehci_hcd and address 2
[    1.400405] usb 1-8: configuration #1 chosen from 1 choice
[    9.613177] usbcore: registered new interface driver rtl8187

---

### Post by flippo on 2010-03-05
oops, I typo'd the code, it should be ehci_hcd, not echi_hcd.  

It appears your computer is detecting devices as usb2.0 though, judging by the dmesg output:```
[ 1.260073] usb 1-8: new high speed USB device using ehci_hcd and address 2
```

So ehci_hcd is most likely a kernel built-in instead of a module, which would be why it didn't pop up on the modprobe.

I really don't know why your experiencing slow transfers :-/

To be absolutely sure your device is using the correct driver can you do the following:
```
<unmount/unplug the HD>
sudo dmesg > dmesg_nohd
<plugin the HD and wait for it to automount>
sudo dmesg > dmesg_hd
sudo diff dmesg_hd dmesg_nohd
sudo rm dmesg_hd dmesg_nohd
```

print the output of:```
sudo diff dmesg_hd dmesg_nohd
```

---

### Post by El Zoido on 2010-03-05
> oops, I typo'd the code, it should be ehci_hcd, not echi_hcd. 

Yes, indeed! ;)

However, I just had a look at what you actually can expect from USB, speed-wise.
5MB/s (what the OP reported) is already much higher than what USB 1.1 could provide (I think the maximum would be roughly 1,5 MB/s).
Now USB 2.0 should be able to handle 60MB/s **in theory**.
You will probably never see this speed in real life, though.

The transfer rates you will see also depend on your device. I have on USB flash drive that delivers about 5 MB/s, and another that gives me 12 MB/s.

So while you get indeed much less than one would like to see, I guess we can safely assume that your PC is using USB 2.0 .

---

### Post by sille777 on 2010-06-20
I seem to be having similar issues with slow usb transfer speeds:

Output from 
```
sudo dmesg | grep usb
[    0.104963] usbcore: registered new interface driver usbfs
[    0.104977] usbcore: registered new interface driver hub
[    0.105004] usbcore: registered new device driver usb
[    0.904163] usb usb1: configuration #1 chosen from 1 choice
[    1.002346] usb usb2: configuration #1 chosen from 1 choice
[    1.091888] usb usb3: configuration #1 chosen from 1 choice
[    1.275940] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.466921] usb 1-2: configuration #1 chosen from 1 choice
[    1.888793] usbcore: registered new interface driver usb-storage
[    1.888882] usb-storage: device found at 2
[    1.888884] usb-storage: waiting for device to settle before scanning
[    6.888348] usb-storage: device scan complete
[  521.412075] usb 2-1: new low speed USB device using ohci_hcd and address 2
[  521.621642] usb 2-1: configuration #1 chosen from 1 choice
[  521.750970] usbcore: registered new interface driver hiddev
[  521.759287] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input8
[  521.759767] generic-usb 0003:046D:C01D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1/input0
[  521.759836] usbcore: registered new interface driver usbhid
[  521.762784] usbhid: v2.6:USB HID core driver

```And  Output from:
```
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 154b:6545 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Please let me know any other information I may need to provide.  Thanks.

---

### Post by jodajen2 on 2010-06-25
> **sille777 said:**
> I seem to be having similar issues with slow usb transfer speeds:

Output from 
```
sudo dmesg | grep usb
[    0.104963] usbcore: registered new interface driver usbfs
[    0.104977] usbcore: registered new interface driver hub
[    0.105004] usbcore: registered new device driver usb
[    0.904163] usb usb1: configuration #1 chosen from 1 choice
[    1.002346] usb usb2: configuration #1 chosen from 1 choice
[    1.091888] usb usb3: configuration #1 chosen from 1 choice
[    1.275940] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.466921] usb 1-2: configuration #1 chosen from 1 choice
[    1.888793] usbcore: registered new interface driver usb-storage
[    1.888882] usb-storage: device found at 2
[    1.888884] usb-storage: waiting for device to settle before scanning
[    6.888348] usb-storage: device scan complete
[  521.412075] usb 2-1: new low speed USB device using ohci_hcd and address 2
[  521.621642] usb 2-1: configuration #1 chosen from 1 choice
[  521.750970] usbcore: registered new interface driver hiddev
[  521.759287] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input8
[  521.759767] generic-usb 0003:046D:C01D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1/input0
[  521.759836] usbcore: registered new interface driver usbhid
[  521.762784] usbhid: v2.6:USB HID core driver

```And  Output from:
```
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 154b:6545 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Please let me know any other information I may need to provide.  Thanks.


Did you figure anything out?  I have having the same issue with slow usb transfer rates.  It seems to start fast and last for about 150 mb then it slows to a crawl.  I have mythtv installed and was using it for a external storage device but it just can't keep up.  let me know if you figured anything?

---

