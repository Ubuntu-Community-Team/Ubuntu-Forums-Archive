---
title: "E220 modem problem"
date: 2010-08-27
forum: General Help
---

### Post by bigseb on 2010-08-27
I use Hauwei E220 modem to connect to the internet but for some reason it doesn't want to connect anymore. It works perfectly in XP, it picks just about every wireless network in my area (which I have no access to), it works beautifully if I plug it in *before* switching on my PC. If, however, I plug it in when the PC is on then nothing :(

What's wrong and how do I fix it?

Strangely, it used to work fine then somehow forgot what its supposed to do...

---

### Post by bigseb on 2010-08-30
bump

---

### Post by nathan726 on 2010-08-31
Try this...

Run:
```

sudo gedit /etc/modules
```

And at the bottom add:
```
usbserial
option
```

Save and reboot.

---

### Post by bigseb on 2010-08-31
> **nathan726 said:**
> Try this...

Run:
```

sudo gedit /etc/modules
```And at the bottom add:
```
usbserial
option
```Save and reboot.
Hi Nathan, great to hear from you again!! Will try once I have a minute to spare...

---

### Post by bigseb on 2010-09-01
It works like charm now. Thanks!!

---

### Post by gandaran on 2010-09-01
> **nathan726 said:**
> Try this...

Run:
```

sudo gedit /etc/modules
```

And at the bottom add:
```
usbserial
option
```

Save and reboot.
nathan
I'm just curious, I had a similar problem before and adding usbserial to /etc/modules didn't help, so what does the "option" under usbserial do?

---

### Post by nathan726 on 2010-09-03
> what does the "option" under usbserial do?
It's a usb serial driver.

---

