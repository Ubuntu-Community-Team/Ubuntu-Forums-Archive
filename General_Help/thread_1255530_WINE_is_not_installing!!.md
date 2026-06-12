---
title: "WINE is not installing!!"
date: 2009-09-01
forum: General Help
---

### Post by antdgar on 2009-09-01
I just got my high-end server today and I have had to install Ubuntu 5 times. I've only had the server for 3 hours.....

WINE just will not install.

1. The latest version of WINE has a bug so I can't install it - therefore I cannot use SYNAPTIC
2. I tried installing by using dpkg on the downloaded .deb file
This is a fresh install, all I have done is run updates.

I get this error when installing an older (but known to actually work) version of WINE:
```

Selecting previously deselected package wine.
(Reading database ... 39858 files and directories currently installed.)
Unpacking wine (from wine_1.1.25~winehq0~ubuntu~9.04-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on binfmt-support (>= 1.1.2); however:
  Package binfmt-support is not installed.
 wine depends on libaudio2; however:
  Package libaudio2 is not installed.
 wine depends on libaudiofile0 (>= 0.2.3-4); however:
  Package libaudiofile0 is not installed.
 wine depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35); however:
  Package libesd-alsa0 is not installed.
  Package libesd0 is not installed.
 wine depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not installed.
 wine depends on libgphoto2-port0 (>= 2.4.0); however:
  Package libgphoto2-port0 is not installed.
 wine depends on liblcms1 (>= 1.15-1); however:
  Package liblcms1 is not installed.


```I am using Ubuntu Server 9.04

And no, I can't install those dependencies either. I just get roughly the same message as above^

---

### Post by oldos2er on 2009-09-01
You'll need to use aptitude or apt-get to install the dependencies; once that's done the dpkg command should work.

---

### Post by antdgar on 2009-09-01
> **oldos2er said:**
> You'll need to use aptitude or apt-get to install the dependencies; once that's done the dpkg command should work.
apt-get on the dependencies just yields more and more dependencies messages like the above. It's an endless chain of nonsense.

---

### Post by denver on 2009-09-01
After the initial:

```
 dpkg -i <package>.deb
```

that yealded those dependency errors, try running:

```
apt-get -f install
```

That command will try to install all the missing dependencies for the package you initially tried to install but failed.

If dependencies cannot be satisfied, the package will be removed.

Good luck!

---

### Post by antdgar on 2009-09-01
> **denver said:**
> After the initial:

```
 dpkg -i <package>.deb
```that yealded those dependency errors, try running:

```
apt-get -f install
```That command will try to install all the missing dependencies for the package you initially tried to install but failed.

If dependencies cannot be satisfied, the package will be removed.

Good luck!
You deserve a medal

It worked. Thanks

---

### Post by denver on 2009-09-01
You're welcome :)

---

