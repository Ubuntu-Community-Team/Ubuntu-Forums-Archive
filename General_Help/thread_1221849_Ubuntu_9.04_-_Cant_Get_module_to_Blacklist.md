---
title: "Ubuntu 9.04 - Cant Get module to Blacklist"
date: 2009-07-24
forum: General Help
---

### Post by jseiser on 2009-07-24
I used to be able to stick 'blacklist ath5k' into the /etc/modprobe.d/blacklist.conf file and it would stop the ath5k driver from starting.   It doesnt work well and its easier to just use my usb wireless card.  Well since I upgraded this laptop to jaunty that command no longer works.  I can run 'modprobe -r ath5k' and it will bring the module down but the blacklist.conf does nothing.  Is there another way to blacklist a file?  I would even be ok with creating a file that said modprobe -r ath5k and having it run at startup.  Any ideas would be great.  Thank you.

---

### Post by jseiser on 2009-07-24
Anyone know how to run a command as root on boot?  I want to run modprobe -r ath5k

---

### Post by jseiser on 2009-07-24
I found this on the internet but it doesnt work either
```

$chmod +x FOO
update-rc.d FOO defaults

```

FOO is a file that reads #!bin/bash modprobe -r ath5k - That does not stop the moduule from loading either.

---

