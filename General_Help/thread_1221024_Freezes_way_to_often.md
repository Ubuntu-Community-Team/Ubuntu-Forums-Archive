---
title: "Freezes way to often"
date: 2009-07-23
forum: General Help
---

### Post by hugstari on 2009-07-23
Hello

I having a little trouble with my laptop. I locks up way to often and the only thing i can do is a complete shutdown and reset. I don't have any more info other then this seems to happen frequently while i watch videos using both movie player and vlc, but it also occurs less frequently during the startup process. 

Are there any log files that i could check that would give me (and you) any more information on why this is happening?

I fit matters then here is some system information.
Ubuntu Info:
Ubuntu: 9.04
Kernel: 2.6.28-13
Gnome: 2.26.1

Sys info:
Intel "Pentium" T2060
Mem: 874.8 Mib
Free Space 38.8

---

### Post by Johnny B on 2009-07-23
dmesg | tail -25

---

### Post by hugstari on 2009-07-23
Should i do this straight after the system locks up or is this of any use? Should i try doing the command again later perhaps?

```
[ 9398.342102] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9439.343216] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9700.342100] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9762.342100] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9863.342013] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9894.342118] ath5k phy0: noise floor calibration timeout (2437MHz)
[ 9915.342141] ath5k phy0: noise floor calibration timeout (2437MHz)
[10218.342013] ath5k phy0: noise floor calibration timeout (2437MHz)
[10422.328010] ath5k phy0: noise floor calibration timeout (2437MHz)
[10562.841896] ath5k phy0: unsupported jumbo
[10625.342102] ath5k phy0: noise floor calibration timeout (2437MHz)
[10736.342015] ath5k phy0: noise floor calibration timeout (2437MHz)
[10858.342102] ath5k phy0: noise floor calibration timeout (2437MHz)
[10969.342013] ath5k phy0: noise floor calibration timeout (2437MHz)
[11070.342013] ath5k phy0: noise floor calibration timeout (2437MHz)
[11191.342013] ath5k phy0: noise floor calibration timeout (2437MHz)
[11321.594610] atkbd.c: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
[11321.594616] atkbd.c: Use 'setkeycodes 55 <keycode>' to make it known.
[11324.644819] atkbd.c: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[11324.644830] atkbd.c: Use 'setkeycodes 55 <keycode>' to make it known.
[11324.942722] atkbd.c: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
[11324.942732] atkbd.c: Use 'setkeycodes 55 <keycode>' to make it known.
[11326.284741] atkbd.c: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[11326.284751] atkbd.c: Use 'setkeycodes 55 <keycode>' to make it known.
[11481.439014] ath5k phy0: unsupported jumbo

```

---

### Post by hugstari on 2009-07-24
It happened again tonight. Could it be over heating that is the problem? I tried looking though some logs in var/log but couldn't find anything relevant. Maybe i am not sure what i should be looking for

---

### Post by edantes on 2009-08-07
Had the same problem since installing Jaunty.  I stopped using the ath5k driver for my wifi.

[http://ubuntuforums.org/showthread.php?t=1233309&highlight=ath5k](http://ubuntuforums.org/showthread.php?t=1233309&highlight=ath5k)

---

