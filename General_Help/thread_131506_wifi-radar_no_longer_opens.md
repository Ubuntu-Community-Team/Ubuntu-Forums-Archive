---
title: "wifi-radar no longer opens"
date: 2006-02-16
forum: General Help
---

### Post by dusty on 2006-02-16
whe i try to open wifi radar is asks for a password and than just never opens.

it just started doing thing that last few days.

what should i do?

---

### Post by LordBug on 2006-02-16
Run it from a console, post any error messages you get.  It'll help figure out what went wrong.

---

### Post by dusty on 2006-02-16
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1273, in ?
    auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'

---

### Post by guayusa on 2006-04-21
[QUOTE=dusty]Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1273, in ?
    auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'[/QUOTE]

i get more or less the same, also seemingly out of the blue, using Dapper with latest apt-get dist-upgrade:

Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1377, in ?
    auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'

any ideas?

---

### Post by guayusa on 2006-04-21
well, i solved the brute way:

open synaptic, search for wifi-radar, then right-click and choose "Mark for Complete Removal" - click Apply, then wait, then right-click it again and install.

And it works.

---

### Post by kaosreset on 2006-09-18
I ran into the same issue -
here's how I solved it:

changed /usr/sbin/wifi-radar to init auto_profile_order as a string.

diff /usr/sbin/wifi-radar /usr/sbin/wifi-radar.original
1338c1338
< auto_profile_order    = ""
---
> auto_profile_order    = []

call of split() is available for a string not a list. 

- checked wifi-radar svn and this piece exists all along from version 1, so not sure if this is the complete fix.

- tested it by resetting my /etc/wifi-radar/wifi-radar.conf to default.

anyway, perhaps this might help someone running into this.

---

### Post by brianfinley on 2006-10-10
Please include the version number in your posts.  You can do this with:

```
dpkg -l wifi-radar
```

Thanks!

---

### Post by mlaccs on 2007-05-11
No probllems for several months.  CentOS 4.4 and now 5.

Yesterday get the followng:

Traceback (most recent call last):
File "/usr/sbin/wifi-radar", line 1273, in ?
auto_profile_order = auto_profile_order.split( ',' )
AttributeError: 'list' object has no attribute 'split'

Renamed   /etc/wifi-radar/wifi-radar.conf to  wifi-radar.bad

Restarted and it created the config file again and all seems to be OK.

Mark

---

### Post by fragos on 2007-05-11
If gnome network manager and wifi-radar are both installed they interfeer with each other.  In Ubuntu 7.04 gnome network manager is part of the default install.

---

