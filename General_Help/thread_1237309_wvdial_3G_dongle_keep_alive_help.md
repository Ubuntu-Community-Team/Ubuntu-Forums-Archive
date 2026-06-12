---
title: "wvdial 3G dongle keep alive help"
date: 2009-08-11
forum: General Help
---

### Post by markytheone on 2009-08-11
Hi guys, I have a dongle connected to my laptop running Hardy server. I can connect to the internet first by putting my SIM pin in through minicom AT+CPIN=1234. Then I use

#wvdial three

Now, as the train moves and the connection dies (due to poor signal), I cannot reconnect the connection using the same command as all I get is:

voyage:~# wvdial three
--> WvDial: Internet dialer version 1.56
--> Cannot open /dev/ttyUSB1: Device or resource busy
--> Cannot open /dev/ttyUSB1: Device or resource busy
--> Cannot open /dev/ttyUSB1: Device or resource busy

Is there anyway to make sure the connection is astill alive and kill it if not?

thanks

Mark

---

### Post by markytheone on 2009-08-11
Comon guys....anyone?

---

### Post by GeorgeVita on 2009-08-11
Hi **markytheone**,
the problem you have may caused for 2 reasons. Either **wvdial** (or minicom) are holding the /dev/ttyUSB1 port or the USB modem come to an 'unavailable' state.

Some checks to do (it is better to remove "SIM PIN check" (as you will have one thing less to interfere):

Just after the disconnection, open  a terminal window and type: **dmesg**
Post here last lines including any possible disconnection.

Notes: it is better to remove "SIM PIN check" as you will have one thing less to interfere.
Also you can use **wvdial** to send "AT+PIN=1234" command, adding an extra paragraph to the /etc/wvdial.conf file:

> [Dialer myPIN]
Init4 = AT+CPIN=1234

You can send the PIN with: **sudo wvdial myPIN** (ignore the error messages)

In any case POST here ALL your /etc/wvdial.conf file together with full data of your modem: manufacturer, model (look at ths sticker on it) and  the output of **lsusb** when attached.

Regards,
George

---

