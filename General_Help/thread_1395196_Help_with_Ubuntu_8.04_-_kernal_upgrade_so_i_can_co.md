---
title: "Help with Ubuntu 8.04 - kernal upgrade so i can connect"
date: 2010-01-31
forum: General Help
---

### Post by Monotoko on 2010-01-31
Hiya, could do with some help here...

My laptop is a little bit picky, after trying Ubuntu 8.10, 9.04 and 9.10, OpenSUSE, PCLinuxOS, Debian Lenny, etc etc etc and finding they all have there own problems with software and drivers.

I finally managed to get Debian Lenny working, but soon realized it was very bare, and wanted to get Ubuntu.

8.10, 9.04 and 9.10 all have major issues with speed on my laptop, crashing out and dying every hour or so, yet 8.04 never did, nor has any other linux distrobution (but they all had there own issues), so heres what i planned.

Now, when booting into 8.04, my graphics are on simple mode and my wifi isnt recognised, for Ubuntu to recognise both of these i need the 2.6.32 kernal.

I went and found a deb version of the kernal and attempted to install it, however now im stuck with this: "Error, dependancy is not satisfiable: wireless-crda"

---

### Post by Barriehie on 2010-01-31
Have you tried:
```

sudo apt-get -f wireless-crda

```
See the manpage for apt-get but this should fix broken dependencies.

Barrie

---

