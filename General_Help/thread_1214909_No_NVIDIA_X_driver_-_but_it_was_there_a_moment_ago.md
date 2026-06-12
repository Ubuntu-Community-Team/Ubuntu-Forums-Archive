---
title: "No NVIDIA X driver - but it was there a moment ago...?"
date: 2009-07-16
forum: General Help
---

### Post by kneewax on 2009-07-16
Hey folks,

I just rebooted after a regular update and I get X graphic driver errors, I finally got the desktop loaded and went looking to see if there is something screwy with my on-board NVIDIA drivers that have been so faith until now.

When I try to check the NVIDIA settings I get this error message:

```

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

```

So I did what it suggested and got this output from the terminal:

```

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


```

Any ideas, I am running in a low graphics mode, and it ain't nice :(

Thanks

---

