---
title: "No GUI when using Unity!"
date: 2011-09-06
forum: General Help
---

### Post by palz2015 on 2011-09-06
I just formatted and installed Ubuntu on my laptop because when I upgraded from 10.10 my keyboard and mouse stopped working. Anyway, when I log in and keep the environment on "Ubuntu", I just see my wallpaper, and the WiFi notification and other windows flickering. I'm typing this from "Ubuntu Classic". Yes, I have the driver for my graphics card. I've tried "unity --reset" from the terminal login (the desktop environment, not recovery mode). What's going on?

It's a Toshiba Tecra M2.

This is what I get when I try "unity --reset" from Ubuntu Classic:
> root@palz2015-laptop:/home/palz2015# unity --reset
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'


---

### Post by garvinrick4 on 2011-09-06
Here is a line of code to see if 3d capable:
```
/usr/lib/nux/unity_support_test -p 
```

---

### Post by garvinrick4 on 2011-09-06
If 3D capable install ccsm as in screenshot and make sure Ubuntu Unity plugin is checked in lower right of ccsm.. 
Must sign off for a while, enjoy.

---

