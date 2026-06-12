---
title: "When reconnecting a USB keyboard to my system, I got this stream of messages in `/var"
date: 2011-04-01
forum: General Help
---

### Post by intuited on 2011-04-01
When reconnecting a USB keyboard to my system, I got this stream of messages in `/var/log/syslog`:


```
    Mar 31 22:35:01 gatsby kernel: [442633.491562] usb 2-1.2: new low speed USB device using ehci_hcd and address 79
    Mar 31 22:35:01 gatsby kernel: [442633.579057] ehci_hcd 0000:00:1d.0: fatal error
    Mar 31 22:35:01 gatsby kernel: [442633.585381] ehci_hcd 0000:00:1d.0: force halt; handshake ffffc90000674824 00004000 00004000 -> -110
    Mar 31 22:35:01 gatsby kernel: [442633.585389] ehci_hcd 0000:00:1d.0: HC died; cleaning up
    Mar 31 22:35:01 gatsby kernel: [442633.598955] usb 2-1.2: device descriptor read/all, error -108
    Mar 31 22:35:01 gatsby kernel: [442633.598961] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598974] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598977] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598983] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598987] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598992] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598995] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598998] hub 2-1:1.0: unable to enumerate USB device on port 2
    Mar 31 22:35:01 gatsby kernel: [442633.599002] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.599015] usb 2-1: USB disconnect, address 2

```
A normal set of log messages for the same event looks like this:

```
    Mar 31 16:36:44 gatsby kernel: [421175.156518] usb 2-1.2: new low speed USB device using ehci_hcd and address 74
    Mar 31 16:36:44 gatsby kernel: [421175.278006] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input63
    Mar 31 16:36:44 gatsby kernel: [421175.278256] generic-usb 0003:413C:2003.0038: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.2/input0

```
Since that error was logged, the system will no longer respond to the connection of USB devices.  There is no record of these events in either `/var/log/syslog` or via `dmesg`.

I'm running 10.10 on an Acer Aspire 5742 laptop.  It may be relevant that both my HECI controller and SMBus show up as `UNCLAIMED` in the output from `lshWhen reconnecting a USB keyboard to my system, I got this stream of messages in `/var/log/syslog`:


```
    Mar 31 22:35:01 gatsby kernel: [442633.491562] usb 2-1.2: new low speed USB device using ehci_hcd and address 79
    Mar 31 22:35:01 gatsby kernel: [442633.579057] ehci_hcd 0000:00:1d.0: fatal error
    Mar 31 22:35:01 gatsby kernel: [442633.585381] ehci_hcd 0000:00:1d.0: force halt; handshake ffffc90000674824 00004000 00004000 -> -110
    Mar 31 22:35:01 gatsby kernel: [442633.585389] ehci_hcd 0000:00:1d.0: HC died; cleaning up
    Mar 31 22:35:01 gatsby kernel: [442633.598955] usb 2-1.2: device descriptor read/all, error -108
    Mar 31 22:35:01 gatsby kernel: [442633.598961] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598974] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598977] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598983] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598987] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598992] hub 2-1:1.0: cannot reset port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598995] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.598998] hub 2-1:1.0: unable to enumerate USB device on port 2
    Mar 31 22:35:01 gatsby kernel: [442633.599002] hub 2-1:1.0: cannot disable port 2 (err = -19)
    Mar 31 22:35:01 gatsby kernel: [442633.599015] usb 2-1: USB disconnect, address 2

```
A normal set of log messages for the same event looks like this:

```
    Mar 31 16:36:44 gatsby kernel: [421175.156518] usb 2-1.2: new low speed USB device using ehci_hcd and address 74
    Mar 31 16:36:44 gatsby kernel: [421175.278006] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input63
    Mar 31 16:36:44 gatsby kernel: [421175.278256] generic-usb 0003:413C:2003.0038: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.2/input0

```
Since that error was logged, the system will no longer respond to the connection of USB devices.  There is no record of these events in either `/var/log/syslog` or via `dmesg`.

I'm running 10.10 on an Acer Aspire 5742 laptop.  It may be relevant that both my HECI controller and SMBus show up as `UNCLAIMED` in the output from `lshw`.  They are both listed as being `/^\s*product: 5 Series/3400 Series Chipset (HECI|SMBus) Controller/`.

I'm booting with the `acpi_osi=` kernel argument.

I'd like to know how I can

[LIST]
[*]recover from such situations without rebooting the machine
[*]prevent these problems from occurring in the first place.
[/LIST]

I tried

    $ sudo modprobe -r usbhid ; sudo modprobe usbhid

This logged the following to `/var/log/syslog`


```
    Apr  1 00:41:10 gatsby kernel: [450189.768916] usbcore: deregistering interface driver usbhid
    Apr  1 00:41:10 gatsby kernel: [450189.768960] usbcore: deregistering interface driver hiddev
    Apr  1 00:41:10 gatsby kernel: [450189.823210] usbcore: registered new interface driver hiddev
    Apr  1 00:41:10 gatsby kernel: [450189.823246] usbcore: registered new interface driver usbhid
    Apr  1 00:41:10 gatsby kernel: [450189.823250] usbhid: USB HID core driver

```
but otherwise had no effect: newly-connected USB devices still do not work, nor are any syslog messages generated in response to their connection.

I tried connecting devices to two different USB ports on different sides of the machine, both to the same non-effect.

I've posted similarly at [Ubuntu questions]("https://answers.launchpad.net/ubuntu/+question/151251") and at [AskUbuntu.com]("http://askubuntu.com/questions/32961/recovering-from-and-preventing-usb-errors").w`.  They are both listed as being `/^\s*product: 5 Series/3400 Series Chipset (HECI|SMBus) Controller/`.

I'm booting with the `acpi_osi=` kernel argument.

I'd like to know how I can

[LIST]
[*]recover from such situations without rebooting the machine
[*]prevent these problems from occurring in the first place.
[/LIST]

I tried

```
    $ sudo modprobe -r usbhid ; sudo modprobe usbhid

```
This logged the following to `/var/log/syslog`


```
    Apr  1 00:41:10 gatsby kernel: [450189.768916] usbcore: deregistering interface driver usbhid
    Apr  1 00:41:10 gatsby kernel: [450189.768960] usbcore: deregistering interface driver hiddev
    Apr  1 00:41:10 gatsby kernel: [450189.823210] usbcore: registered new interface driver hiddev
    Apr  1 00:41:10 gatsby kernel: [450189.823246] usbcore: registered new interface driver usbhid
    Apr  1 00:41:10 gatsby kernel: [450189.823250] usbhid: USB HID core driver

```
but otherwise had no effect: newly-connected USB devices still do not work, nor are any syslog messages generated in response to their connection.

I tried connecting devices to two different USB ports on different sides of the machine, both to the same non-effect.

I've posted similarly at [Ubuntu questions]("https://answers.launchpad.net/ubuntu/+question/151251") and at [AskUbuntu.com]("http://askubuntu.com/questions/32961/recovering-from-and-preventing-usb-errors").

---

