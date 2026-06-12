---
title: "random freezes?"
date: 2010-05-18
forum: General Help
---

### Post by KwukDuck on 2010-05-18
[FONT=Verdana][SIZE=2]Since of today it seems my pc freezes randomly, these are the messages that got logged just before it froze: (i tried disconnecting the usb-mouse to get input again, it registered that, but didn't help)

```

May 18 15:52:36 pc-003 kernel: [ 1507.820656] Monitor-Mwait will be used to enter C-3 state
May 18 15:53:43 pc-003 kernel: [ 1574.198833] ===>rt_ioctl_giwscan. 24(24) BSS returned, data->length = 3127
May 18 15:53:50 pc-003 kernel: [ 1581.418314] usb 3-1: USB disconnect, address 2

```[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]```
May 18 19:06:40 pc-003 kernel: [84960.004358] ACPI Error (dsfield-0143): [CB04] Namespace lookup failure, AE_ALREADY_EXISTS 
May 18 19:06:40 pc-003 kernel: [84960.004373] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f7012a68), AE_ALREADY_EXISTS 
May 18 19:06:40 pc-003 kernel: [84960.004389] ACPI: Marking method WMCA as Serialized because of AE_ALREADY_EXISTS error 
May 18 19:07:17 pc-003 kernel: [84997.208160] usb 2-1: USB disconnect, address 2 
May 18 19:07:19 pc-003 kernel: [84998.944042] usb 2-1: new full speed USB device using uhci_hcd and address 3 
May 18 19:07:19 pc-003 kernel: [84999.126654] usb 2-1: configuration #1 chosen from 1 choice 
May 18 19:07:19 pc-003 kernel: [84999.134916] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input11 
May 18 19:07:19 pc-003 kernel: [84999.135129] generic-usb 0003:046D:C51A.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0 
May 18 19:07:19 pc-003 kernel: [84999.139768] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input12 
May 18 19:07:19 pc-003 kernel: [84999.140578] generic-usb 0003:046D:C51A.0004: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1 
May 18 19:10:07 pc-003 kernel: imklog 4.2.0, log source = /proc/kmsg started.
```[/COLOR][/SIZE][/FONT]

```
[COLOR=#000000][FONT=Segoe UI][SIZE=3]May 18 22:03:23 pc-003 kernel: [10406.004103] ACPI Error (dsfield-0143): [CB04] Namespace lookup failure, AE_ALREADY_EXISTS 
May 18 22:03:23 pc-003 kernel: [10406.004117] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node f7012a68), AE_ALREADY_EXISTS 
May 18 22:03:23 pc-003 kernel: [10406.004133] ACPI: Marking method WMCA as Serialized because of AE_ALREADY_EXISTS error 
May 18 22:03:24 pc-003 kernel: [10406.765256] usb 5-2: new full speed USB device using uhci_hcd and address 3 
May 18 22:03:24 pc-003 kernel: [10406.942512] usb 5-2: configuration #1 chosen from 1 choice[/SIZE][/FONT][/COLOR]
```Anyone knows what these messages may mean?

---

### Post by breek on 2010-05-18
lots of people (me included) are having the same (or similar) issue.
please post [here]("http://ubuntuforums.org/showthread.php?t=1478787")

---

