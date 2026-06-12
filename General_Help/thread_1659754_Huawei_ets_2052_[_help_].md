---
title: "Huawei ets 2052 [ help ]"
date: 2011-01-04
forum: General Help
---

### Post by rubbernackin on 2011-01-04
[B]Hello brother i'm from indonesia..

i have a problem with my HUAWEI ETS 2052..
i'm using Ubuntu 10.04 LTS
i've already install usb-modeswitch..

and my linux kernel detected the modem
but after i run following command
" wvdialconf "
i got this
"[/B]
root@project-desktop:~# wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.**"**

[B]then i try this command
" dmesg | tail "
i got this to 
"[/B]
root@project-desktop:~# dmesg | tail
[  883.440034] usb 2-1: device descriptor read/64, error -110
[  898.656029] usb 2-1: device descriptor read/64, error -110
[  898.872019] usb 2-1: new full speed USB device using uhci_hcd and address 12
[  913.984022] usb 2-1: device descriptor read/64, error -110
[  929.200023] usb 2-1: device descriptor read/64, error -110
[  929.416017] usb 2-1: new full speed USB device using uhci_hcd and address 13
[  939.824024] usb 2-1: device not accepting address 13, error -110
[  939.936025] usb 2-1: new full speed USB device using uhci_hcd and address 14
[  950.344022] usb 2-1: device not accepting address 14, error -110
[  950.344047] hub 2-0:1.0: unable to enumerate USB device on port 1
root@project-desktop:~# [B]"


anyone help me with this... :cry:[/B]

---

