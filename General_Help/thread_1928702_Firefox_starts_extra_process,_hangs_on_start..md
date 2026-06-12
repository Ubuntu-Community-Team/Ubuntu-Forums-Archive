---
title: "Firefox starts extra process, hangs on start."
date: 2012-02-20
forum: General Help
---

### Post by LiSrt on 2012-02-20
For the last couple of days, Firefox isn't starting properly, the window appears, but it is just grey - no buttons, no start page, no menu, no scrollbars.

Running ps -A shows two firefox processes, killing the higher numbered one lets Firefox start "normally".

I do not know why two processes should start, I am sure I am not double clicking the menu button for Firefox. :confused:

Any ideas for how to fix this?

I'm using xubuntu 11.10, Firefox version 10.0.2

---

### Post by lovinglinux on 2012-02-20
Try starting Firefox in safe mode and with a clean profile, then report back.


Safe Mode

```
firefox -safe-mode
```


Profile manager

```
firefox -P
```

---

### Post by LiSrt on 2012-02-21
> **lovinglinux said:**
> Try starting Firefox in safe mode and with a clean profile, then report back.


Safe Mode

```
firefox -safe-mode
```Profile manager

```
firefox -P
```

I already tried safe mode, with the same result.

I then tried deleting the ~/.mozilla folder and starting firefox again (with the same result). Would this have had the same effect as firefox -P?

Also, I found another example of this issue: [http://ubuntuforums.org/showthread.php?t=1888175](http://ubuntuforums.org/showthread.php?t=1888175)

---

### Post by LiSrt on 2012-02-24
bug report:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/939712](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/939712)

---

### Post by lovinglinux on 2012-02-24
> **LiSrt said:**
> I already tried safe mode, with the same result.

I then tried deleting the ~/.mozilla folder and starting firefox again (with the same result). Would this have had the same effect as firefox -P?

Also, I found another example of this issue: [http://ubuntuforums.org/showthread.php?t=1888175](http://ubuntuforums.org/showthread.php?t=1888175)

In this case, it could be a corrupt firefox installation.

Try to reinstall Firefox:

```
sudo apt-get install --reinstall firefox
```

---

### Post by LiSrt on 2012-02-26
> **lovinglinux said:**
> In this case, it could be a corrupt firefox installation.

Try to reinstall Firefox:

```
sudo apt-get install --reinstall firefox
```

I tried that as well, unfortunately it didn't work.

I'll try reinstalling the graphics drivers, or changing them, next.

---

