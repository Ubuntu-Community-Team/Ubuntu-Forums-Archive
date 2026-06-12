---
title: "confused brightness in Ubuntu 12.04"
date: 2012-05-02
forum: General Help
---

### Post by parminides on 2012-05-02
I did a fresh install of Ubuntu 12.04 on my HP TouchSmart, and I'm having a strange brightness problem. When I reboot the brightness resets to the dimest level. This problem appears in the forums, but it seems to afflict laptops. The TouchSmart is a desktop.

If I run the Brightness and Lock application, the horizontal slider that sets the level is backwards: brightness increases as I move it to the left! (I haven't found any mention this weird slider behavior.)

I could accept the backward slider as one of the many lovable quirks of Linux, but having to manually reset my brightness after every bootup is really annoying.

Following [http://ubuntuforums.org/showthread.php?t=1882469](http://ubuntuforums.org/showthread.php?t=1882469), message 9, I did the following test when the screen was set to its brightest:

```

$ cat /sys/class/backlight/intel_backlight/brightness 
0
$ cat /sys/class/backlight/intel_backlight/max_brightness 
12750000
$ cat /sys/class/backlight/intel_backlight/actual_brightness 
0

```

This is very strange that the actual brightness is 0 when the screen is at its brightest, but it's sort of consistent with the backwards slider. The computer is somehow confused about max and min brightness.

After bootup dimming, I can increase to maximum brightness with the following command:

```

$ echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness

```

I'd like a more elegant fix, but I'd settle for a place to put the above command such that it will automatically run at startup without requiring a password.

---

### Post by parminides on 2012-05-04
I found the inelegant solution. Add

```

echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness

```

to the end of /etc/init.d/rc.local.

---

### Post by cmcanulty on 2012-05-05
does the 0 set it to highest or lowest? I want highest. This was fixed in 11.10 with a kernel patch and now it is back and very annoying.

---

### Post by parminides on 2012-05-05
Yes, 0 sets it to the highest brightness. Very strange and annoying.

---

