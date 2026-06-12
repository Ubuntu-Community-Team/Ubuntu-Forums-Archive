---
title: "usb drive not recognized"
date: 2012-07-18
forum: General Help
---

### Post by Ububtubobl on 2012-07-18
Usb Flash drives and external hard drives are not seen by the disk utility in Ubuntu 10.04. The system will boot to usb on start-up and widows xp recognizes it ( dual boot windows/Ubuntu ), but usb drives are unusable in Ubuntu. Any suggestions?

---

### Post by Whovian on 2012-07-18
Try the command 

```
dmesg | grep -i usb
```

to see what USB's are effected

---

### Post by Ububtubobl on 2012-07-20
> **Whovian said:**
> Try the command 

```
dmesg | grep -i usb
```to see what USB's are effected
robert@robert-desktop:~$ dmesg | grep -i usb
[    0.407688] usbcore: registered new interface driver usbfs
[    0.407714] usbcore: registered new interface driver hub
[    0.407761] usbcore: registered new device driver usb
[    0.738274] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.738389] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.755325] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.755479] usb usb1: configuration #1 chosen from 1 choice
[    0.755535] hub 1-0:1.0: USB hub found
[    0.755658] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.755683] uhci_hcd: USB Universal Host Controller Interface driver
[    0.755803] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.755980] usb usb2: configuration #1 chosen from 1 choice
[    0.756029] hub 2-0:1.0: USB hub found
[    0.756190] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.756380] usb usb3: configuration #1 chosen from 1 choice
[    0.756428] hub 3-0:1.0: USB hub found
[    0.756578] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.756761] usb usb4: configuration #1 chosen from 1 choice
[    0.756806] hub 4-0:1.0: USB hub found
[    0.756957] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.757149] usb usb5: configuration #1 chosen from 1 choice
[    0.757194] hub 5-0:1.0: USB hub found
[    1.340256] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.516349] usb 3-1: configuration #1 chosen from 1 choice
[    1.532840] usbcore: registered new interface driver hiddev
[    1.546524] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    1.546686] generic-usb 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.1-1/input0
[    1.546735] usbcore: registered new interface driver usbhid
[    1.546743] usbhid: v2.6:USB HID core driver
[    1.760059] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    1.914305] usb 3-2: configuration #1 chosen from 1 choice
[    1.929520] input: HID 04b3:3105 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    1.929645] generic-usb 0003:04B3:3105.0002: input,hidraw1: USB HID v1.00 Mouse [HID 04b3:3105] on usb-0000:00:1d.1-2/input0
robert@robert-desktop:~$

---

### Post by Whovian on 2012-07-20
well all the usb's are being recognized and seem to be working fine... I think the devices just aren't auto mounting in the system.

The community article on mounting [here]("https://help.ubuntu.com/community/Mount/USB") gives a good examples on how to if this problem an try a manual mount to get the devices to work in the mean time. Let me know what happens if this is the problem at all.

---

### Post by Ububtubobl on 2012-07-23
[B][SIZE=2] [/SIZE]
[/B]

**"Configuring Automounting**

 To enable or disable automount open a terminal and type **dconf-editor** followed by the **[Enter]** key. "


This is what the documentation suggests and this is what I get back from Terminal


"robert@robert-desktop:~$ dconf-editor 
No command 'dconf-editor' found, did you mean:
 Command 'gconf-editor' from package 'gconf-editor' (main)
dconf-editor: command not found
robert@robert-desktop:~$ 


[B]
[/B]

[B]
[/B]



**"Configuring Automounting**

 To enable or disable automount open a terminal and type **dconf-editor** followed by the **[Enter]** key. "

---

