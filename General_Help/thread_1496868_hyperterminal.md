---
title: "hyperterminal"
date: 2010-05-29
forum: General Help
---

### Post by mick463 on 2010-05-29
can some one please tell me how to get a hyperterminal session in linux .
i have an asus laptop with only usb and a aten usb to serial converter which i do not know how to get to work please help.

---

### Post by mick463 on 2010-05-29
please some one help i am desperate

---

### Post by capscrew on 2010-05-29
> **mick463 said:**
> please some one help i am desperate
Try Minicom.  See [**_here_**]("https://help.ubuntu.com/community/SerialConsoleHowto").

---

### Post by bakegoodz on 2010-05-29
To use minicomm you will have set the serial device name. With a USB adapter it is probably /dev/USBtty0
You can plug it in and run dmesg to find the device name

Or alternalty 
ls /dev/* > /tmp/1
plug or unplug device
ls /dev/* > /tmp/2
diff /tmp/1 /tmp/2

---

### Post by thirdgen88 on 2010-05-30
The device will probably be /dev/ttyUSB0, not USBtty0...

---

### Post by mick463 on 2010-06-06
thank you miniterm is the easiest

---

