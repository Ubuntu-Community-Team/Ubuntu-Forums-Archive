---
title: "Battery icon dont change when unplugged"
date: 2009-10-31
forum: General Help
---

### Post by pjalegria on 2009-10-31
Hi

When i unplugged the battery icon don change, only if restart, um using Karmic UNR, can someone help me please?

Thanks

---

### Post by pjalegria on 2009-11-01
Bump... only i have that problem???

---

### Post by san_terre on 2009-11-01
Same here.  Sony SZ640 with upgrade to 9.10 from 9.04.

When my battery is fully charged, the icon stays this way whether or not AC power is applied or not.

---

### Post by pjalegria on 2009-11-01
Someone have report that bug???

---

### Post by pjalegria on 2009-11-01
Bug reported

[https://bugs.launchpad.net/ubuntu/+bug/469149](https://bugs.launchpad.net/ubuntu/+bug/469149)

---

### Post by TheNessus on 2009-11-01
Same for me but using the normal karmic version, not the remix. Can you add that to the bug report please?

---

### Post by pjalegria on 2009-11-01
Bug reported, can you click "this bug affect me too"

---

### Post by pjalegria on 2009-11-15
No fix yet...

---

### Post by pjalegria on 2009-11-15
bump...

---

### Post by pjalegria on 2009-11-19
I found a fix :D

> Power manager status icon in the Notification Applet does not switch from AC power to Battery when unplugged, although the screen dims. Since it still shows as AC power, it does not show an estimate of battery time left. If it is unplugged at login, it will switch to AC power status when plugged in, but not back if unplugged again. A work around for this is to add the add the following line in /etc/rc.local before the exit 0 line:

#Power manager status icon fix
/etc/init.d/laptop-mode start service laptop-mode status



---

