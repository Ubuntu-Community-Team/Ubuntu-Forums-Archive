---
title: "Removing packages installed without checkinstall from source"
date: 2009-10-24
forum: General Help
---

### Post by cross157 on 2009-10-24
Please help, I didn't use checkinstall (stupidly) and now I can't get rid of a couple of packages, for example

```
$ xfburn -V
xfburn version 0.4.2 for Xfce 4.6.1
	built with GTK+-2.18.3, linked with GTK+-2.18.3.
	GStreamer support (built with 0.10.25, linked against 0.10.25)

```

```
$ sudo dpkg --force-all --purge xfburn
dpkg: warning: ignoring request to remove xfburn which isn't installed.

```
```

$ sudo apt-get remove --purge xfburn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xfburn is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by OpenGuard on 2009-10-24
```
sudo make uninstall

```

Execute it in the directory where all your source files are - success depends on whether the developer have added this feature or not.

---

### Post by cross157 on 2009-10-24
> **OpenGuard said:**
> ```
sudo make uninstall

```

Execute it in the directory where all your source files are - success depends on whether the developer have added this feature or not.


Thank you, that got rid of xfburn but I have another package that did not have this feature. Any other suggestions?

---

