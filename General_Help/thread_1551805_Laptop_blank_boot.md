---
title: "Laptop blank boot"
date: 2010-08-12
forum: General Help
---

### Post by xalelexx on 2010-08-12
Hi there, yesterday I updated my laptop (old Toshiba Satellite Pro 4200) to 10.04. it was 99% done, so I unplugged it and left it in my locked draw to finish. Now when I turn it on this morning, it's just blank. Holding the shift key while booting does nothing.

Any ideas on what I should do to get my laptop up and running again?

---

### Post by [Shawn] on 2010-08-12
It might not support your graphics card.
Or your laptop died when you unplugged it and it wasn't finished.
If that's the case if it's a blank boot. My best suggestion is that you Burn/request a ubuntu 9.10 CD
from another computer.

---

### Post by xalelexx on 2010-08-12
So basically I'm ****ed either way

---

### Post by [Shawn] on 2010-08-12
I wouldn't say that i'm pretty sure there's solutions out there.
If you still have the live CD that you used to install ubuntu 9.10
or any other ubuntu version then you can reinstall it and overwrite ubuntu 10.04.

---

### Post by [Shawn] on 2010-08-12
Here is a bug that corresponds to your issue:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/578028](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/578028)

---

### Post by wilee-nilee on 2010-08-12
Boot the live disc and look in gparted to see if you have a system built.

Chances are you unplugged it and a prompt came up and it waited till the battery went down and never finished. If you could get to a command line you might be able to run
```
sudo apt-get install -f
```
and it might finish, otherwise reinstall.

You say your were updating was it upgrading? Or was this a fresh install.

---

