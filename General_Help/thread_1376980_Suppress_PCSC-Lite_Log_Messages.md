---
title: "Suppress PCSC-Lite Log Messages"
date: 2010-01-09
forum: General Help
---

### Post by slalomchip on 2010-01-09
I configured Ubuntu 9.10 for a ExpressCard SmartCard reader (CAC card) for my laptop.  I use the SmartCard infrequently.  My logged messages in /etc/log/messages is overwhelmed with pscsd messages saying 

*Jan  9 10:44:27 [laptop-name] pcscd: eventhandler.c:333:EHStatusHandlerThread() Error communicating to: SCM SCR 3340 ExpressCard54 (21220713704118) 00 00*

if the card is not present in the reader

or 

*Jan  9 19:13:16 [laptop-name] pcscd: winscard.c:309:SCardConnect() Reader E-Gate 0 0 Not Found*

if the card reader is removed from the ExpressCard slot.

I would like to suppress these messages (and only these messages).  Does anyone know how I can do that?

Many Thanks.

---

### Post by slalomchip on 2010-01-09
Oops - I meant the log messages in /var/log/messages, not etc/log/messages.  Sorry

---

