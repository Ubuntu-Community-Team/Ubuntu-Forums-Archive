---
title: "LightDM not loading"
date: 2012-01-26
forum: General Help
---

### Post by lolpenguin on 2012-01-26
On startup LightDM doesn't seem to show up.```
jamesye@ubuntu:~$ cat /var/log/boot.log
udevd[400]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:10

udevd[400]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:12

rpcbind: Cannot open '/run/rpcbind/rpcbind.xdr' file for reading, errno 2 (No such file or directory)
rpcbind: Cannot open '/run/rpcbind/portmap.xdr' file for reading, errno 2 (No such file or directory)
fsck from util-linux 2.19.1
/dev/loop0: clean, 387181/1073152 files, 3362650/4286464 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                                            [ OK ]
 * Stopping Failsafe Boot Delay                                                          [ OK ]
 * Stopping System V initialisation compatibility                                        [ OK ]
 * Starting System V runlevel compatibility                                              [ OK ]
 * Stopping automatic crash report generation                                            [fail]                                                                                     
 * Starting restore sound card(s') mixer state(s)                                        [ OK ]
 * Starting LightDM Display Manager                                                      [ OK ]
 * Starting ACPI daemon                                                                  [ OK ]
 * Starting anac(h)ronistic cron                                                         [ OK ]
 * Starting save kernel messages                                                         [ OK ]
 * Starting CPU interrupts balancing daemon                                              [ OK ]
 * Stopping restore sound card(s') mixer state(s)                                        [ OK ]
 * Starting regular background program processing daemon                                 [ OK ]
 * Starting deferred execution scheduler                                                 [ OK ]
```
And it just stays here. I can manually run LightDM by first switching to a tty then "sudo lgihtdm"
UPDATE: seems to be fine after a kernel update

---

### Post by lolpenguin on 2012-01-26
And it's happening again. Oh, and it seems to not happen if I run apt-get...

---

### Post by lolpenguin on 2012-01-27
Bump. It's getting really annoying.

---

