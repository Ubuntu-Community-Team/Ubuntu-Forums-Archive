---
title: "X failsafe mode when no monitor attached"
date: 2012-07-29
forum: General Help
---

### Post by PeRy_SoY on 2012-07-29
Hello!

I'm trying to boot the computer with the monitor unplugged, but X started in failsafe mode (terminal) and I can not connect via VNC, (no X up)

any suggestions?

Thanks and sorry for my English


Ubuntu 12.04, gnome-shell 

byE!

dmesg:

[   26.929785] init: lightdm main process (1041) terminated with status 1
[   35.840029] eth0: no IPv6 routers present
[   42.050231] init: failsafe-x main process (1326) terminated with status 1


lightdm.conf:


[SeatDefaults]
autologin-guest=false
autologin-user=pery
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter

---

