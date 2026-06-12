---
title: "gammu-smsd error"
date: 2009-12-25
forum: General Help
---

### Post by rabidityfactor on 2009-12-25
Hi. I get get the 'DataBase structures are from higher Gammu version' error when I start gammu-smsd daemon.

```
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: Configuring Gammu SMSD...
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: SHM token: 0xffffffffce025713 (-838707437)
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: PIN code is "1234"
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: commtimeout=30, sendtimeout=30, receivefrequency=0, resetfrequency=0, checksecurity=1
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: deliveryreport = sms
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: phoneid = 
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: **Database structures version: 11, SMSD current version: 10**
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: **DataBase structures are from higher Gammu version**
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: Please update this client application
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: Initialisation failed, stopping Gammu smsd (Unknown error.:27)
```

Everything has been updated, and I still get the error. Im trying to setup kalkun sms managemnt.
Thanks in advance

---

### Post by back2arie on 2009-12-26
> **rabidityfactor said:**
> Hi. I get get the 'DataBase structures are from higher Gammu version' error when I start gammu-smsd daemon.

```
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: Configuring Gammu SMSD...
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: SHM token: 0xffffffffce025713 (-838707437)
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: PIN code is "1234"
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: commtimeout=30, sendtimeout=30, receivefrequency=0, resetfrequency=0, checksecurity=1
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: deliveryreport = sms
Sat 2009/12/26 10:09:47 gammu-smsd[10395]: phoneid = 
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: **Database structures version: 11, SMSD current version: 10**
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: **DataBase structures are from higher Gammu version**
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: Please update this client application
Sat 2009/12/26 10:09:47 gammu-smsd[10396]: Initialisation failed, stopping Gammu smsd (Unknown error.:27)
```Everything has been updated, and I still get the error. Im trying to setup kalkun sms managemnt.
Thanks in advance

Hi
You need to downgrade the Database structures.

Try this on your mysql console:

mysql> UPDATE gammu set Version='10';

---

### Post by rabidityfactor on 2009-12-29
Wow! Thanks a million back2arie. It worked.

---

