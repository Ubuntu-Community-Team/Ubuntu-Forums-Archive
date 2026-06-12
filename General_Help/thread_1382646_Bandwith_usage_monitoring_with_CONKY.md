---
title: "Bandwith usage monitoring with CONKY"
date: 2010-01-16
forum: General Help
---

### Post by josamoto on 2010-01-16
Hi all!

I'm using CONKY on Ubuntu 9.10, and trying to display network usage statistics for my 3G internet. I want to display something like the following:

```
Today---------------------
UP : xxxMb    DOWN : xxxMb
Past Week:----------------
UP : xxxMb    DOWN : xxxMb
Past Month:---------------
UP : xxxMb    DOWN : xxxMb
```

I have the following script for .conkyrc
```
${voffset 4}${font Liberation Sans:style=Bold:size=8}TELKOM 3G (${addr ppp0}) $stippled_hr${font}
Down: $color${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${downspeedgraph ppp0 25,90 000000 ff0000} ${alignr}${upspeedgraph ppp0 25,90 000000 00ff00}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
```

Any ideas how I might tell Conky to monitor for a period of time?

Thanks in advance!

---

### Post by josamoto on 2010-01-17
Another issue is that conky doesn't want to start up properly with Ubuntu. I've added this to the startup items, and it loads and displays just after the login page, but when the desktop appears it disappears.

---

### Post by josamoto on 2010-01-17
Just for those who are uncertain as to what Conky is:

[http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328")

:)

---

### Post by lemmy999 on 2010-01-17
I'd recommend vnstat for monitoring your 3G modem. Works well on my EEEPC 900 using Crunchbanglinux and a Vodafone 3G dongle.

---

### Post by josamoto on 2010-01-17
Thanks for that! Got vnstat, and a script that I found online that displays exactly what I want.

Now I just need to delay the start of conky, otherwise it disappears when switching from login to desktop screen.

EDIT
Which can be done like this:
sh -c "sleep 60; exec conky"

---

