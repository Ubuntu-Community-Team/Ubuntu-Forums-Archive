---
title: "network being used with no processes running"
date: 2011-05-17
forum: General Help
---

### Post by ironchefchopchop on 2011-05-17
[IMG]http://a8.sphotos.ak.fbcdn.net/hphotos-ak-ash4/226260_10150180685818445_584178444_7157532_7455453_n.jpg[/IMG]

[IMG]http://a6.sphotos.ak.fbcdn.net/hphotos-ak-ash4/228335_10150180685803445_584178444_7157531_2289030_n.jpg[/IMG]

```
lsof -i
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
gweather- 1751 gianni   20w  IPv4  37184      0t0  TCP frankie-two-time:44549->24.143.206.58:www (CLOSE_WAIT)
gweather- 1751 gianni   25r  IPv4  37186      0t0  TCP frankie-two-time:44550->24.143.206.58:www (CLOSE_WAIT)

```

it only starts going when absolutely nothing else is being used

once i type a command or open a program it stops

how can i stop my bandwidth from being used when im not doing anything?

---

