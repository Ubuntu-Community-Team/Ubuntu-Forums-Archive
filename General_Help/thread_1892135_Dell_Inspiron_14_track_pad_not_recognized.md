---
title: "Dell Inspiron 14 track pad not recognized"
date: 2011-12-07
forum: General Help
---

### Post by jamesisin on 2011-12-07
I am trying to sort out a mouse/track pad problem with my Dell Inspiron 14 or N4030.  If I look under the Mouse system preferences there is no Touchpad tab.  As such I am not able to make adjustments to improve its performance (it tends to dart around while typing), and I suspect this is precisely because Ubuntu is treating it as though it were a mouse.

(The utility gpointing-device-settings has the same problem.)

Next steps?

---

### Post by jamesisin on 2011-12-07
Anybody?

---

### Post by aeronutt on 2011-12-07
Check this out:
[http://ubuntuforums.org/showthread.php?p=11497066#post11497066](http://ubuntuforums.org/showthread.php?p=11497066#post11497066)

Which points to this driver for ALPS

[http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

Which seems to work for a lot of Dell laptops.

Read somewhere that this won't get fixed in the kernel until 3.3 or so, but maybe in Ubuntu 12.04.

---

### Post by jamesisin on 2011-12-08
It did look a bit promising when I read through that post; however, I tried to install the linked deb package on this 10.04 machine to no avail.  There were errors but more importantly nothing seems to have changed after a reboot.  Perhaps there needs to be a different package for 10.04?

Running this machine using an 11.04 live CD gives slightly better functionality (the edge scrolling works), but still there is no Touchpad tab in Mouse.  Installing that deb also seems to change nothing in 11.04.

Next?

---

### Post by jamesisin on 2011-12-12
Anybody?

---

### Post by jamesisin on 2011-12-14
Hello?

---

### Post by jamesisin on 2011-12-15
Please?

---

### Post by jamesisin on 2012-01-03
Can someone please help with this?  This is a great lappy except that the touchpad isn't a touchpad right now.  Can I just lie to the system so that it loads a different driver?  Anything?

---

### Post by jamesisin on 2012-01-08
Anybody?

---

### Post by jamesisin on 2012-02-28
This must be something which requires a clever hacker...

---

### Post by jamesisin on 2012-02-29
I tested 11.10 and found that vertical scrolling does work even though the pad is still detected as a mouse (in Mouse and Trackpad there are only mouse options/tab).

---

### Post by jamesisin on 2012-03-09
Is there a way for me to force 10.04 to do whatever 11.10 is doing which improves the trackpad usage?

---

### Post by jamesisin on 2012-03-26
Shockingly this is still broken.  Any ideas?

---

### Post by jamesisin on 2012-03-31
I did find this output from a Win7 user with this same laptop:

```
+ Dell Touchpad
| Matching Device ID: *dll0466
| Upper Filters: ApfiltrService
| Service: i8042prt
```

( [http://en.community.dell.com/support-forums/laptop/f/3518/t/19432783.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/t/19432783.aspx) )

Is this useful in understanding the Ubuntu problem?

---

