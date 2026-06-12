---
title: "Connect to BT GPS receiver automatically"
date: 2009-11-06
forum: General Help
---

### Post by lotus49 on 2009-11-06
I have successfully connected my Bluetooth GPS receiver (Qstarz Q880) to my laptop (Acer Aspire One running 9.10) by creating an appropriate /etc/bluetooth/rfcomm.conf file and running

$ rfcomm connect 0

gpsd is configured and everything seems to be working OK.  However, I have two questions.

The first is that I have to run the above command twice, killing the first connection using ^C.  It seems to connect fine but only the second time.  Does anyone know why or how to avoid this?

My second question is can I set my machine up to do this automatically when the GPS receiver is switched on?  I know it's not a major hardship having to type the command in manually, but it doesn't seem a very elegant way of going about it.

PS There may be a clever way of doing this altogether of which I am unaware.  I got this working by following a very old thread somewhere on ubuntuforums.  If there is, a pointer would be most appreciated.

---

### Post by KeLa on 2009-11-06
Usually it's up to application that uses the gps receiver to activate the connection.
Every system that i have used does it this way.

---

### Post by lotus49 on 2009-11-06
Of the three applications I have tried, none does this.

I have tried xgps, gpsdrive and kismet.  xgps and kismet rely on gpsd (gpsdrive may as well AFAIK) which is run at boot time (ie before the GPS receiver is necessarily turned on) and so it's hard to see how the apps could effectively start rfcomm.

---

