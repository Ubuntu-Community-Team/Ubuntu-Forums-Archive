---
title: "skype crashes after upgrade from 9.04 to 9.10 latest alpha"
date: 2009-08-22
forum: General Help
---

### Post by TDK800 on 2009-08-22
skype starts ok, but after it logs in, just disappears, terminal gives error:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Edit:
when i run skype as root from terminal:
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

---

### Post by srge on 2009-08-22
> **TDK800 said:**
> skype starts ok, but after it logs in, just disappears, terminal gives error:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Edit:
when i run skype as root from terminal:
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

I was getting this error from a fresh 9.10 alpha4 install so I just installed the skype-static-oss version and it worked fine.   Go figure.  Make sure you have that alsa-oss compat package though.

---

### Post by TDK800 on 2009-08-22
fixed it, thanks srge!

here's the how-to for anyone else having this problem (skype-static-oss is only available in medibuntu repository):

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring

sudo apt-get update

sudo apt-get install skype-static-oss

---

