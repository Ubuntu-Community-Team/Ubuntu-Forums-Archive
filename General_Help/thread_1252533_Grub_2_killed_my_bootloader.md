---
title: "Grub 2 killed my bootloader"
date: 2009-08-28
forum: General Help
---

### Post by Sashin on 2009-08-28
I followed this guide:
-http://gastly.iblogger.org/how-to-install-grub2-on-ubuntu-jaunty/

and after I installed the grub2 chainloader all my boot entires became debian and when I boot I get Error 11.

Anyone know of any ways to remedy this?

This is on my laptop, I'm on my desktop right now.

---

### Post by TeoBigusGeekus on 2009-08-29
[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by gastly on 2009-08-29
Hi Sahin :)

There's a bug filed for your problem [here](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/376879)
It also has a solution for it. If you edit your menu.lst file and replace the

```
root <uuid-of-your-device>
```
with
```
uuid <uuid-of-your-device>
```

Then the problem should get fixed. Many users are experiencing this problem.

btw, that was my guide you followed :-\" lol
So, please let me know if that fixed your problem so I can update the post :)

---

### Post by Sashin on 2009-08-29
None of these work, I've had already tried restoring grub and reinstalling isn't working for some reason.

It says that it can't find /dev/hda and when I use the /find/something/stage1 it says error 15 cannot be found.

---

