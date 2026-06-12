---
title: "command-not-found"
date: 2011-10-22
forum: General Help
---

### Post by OnyxDragun on 2011-10-22
I get the following error when I type a non-existant command.

```

$ jh
/usr/bin/python: '/usr/share/command-not-found' is a directory, cannot continue

```

When I try and do apt-get upgrade
I get 
```

You might want to run 'apt-get -f install' to correct these
The following packages have unmet dependencies:
 console-setup: Depends: keyboard-configuration but it is not installed
      Depends: kbd (>= 1.15-1ubuntu3)
 ubuntu-minimal: Depends: isc-dhcp-client but it is not installed
      Depends: kbd
      Depends: netcat-openbsd but it is not installed
      Depends: rsyslog but it is not installed
      Depends: ureadahead but it is not installed
E: Unmet dependencies Try using -f.
[code]

So when I do apt-get -f install I get that there are updates to the above but I get back this:
[code]
dpkg: error processing /var/cache/apt/archives/keyboard-configuration_1.57ubuntu20_all.deb (--unpack):
 trying to overwrite '/etc/init.d/console-setup', which is also in package console-setup 1.57ubuntu20
Errors were encountered while processing:
 /var/cache/apt/archives/keyboard-configuration_1.57ubuntu20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I seem to not be able to get any of the packages installed properly. Anyone know what I can try?

I'm running Natty

---

### Post by matt_symes on 2011-10-22
Hi

For your second error

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/keyboard-configuration_1.57ubuntu20_all.deb
```Then try
```
sudo apt-get -f install
```For your first error let's check your aliases. Post the output of

```
alias
```Kind regards

---

### Post by OnyxDragun on 2011-10-22
For some reason my computer rebooted and now I get the following

```
Starting up...
mount: mounting none on /dev failed: No such device
W: devtmpfs not available, falling back to tmpfs for /dev
udevd[897]: error getting socket: Invalid argument

error initializing netlink socket
udevd[897]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid Argument
Segmentation fault

Gave up waiting for root device

ALERT! /dev/disk/blah_blah_blah does not exist
Dropping to a shell!

Busy Box v1.17.1 (Ubuntu 1:1.17.1-10ubunutu1) built-in shell (ash)

(intiramsfs)
```


And for some odd reason, my USB keyboard isn't working. (works when I go into the bios though)

---

### Post by matt_symes on 2011-10-22
Hi

Blimey! When did your PC reboot ? Did you have a powercut ?

If you have a LiveCD/USB available then boot into that.

Check the SMART status of the hard drive first (use disc utility) and then run fsck on your main partition.

 Run a test first to see if it sees anything wrong (-N switch). If it does then run a full fsck to repair.

Kind regards

---

