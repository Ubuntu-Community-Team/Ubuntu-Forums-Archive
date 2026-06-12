---
title: "Ubuntu 10.10 Login Script"
date: 2011-06-18
forum: General Help
---

### Post by gabrielshier on 2011-06-18
Hey, 
Want to add three lines to login script:
ifconfig wlan0 down
macchanger wlan0 00:11:22:33:44:55
ifconfig wlan0 up

all to be ran as root. Can anyone help please on how to add those to the basic login script (user or computer - the same) ?
Thanks.

---

### Post by Krytarik on 2011-06-18
Just add those commands to your "/etc/rc.local", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig wlan0 down
macchanger wlan0 00:11:22:33:44:55
ifconfig wlan0 up

exit 0
```Of course, you need root rights to do so:
```
gksudo gedit /etc/rc.local
```Greetings.

---

### Post by gabrielshier on 2011-06-18
Hey,

First of all, thanks for your time. Did that and found it. Still won't work. After i rebooted my pc still getting the same mac as if that script didn't ran at all. 
Any ideas for why that is?

---

### Post by hiukkanen on 2011-06-18
I think you have line

```
iface wlan0 inet dhcp
```

in your ```
/etc/networki/interfaces
```

If that is a case: Add line
```
hwaddress ether 00:11:22:33:44:55
``` after that line.

It should then look like

```
iface wlan0 inet dhcp
hwaddress ether 00:11:22:33:44:55
```

---

### Post by gabrielshier on 2011-06-20
Thanks alot!
Fixed it for me and now it works :)

---

