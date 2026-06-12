---
title: "Xorg mess - help!"
date: 2010-11-03
forum: General Help
---

### Post by ocirne94 on 2010-11-03
Hi all,
I seem to have messed up my xorg, trying to revert to an older nvidia driver (from 260.19.12 to 256.53, to overclock my GPU); opening nvidia settings will show the message
```

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

```
But nvidia-xconfig can't be found as a command!
I have tried to revert my xorg.conf to a previous (backup) version, but with no luck.
Now it seems that OpenGL don't work anymore,
I get ```
 Couldn't find matching GLX visual 
```and ```
Xlib:  extension "GLX" missing on display ":0.0".
freeglut (/opt/torcs/lib/torcs/torcs-bin): OpenGL GLX extension not supported by display ':0.0' 
```
errors now trying to open any game for example.

Any tips?
Thanks,
Ocirne

---

### Post by Zorael on 2010-11-04
Try **purging** the Nvidia driver and then reinstall the version you'd like to use.

How did you install them? Via packages?

---

### Post by ocirne94 on 2010-11-04
How to purge it?

I installed them with official NVidia binaries.

After getting my kubuntu to work only in reduced graphics mode :(, I managed to restore everything by reactivating the offical 260 driver using the "Additional Drivers" program (jockey-kde I think).

Now, everything works, but I'd like to get back to driver 256...

Thanks,
Ocirne

---

### Post by Zorael on 2010-11-04
Hmm. First use the official binary and pass the **--uninstall** argument to it. Then purge the nvidia packages and reinstall them.

```
$ sudo ./NVIDIA-Linux-x86-260.19.12.run **--uninstall**

$ sudo aptitude **purge** nvidia-current
$ sudo aptitude **install** nvidia-current nvidia-settings
```
Then do a full reboot.

---

### Post by ocirne94 on 2010-11-05
Is there a package of driver 256 into the repositories?

---

