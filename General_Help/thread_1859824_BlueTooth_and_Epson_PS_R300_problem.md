---
title: "BlueTooth and Epson PS R300 problem"
date: 2011-10-14
forum: General Help
---

### Post by coldraven on 2011-10-14
I had not used my printer for a while until I got some new re-fillable cartridges.
Now it will not print via Bluetooth. The printer is located about 8 feet away in line of sight on the other side of the room.
It prints fine via cable.
I have tried this in 10.10 and 11.04 and get the same result.
I can add a new printer and all the parameters seem OK.

From the LCD screen on the printer, Bluetooth settings:
Printer name: Stylus Photo R300-0
The PIN number is set to: 0000.
Communication mode: Public
Encryption: Off
Device address: 00:02:5B:01:F4:A4


From the terminal
```
 hcitool scan
Scanning ...
    00:02:5B:01:F4:A4    Stylus Photo R300-0

```

Anyone have an idea?

---

### Post by coldraven on 2011-10-15
Solved! I found this post [http://ubuntuforums.org/showpost.php?p=10385441&postcount=2](http://ubuntuforums.org/showpost.php?p=10385441&postcount=2)
I added Brian Rogers PPA and updated to these packages

[LIST]
[*]bluez-4.84-~0maverick
[*]         bluez-alsa-4.84-~0maverick
[*]         bluez-compat-4.84-~0maverick
[*]         bluez-cups-4.84-~0maverick
[*]         bluez-gstreamer-4.84-~0maverick
[*]         bluez-pcmcia-support-4.84-~0maverick
[*]         libbluetooth-dev-4.84-~0maverick
[*]         libbluetooth3-4.84-~0maverick
[/LIST]
Thanks Brian :)

---

