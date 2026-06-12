---
title: "How do I add commands to startup? (so internet starts automatically)"
date: 2010-01-22
forum: General Help
---

### Post by oni-kun on 2010-01-22
I have ndiswrapper and my old usb wireless card up and running, but I have to run the following to get it up:

```
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid MyEssid key 0000000 mode Managed
sudo ifconfig wlan0 up
dhcpcd -t 60
```

To get my wifi set up. How do I add it into a script (like a batch file as like windows has.. can't figure out how) Or in startup? xinit I suppose or something

Please help, It's so annoying to have to manually do this!

EDIT: Besides security issues, can I use sudo w/o password ? or do I need it onstartup.. Confusing stuff. O_o;

---

### Post by pmlxuser on 2010-01-22
easy creat a script Say names wake_wireless then
```

$cd /sbin
$sudo cat <<EOF > wake_wireless
>#! /bin/bash
>sudo ifconfig eth0 down
>sudo ifconfig wlan0 up
>sudo iwconfig wlan0 essid MyEssid key 0000000 mode Managed
>sudo ifconfig wlan0 up
>dhcpcd -t 60
>EOF

$sudo chmod +x wake_wireless

```

you would then go >system >preferences>  prefered application >add >wake_wireless

It might require you to supply sudo password i guess.

---

### Post by oni-kun on 2010-01-22
I added them using the XFCE sessions/startup menu, as long as the bootup process doesn't explode becuase of needing to enter a password, it should work fine. :popcorn:

I'll definately impliment the script if it doesn't work.

---

### Post by kerry_s on 2010-01-22
you can put the commands in /etc/rc.local & it will run as root so you don't need sudo.

why are you running "sudo ifconfig wlan0 up" twice ?

---

