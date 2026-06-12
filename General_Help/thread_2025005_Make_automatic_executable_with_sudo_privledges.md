---
title: "Make automatic executable with sudo privledges"
date: 2012-07-14
forum: General Help
---

### Post by CrusaderAD on 2012-07-14
I have a wireless usb network adapter that needs a couple commands executed after each reboot in order for it to work. Does anyone have any ideas for executing these automatically on boot up? They need sudo privledges. Here they are:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```

and

```
modprobe -v rt2800usb
```

---

### Post by Toz on 2012-07-14
If you add these commands to /etc/rc.local (before the *exit 0* command), they will be executed with root privileges on each boot - therefore, you will not need to use the sudo command.

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | tee /etc/modprobe.d/rt2800usb.conf
```
and
```
modprobe -v rt2800usb
```

---

### Post by CrusaderAD on 2012-07-14
Cool, I think that worked perfect. Thanks!

---

