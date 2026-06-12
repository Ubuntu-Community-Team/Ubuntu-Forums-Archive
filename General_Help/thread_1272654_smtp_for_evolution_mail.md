---
title: "smtp for evolution mail"
date: 2009-09-22
forum: General Help
---

### Post by oldtraveler on 2009-09-22
[color=red]SOLVED by changing to "Security: TLS encryption" from SSL.[/color]

Using the setting for Hotmail pop ([http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide](http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide)) I am able to receive hotmail but when I try to send via hotmail pop I get an error message stating that Evolution can't access the server at smtp.live.com. In this regard I am unable to access "check for supported types of authentication".  I've tried several types, but without success. Also on another pc I have used Outlook Express to send via hotmail pop successfully using the same settings as with Evolution.

---

### Post by i.r.id10t on 2009-09-22
Your ISP may be blocking outgoing connections to the SMTP server since it isn't on their network.

---

### Post by philinux on 2009-09-22
> **oldtraveler said:**
> Using the setting for Hotmail pop ([http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide](http://lifehacker.com/5169684/hotmail-finally-enables-pop3-worldwide)) I am able to receive hotmail but when I try to send via hotmail pop I get an error message stating that Evolution can't access the server at smtp.live.com. In this regard I am unable to access "check for supported types of authentication".  I've tried several types, but without success. Also on another pc I have used Outlook Express to send via hotmail pop successfully using the same settings as with Evolution.

Settings need to be:-

Server= smtp.live.com:25
Requires Authentication should be ticked and the option should be TLS  encryption.

---

