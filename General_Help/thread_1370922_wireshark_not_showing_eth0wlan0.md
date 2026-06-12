---
title: "wireshark not showing eth0/wlan0"
date: 2010-01-02
forum: General Help
---

### Post by gfunkera on 2010-01-02
i used wireshark with intrepid and jaunty and found it to be very cool..

when i switched to karmic koala, i was bored one day and opened it up and noticed that the only interfaces it was allowing me to see were my USB connections...

how do i get my wlan0 interface on wireshark v1.2.2??

i have attached a snapshot of what im seeing when i start it...

it seems rather useless without the internet interface available..

---

### Post by DukeKun on 2010-01-07
gfunkera, I just ran into the same problem. This thread gave the answer needed.
[http://ubuntuforums.org/showthread.php?t=1361819&highlight=eth0+Wireshark](http://ubuntuforums.org/showthread.php?t=1361819&highlight=eth0+Wireshark)

use terminal and open with the command sudo wireshark.

---

### Post by bodhi.zazen on 2010-01-07
Indeed you need to run wireshark as root.

IMO you should use gksu with graphical apps 

```
gksu wireshark &
```

You will get a warning box about running as root, you can close that =)

---

### Post by gfunkera on 2010-01-07
I love the linux community!

---

### Post by DukeKun on 2010-01-07
> **bodhi.zazen said:**
> Indeed you need to run wireshark as root.

IMO you should use gksu with graphical apps 

```
gksu wireshark &
```You will get a warning box about running as root, you can close that =)


Even better. Thanks! I added wireshark to my launch panel, right clicked and selected properties, then added _gksu wireshark_ to the command line.

---

