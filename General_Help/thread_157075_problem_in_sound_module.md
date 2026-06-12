---
title: "problem in sound module"
date: 2006-04-08
forum: General Help
---

### Post by inhuman!!! on 2006-04-08
Hi,
I've mistakenly disabled and enabled some startup modules by "sysv-rc-conf" and now i have no sound.
module alsa-utils is loaded but module"alsa" is not and there is no device "/dev/esd"

---

### Post by FarEast on 2006-04-08
Hi;) ,

Please paste the output after executing:
$ ls /etc/rcS.d/

---

### Post by inhuman!!! on 2006-04-08
Result for ls /etc/rcS.d/

K60hotplug                          S20module-init-tools  S40networking
K76readahead                        S22hwclockfirst.sh    S45mountnfs.sh
K80alsa                             S26lvm                S48console-screen.sh
K89hotplug-net                      S27evms               S50alsa-utils
README                              S30checkfs.sh         S50hwclock.sh
S02mountvirtfs                      S30procps.sh          S51ntpdate
S04mdadm-raid                       S35mountall.sh        S55bootmisc.sh
S04udev                             S36mountvirtfs        S55urandom
S05bootlogd                         S36udev-mtab          S70screen-cleanup
S05keymap.sh                        S38pppd-dns           S70xorg-common
S07hdparm                           S39dns-clean          S75sudo
S10checkroot.sh                     S39ifupdown           S81hplip
S15linux-restricted-modules-common  S40hostname.sh
S18ifupdown-clean                   S40ifrename

---

### Post by inhuman!!! on 2006-04-08
any suggestions?

---

### Post by FarEast on 2006-04-09
Hi inhuman!!!

Sorry, to have kept you waiting.  Here it is 9 hours ahead of GMT.
So it was midnight yesterday when I posted the message.
(In which time zone do you live?;) )

The contents are as follows on my system:

README                              S26lvm            S40ifrename
S02mountvirtfs                      S27evms           S40networking
S04mdadm-raid                       S30checkfs.sh     S41hotplug-net
S04udev                             S30etc-setserial  S45mountnfs.sh
S05bootlogd                         S30procps.sh      S46setserial
S05initrd-tools.sh                  S35mountall.sh    S48console-screen.sh
S05keymap.sh                        S36mountvirtfs    S50alsa-utils
S07hdparm                           S36udev-mtab      S50hwclock.sh
S10checkroot.sh                     S38pppd-dns       S51ntpdate
S15isapnp                           S39dns-clean      S55bootmisc.sh
S15linux-restricted-modules-common  S39ifupdown       S55urandom
S18ifupdown-clean                   S39readahead      S70screen-cleanup
S20module-init-tools                S40hostname.sh    S70xorg-common
S22hwclockfirst.sh                  S40hotplug        S75sudo

They are symbolic links to scripts in /etc/init.d .
Links that has 'S'('K') at the top of them execute scripts with the argument 'start'('stop').

> K80alsa S26lvm S48console-screen.sh

The link 'K80alsa' does not exist on my system.  It may be the cause.
Please paste the output:
$ ls -l /etc/rcS.d | grep alsa

---

### Post by inhuman!!! on 2006-04-09
Thanks for your attention,

The output are:
lrwxrwxrwx  1 root root  14 2006-04-08 15:44 K80alsa -> ../init.d/alsa
lrwxrwxrwx  1 root root  20 2006-04-08 15:44 S50alsa-utils -> ../init.d/alsa-utils

---

### Post by inhuman!!! on 2006-04-10
when I use "lsmod | grep snd" there would be no return, no sound module is loaded.
What can I do? I desprately need my sound ;-)

---

### Post by FarEast on 2006-04-11
Hello;) ,

Give a try:

```
$ cd /etc/rcS.d
$ sudo rm K60hotplug
$ sudo rm K76readahead
$ sudo rm K80alsa
$ sudo rm K89hotplug-net
$ sudo ln -s ../init.d/readahead S39readahead
$ sudo ln -s ../init.d/hotplug S40hotplug
$ sudo ln -s ../init.d/hotplug-net S41hotplug-net
```

---

