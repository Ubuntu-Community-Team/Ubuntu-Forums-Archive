---
title: "Installing Wireless Compatibility modules on Natty"
date: 2011-05-18
forum: General Help
---

### Post by Martin_sensei on 2011-05-18
Hello,

I am not sure what I am doing so I was wondering if I could ask for some help.

Basically I am having some wireless issues in Natty, that have started since the upgrade from Maverick.

Anyway, I was thinking of installing the wireless compatibility modules from linuxwireless.org ([http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases]("http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases"))

My question is simply, is this an apropriate thing to do on Natty.  The kernel is currently 2.6.38.8, so I think this is the right version.

Will this do any damage, will I be able to revert?

Has anyone done this before?

---

### Post by CoolJohnB on 2011-05-18
Is it a laptop?  If so a few of us have had Wifi issues and this thread solved them: [http://ubuntuforums.org/showthread.php?t=1756470&page=2](http://ubuntuforums.org/showthread.php?t=1756470&page=2)

Using this suggestion: Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Hope it works for you

---

### Post by jawilljr on 2011-05-18
[compat-wireless-2.6.39-rc6-1-sp](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc6-1-sp.tar.bz2) will also work in Natty. In fact that is the one I am using to get my Ralink USB dongle to work in Natty.

Jerry

---

### Post by Martin_sensei on 2011-05-18
Aren't those for kernel 2.6.39?  Do these have to match the kernel version number?

---

### Post by Martin_sensei on 2011-05-18
> **CoolJohnB said:**
> Is it a laptop?  If so a few of us have had Wifi issues and this thread solved them: [http://ubuntuforums.org/showthread.php?t=1756470&page=2](http://ubuntuforums.org/showthread.php?t=1756470&page=2)

Using this suggestion: Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Hope it works for you

Hi, Yes it is a laptop, with a ath9k wireless card.

Wireless is working, just not for my Android hotspot.

---

### Post by Martin_sensei on 2011-05-18
> **jawilljr said:**
> [compat-wireless-2.6.39-rc6-1-sp](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-rc6-1-sp.tar.bz2) will also work in Natty. In fact that is the one I am using to get my Ralink USB dongle to work in Natty.

Jerry

I tried that one and got:

```
mememe@mylaptop:~/Downloads/compat-wireless-2.6.39-rc6-1$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.38-8-generic/build M=/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/built-in.o
  CC [M]  /home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/main.o
  CC [M]  /home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/compat-2.6.39.o
/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/compat-2.6.39.c: In function ‘tty_set_termios’:
/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/compat-2.6.39.c:93:4: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/compat-2.6.39.c:93:4: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat/compat-2.6.39.o] Error 1
make[2]: *** [/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1/compat] Error 2
make[1]: *** [_module_/home/mememe/Downloads/compat-wireless-2.6.39-rc6-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2

```

Did you have to do anything before making?

---

### Post by Martin_sensei on 2011-05-19
Hello again,

I can't really find any info on my problem, my guess is, my kernel doesn't match the version of these drivers I am trying to build.  Can anyone confirm that?

---

