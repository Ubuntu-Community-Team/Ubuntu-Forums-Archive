---
title: "Startup Application"
date: 2011-10-31
forum: General Help
---

### Post by joeheim on 2011-10-31
Hi,

my Laptop is a Sony Vaio VPCZ128GG.

With the following command I can turn on the backlight function:

sudo sh -c 'echo 1 > /sys/devices/platform/sony-laptop/kbd_backlight'

I would like to start it right up from the beginning. I'll tried to implement it as a command in the Startup Application Preferences, but it does not work.

Any suggestions?

---

### Post by matt_symes on 2011-10-31
Hi

Add it to rc.local. From a terminal

```
sudo nano /etc/rc.local
```

Enter you password. It will not be echoed to the screen.

Add the command to the file but remove the sudo and quotes.

```
echo 1 > /sys/devices/platform/sony-laptop/kbd_backlight
```

Kind regards

---

### Post by joeheim on 2011-10-31
Perfect !!! It works!!!

Thanks for your quick reply !!

---

