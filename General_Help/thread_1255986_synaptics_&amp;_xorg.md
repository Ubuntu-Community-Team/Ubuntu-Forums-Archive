---
title: "synaptics &amp; xorg"
date: 2009-09-02
forum: General Help
---

### Post by joseche on 2009-09-02
I am using 9.04 in a macbook 4,1 but the touchpad is crazy.

My /etc/X11/xorg.conf has this:

```
Section "Module"
	Load "synaptics"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  Option "SHMConfig" "on"
EndSection


```


My /var/log/Xorg.0.log shows these:

```
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0

```

but it just doesn't work:

```
laptop:~$ synclient  -l
Can't access shared memory area. SHMConfig disabled?

```

Any ideas of why it is not working ?

---

### Post by P4man on 2009-09-02
Maybe this helps?

[http://www.linuxquestions.org/questions/slackware-14/cant-access-shared-memory-area.-shmconfig-disabled-692073/](http://www.linuxquestions.org/questions/slackware-14/cant-access-shared-memory-area.-shmconfig-disabled-692073/)

You'll need a serverlayout section to add the "sendcoreevents"

---

