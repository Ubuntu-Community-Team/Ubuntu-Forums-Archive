---
title: "USB0 missing"
date: 2011-04-23
forum: General Help
---

### Post by Robbyx on 2011-04-23
I connect my mobile phone to Ubuntu and I get an error message that usb0 is not available. Here is the log:

```

--------------- System information ----------------
Platform     linux2
Python       2.6.6
wxPython     2.8.11.0
Wammu        0.35
python-gammu 1.28.0
Gammu        1.28.0
Bluetooth    PyBluez
locales      en_GB (UTF8)
connection   at19200
device       /dev/ttyUSB0
model        auto
Sat 2011/04/23 14:45:24: [Gammu            - 1.28.0 built 13:19:33 Jul 12 2010 using GCC 4.4]
Sat 2011/04/23 14:45:24: [Connection       - "at19200"]
Sat 2011/04/23 14:45:24: [Connection index - 0]
Sat 2011/04/23 14:45:24: [Model type       - ""]
Sat 2011/04/23 14:45:24: [Device           - "/dev/ttyUSB0"]
Sat 2011/04/23 14:45:24: [Runing on        - Linux, kernel 2.6.35-28-generic-pae (#50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011)]
Sat 2011/04/23 14:45:24: [System error     - open in serial_open, 2, "No such file or directory"]
Sat 2011/04/23 14:45:24: Init:GSM_TryGetModel failed with error DEVICENOTEXIST[4]: Error opening device, it doesn't exist.
Sat 2011/04/23 14:45:24: Entering GSM_SetIncomingSMS
Sat 2011/04/23 14:45:24: Entering GSM_SetIncomingCall
Sat 2011/04/23 14:45:24: Entering GSM_SetIncomingCB
Sat 2011/04/23 14:45:24: Entering GSM_SetIncomingUSSD
```

**Any ideas how to create the device?**

---

### Post by Robbyx on 2011-04-24
Has anyone found a solution to a missing USB port?

---

