---
title: "Printer Error =&gt; Printing Completed"
date: 2012-07-18
forum: General Help
---

### Post by frogotronic on 2012-07-18
Hi,

  I have a Brother HL3040CN printer and I have installed the driver as per Brother's instructions.  I can print without problems to the printer via a LAN network.

  However, whenever I print, I get an immediate notification that there is a communication error with the printer, then, after about five seconds, I get a notification stating that the print job completed sucessfully.

  What's going on?  I think it might have something to do with this part of the install:

```
$sudo aa-complain cupsd
sudo: aa-complain: command not found
```

Any suggestions?

- CH

---

### Post by frogotronic on 2012-07-18
```
$sudo apt-get install apparmor-utils

$sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
```

---

