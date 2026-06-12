---
title: "Unable to mount Maxtor USB HD"
date: 2010-07-07
forum: General Help
---

### Post by papibe on 2010-07-07
I have a Maxtor USB hardrive that luckily it's recognized using lsusb, but unfortunately not by blkid nor fdisk. Then I can't mount it.

I have 2 other external HDs both working OK (Iomega and MyBook).

What can I do?

Regards.

P.D.: this is Ubuntu Desktop.

---

### Post by bumanie on 2010-07-07
Has it been formatted with a filesystem or is it still a 'raw' disk?

---

### Post by papibe on 2010-07-07
Yes, it's ntfs formated, with lots on data on it  :confused:.

---

### Post by papibe on 2010-07-07
I checked this: [launchpad bug 88746]("https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/88746")

Is this the revival of an old buggy module?

```
pablo@vaughan:~$ dmesg | tail 
[21264.823448] usb-storage: device found at 6
[21264.823451] usb-storage: waiting for device to settle before scanning
[21269.820437] usb-storage: device scan complete
[21291.112049] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[21296.232024] usb 2-4: device descriptor read/64, error -71
[21306.584031] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[21322.832028] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[21323.084023] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[21333.332090] usb 2-4: reset high speed USB device using ehci_hcd and address 6
[21333.471244] scsi 9:0:0:0: Device offlined - not ready after error recovery
```
then:
```
pablo@vaughan:~$ sudo modprobe -r ehci_hcd
[sudo] password for pablo: 
FATAL: Module ehci_hcd is builtin
pablo@vaughan:~$ 

```
and then it automounted.

Could someone with more experience advice me if report a bug on launchpad is necessary ?

---

### Post by SeePU on 2010-07-14
I think it's a bug. 

I have similar output:
"FATAL: Module ehci_hcd not found."

I googled this and it seems like it's been a bug since 2004.  I suppose Ubuntu devs don't think it's important or they don't care that most of the population may wish to use usb devices.

---

