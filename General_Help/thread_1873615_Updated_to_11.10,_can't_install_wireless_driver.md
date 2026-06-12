---
title: "Updated to 11.10, can't install wireless driver"
date: 2011-11-01
forum: General Help
---

### Post by yourselff on 2011-11-01
Wireless was working on 11.04, now can't get additional drivers to add the wireless driver. Help? Thank you.

---

### Post by yourselff on 2011-11-01
This thing on?

---

### Post by yourselff on 2011-11-01
Goodbye Ubuntu! I tried!

---

### Post by serpentracer on 2011-11-01
sheesh dude you didn't give people enough time to see your post.

try searching google for ubuntu drivers your network card.  that's how i had to find mine.  for some reason as popular as the card is, a 3rd party had to make the drivers for it.

---

### Post by xianbei on 2011-11-01
broadcom wireless device?

you've probably got a wireless device that has proprietary drivers. 

type:
```
lspci -vvnn | grep 14e4
```

you should see what you have for a wireless device. then do a google search to find instructions on installing those drivers for ubuntu.

or, if it's a broadcom wireless device, check this handy link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

i have to go through this every time i install a new linux distro on my acer laptop. no biggie...

---

### Post by yourselff on 2011-11-02
Thanks man! Worked like a charm. Sorry for being impatient, but that was the second thread I made that wasn't getting responses.

Many thanks.

---

### Post by serpentracer on 2011-11-02
yeah I got the same darn card.

---

