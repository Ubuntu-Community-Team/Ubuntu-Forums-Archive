---
title: "rgb.txt is lost"
date: 2009-09-30
forum: General Help
---

### Post by DarknessEnemy on 2009-09-30
HI everyone.

IM trying to install player/stage so I can "try" to pass the class.

I already installed it. but when I run it, it shows an error:

```
err: unable to open color database /usr/X11R6/lib/X11/rgb.txt : No such file or directory (stage.c stg_lookup_color)
```

IN the manual says it is a common error and can be solved by doing this:

```
ln -s /usr/lib/X11/rgb.txt /usr/X11R6/lib/X11/rgb.txt
```

And didn't worked, so I searched for that rgb.txt in the whole HDD and is not there at all... I don't have idea of what could it be.

I hope you can help me and thank you in advance.

---

### Post by diesch on 2009-09-30
That's a known bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/300935](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/300935)

See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/300935/comments/10](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/300935/comments/10) for how to get a rgb.txt

---

### Post by DarknessEnemy on 2009-09-30
Thank you. I had to create all the directory and the rgb.txt BUT IT WORKED.

Than you so much!

---

### Post by irisorn on 2010-02-03
It woks for me too.

thanks

---

