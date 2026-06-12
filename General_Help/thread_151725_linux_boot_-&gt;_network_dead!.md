---
title: "linux boot -&gt; network dead!"
date: 2006-03-28
forum: General Help
---

### Post by Huubke! on 2006-03-28
Hi, I have the quite annoying problem that everytime I boot into linux (warty, hoary, dapper  all have the same problem) the router (Edimax wl 6004 i believe) gets a knock on the head and the internet connection dies...
The LAN still works and I can access the web interface of the router. The only solution then is to release its WAN ip adress and renew it again. But that's just far too annoying of course.
I must add that it boots into windows (yuck) without any problems and has also worked without any problems after a certain system upgrade some time ago, but stopped working again after the next...

Any ideas? Please?

---

### Post by metzen_w on 2006-03-28
$  #sudo gedit /etc/modprobe.d/bad_list

Add this line
alias net-pf-10 off

Save and Restart

Reason for this is the system looks to IPV6 before IPV4 on the router; Hence the eternal Fire fox circle.  Some routers support this and most right now don't
-Jason

---

### Post by Asger on 2007-10-29
I seem to have a similar problem, sometimes the I can't get an IP adress automatically. However I don't have the file /etc/modprobe.d/bad_list but only these files in the directory:

```
aliases       blacklist-framebuffer  bluez              lrm-video
alsa-base     blacklist-modem        ibm_acpi.modprobe  nvidia-kernel-nkc
arch          blacklist-oss          ipw3945            options
arch-aliases  blacklist-scanner      isapnp             toshiba_acpi.modprobe
blacklist     blacklist-watchdog     libpisock9
```

---

