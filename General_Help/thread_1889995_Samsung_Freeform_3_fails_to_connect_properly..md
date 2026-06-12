---
title: "Samsung Freeform 3 fails to connect properly."
date: 2011-12-02
forum: General Help
---

### Post by pengyou on 2011-12-02
hello all,
I have a Samsung Freeform 3.
It connects properly to Windows, but I don't want to switch to windows to edit the contents of my MicroSD (I have no SD slot and I have no MicroSD usb adapter).
I have googled and googled, and found "dmesg" and "lsusb" are what you want.
So, I will unplug...
```
[  863.025947] qcaux 2-1.1:1.2: device disconnected
```And I will replug...
```
[  878.983022] usb 2-1.2: new full speed USB device number 12 using ehci_hcd
[  879.077877] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[  879.081358] qcaux 2-1.2:1.2: qcaux converter detected
[  879.081488] usb 2-1.2: qcaux converter now attached to ttyUSB0
```lsusb:
```

Bus 002 Device 013: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator

```Now I note that it says it is a Modem, this is something new, I assume this has arisen due to my actions, as I have just modified /etc/modules as per instructions in a thread found via google.
This seems to make some threads I have read relevant to my issue, but unfortunately I do not have a file in /lib/udev/rules.d that contains the word "modem" in it's name.
Running oneiric...
Thanks

---

### Post by pengyou on 2011-12-02
I also entered the commands:
```

sudo modprobe -r usb-storage

```and
```

sudo modprobe usb-storage option_zero_cd=2

```In the current boot.

The second line:
```

 usb-storage option_zero_cd=2

```reflects the line I placed in /etc/modules as per the aforementioned instructions.

As I said before, identifying the device as a modem is a new event, as before it was identified as usb storage, or something (I did not copy paste, as I expected this behavior to persist).

---

### Post by pengyou on 2011-12-05
bump

---

