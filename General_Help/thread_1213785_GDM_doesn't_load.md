---
title: "GDM doesn't load"
date: 2009-07-15
forum: General Help
---

### Post by Sergey M. on 2009-07-15
Hi. I have a problem with Ubuntu 9.04. Yesterday i tried to reboot it (I had done it before and all was fine). After the splash screen and the progrees bar it showed nothing. Just black screen. I can boot in recovery mode and use console. I tried startx, dpkg, fsck - nothing helped. Now I'm using LiveCD Ubuntu 8.10. There is a line in syslog:
```
gdm[3276]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
```Maybe it tells you something.

I need help!

(sorry for my english)

---

### Post by Sergey M. on 2009-07-15
Please, help me! I don't want to reinstall the system.

---

### Post by cariboo on 2009-07-15
It seems you have problems with your graphics driver, gdm is loading, but you just can't see it.

To repair the problem you can try starting in recovery mode and running xfix. If that doesn't help, I would suggest you remove /etc/X11/xorg.conf and then at the prompt type: exit, then select resume and you will continue on to your desk top. To remove /etc/X11/xorg.conf move it to a backup file at the prompt type:

```
mv /etc/X11/xorg.conf /etc/X11/xorg,conf.bak
```

Once you are back at your desktop you can reinstall the restricted drivers by going to System-->Administration-->Hardware drivers.

---

### Post by Sergey M. on 2009-07-15
Thanks for your answer, but result is the same. I removed xorg.conf and got black screen again (it blinks several times and that's all).

---

### Post by Sergey M. on 2009-07-17
last try.

---

