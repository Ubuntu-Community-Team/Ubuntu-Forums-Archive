---
title: "usplash fail message"
date: 2010-04-16
forum: General Help
---

### Post by hihihi100 on 2010-04-16
Hi there:

When I turn on my laptop, a message always appears. It reads:

usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

then the system continues to the desktop, where I can use ubuntu without problems

some questions:

My guess is it has something to do with screen resolution, but Im not sure
How bad is it?
Can it be related to a recent upgrade from EXT3 to EXT4?
Is it related to the graphics card model? drivers?
How can I fix it?

cheers

---

### Post by ajgreeny on 2010-04-16
Have a look at /etc/usplash.conf which should look something like
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=1024
```
only in your case may have the 1152 and 864, which does not work, instead of 1280 and 1024.  If so, edit the file and save it, then run ```
sudo update-initramfs
```

---

### Post by hihihi100 on 2010-04-17
that was close: my data:

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1440
yres=900
```

---

### Post by ajgreeny on 2010-04-17
So try the edit to
```
xres=1280
yres=1024
```
and reboot to test it.

---

