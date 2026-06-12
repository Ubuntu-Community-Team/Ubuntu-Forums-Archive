---
title: "Permanently Disable Bluetooth"
date: 2011-10-15
forum: General Help
---

### Post by gbonfiglio on 2011-10-15
Hello,

i'm using a Dell Inspiron Mini 10, which has a Bluetooth device.

I don't use it so often. Moreover, i want my netbook to use the lowest  quantity of battery power so that i can use it for 3/4 hours without  plugging it. So that, in Ubuntu 11.04, after having understood that  turning Bluetooth off from the system tray was not a permanent setting, i  had removed it from System Startup Applications.

Yesterday i've upgraded to 11.10 and it was turned on again. In  addition, now, in Startup Applications I only see Dropbox and the  Calendar, nothing else.

I know I can disable it from the BIOS, but don't want to do this so that  I can turn it on as soon as I need it. The alternative solution is  manually editing runlevels, but this only prevent the bluetooth daemon  to start: the management software and the tray icon still remains there.

Can someone please help me?

Thankyou

---

### Post by effenberg0x0 on 2011-10-15
Well, you can remove it.

```
sudo apt-get remove bluez bluetooth
```

regards,
Effenberg

---

### Post by gbonfiglio on 2011-10-15
Well, this could be a solution, thankyou.

I was just wondering why in 11.10 there isn't anymore that perfect and detailed startup applications management...

---

### Post by mc4man on 2011-10-15
If you want to keep blue* but turn off & disable the applet then - 
you can turn off in System Settings
To disable the applet
```
gksudo gedit /etc/xdg/autostart/bluetooth-applet-unity.desktop
```
Remove the NoDisplay=true line & space it occupied, save
You'll then see it it Startup Applications & can disable

---

### Post by gbonfiglio on 2011-10-15
Thankyou. This is perfect.

There is another strange behavior: i've always used apt-get to install or remove software, but today i've decided to try Ubuntu Package Manager, in order to cleanup my system.

So that, i've "Removed" many package, but, then, launching a:

```
dpkg --get-selections
```

I noticed all those packages were still there:

```
giorgio@GNetbook1:~$ dpkg --get-selections |grep -v lib |grep deinstall
abiword                                         deinstall
abiword-common                                  deinstall
ace-of-penguins                                 deinstall
audacious                                       deinstall
capplets-data                                   deinstall
easycrypt                                       deinstall
esound-common                                   deinstall
evolution                                       deinstall
galculator                                      deinstall
gnome-mplayer                                   deinstall
gnome-orca                                      deinstall
gnome-panel                                     deinstall
gnome-panel-bonobo                              deinstall
gnumeric                                        deinstall
indicator-applet                                deinstall
language-support-writing-en                     deinstall
leafpad                                         deinstall
mplayer                                         deinstall
obconf                                          deinstall
onboard                                         deinstall
openbox                                         deinstall
osmo                                            deinstall
pitivi                                          deinstall
sylpheed                                        deinstall
tsclient                                        deinstall
tsconf                                          deinstall
xpad                                            deinstall
giorgio@GNetbook1:~$

```

Is this the right behavior? How can i get those packages istantly removed, using the GUI?

(i can use the commandline very well, but am trying to understand how the ubuntu GUI works).

Thankyou so much for your help.

---

