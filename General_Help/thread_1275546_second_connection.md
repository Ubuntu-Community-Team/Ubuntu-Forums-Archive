---
title: "second connection"
date: 2009-09-25
forum: General Help
---

### Post by cherith on 2009-09-25
I wish to add  a second, different ISP to ubuntu9.04.Wvdial.conf exhibits my current details. How do I add another ISP without deleting my current ISP.

---

### Post by GeorgeVita on 2009-09-26
Hi **cherith**, welcome to this forum!

To add parameters for another ISP (or another modem) you can add a new section into your **/etc/wvdial.conf** file. All info and some examples can be found 'running' the following command from a terminal window: ```
man wvdial.conf
``` Under the label [Dialer Defaults] are the 'common' or 'default' parameters and other 'alternative options' must be included under a new [Dialer 2ndISP] (any descriptive title is OK).
To connect you can use **sudo wvdial** if you want the 'default' ISP or **sudo wvdial 2ndISP** for your 'new' ISP.

Below is a real example I am using to connect via some 3G modems to my local ISPs using different USB ports: ```
[Dialer Defaults]
New PPPD = yes
Dial Command = ATDT
Dial Attempts = 1
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet"
Phone = *99***1#
Stupid Mode = 1

[Dialer wind]
Username = web
Password = web
Init3 = AT+CGDCONT=1,"IP","gint.b-online.gr"

[Dialer cosmote]
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer vodafone]
Init3 = AT+CGDCONT=1,"IP","internet"

[Dialer MF636]
Modem = /dev/ttyUSB2

[Dialer E169]
Modem = /dev/ttyUSB0

[Dialer E170]
Modem = /dev/ttyUSB0

[Dialer E220]
Modem = /dev/ttyUSB0

[Dialer 0]
Modem = /dev/ttyUSB0

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2

```

Note that a 'duplicate' parameter replaces the previous one!
For connection to 'vodafone' using my 'E169' modem, I use: **sudo wvdial E169 vodafone**

**Post** all your parameters and your existing /etc/wvdial.conf file to fix it.

Regards,
George

---

