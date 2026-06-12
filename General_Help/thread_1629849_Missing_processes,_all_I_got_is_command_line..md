---
title: "Missing processes, all I got is command line."
date: 2010-11-24
forum: General Help
---

### Post by InTheMarket on 2010-11-24
UPDATE: I reinstalled all the processes I could with liveCD+chroot. And their errors went away. I still have this (exactly) appearing on a command-line after the GRUB menu.

```

fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 213665/4104192 files, 2426106/16389120 blocks
init: screen-cleanup main process (726) terminated with status 1
Starting NBD client process: Connecting...nbd-client version 2.9.14
Usage: nbd-client [bs=blocksize] [timeout=sec] host port nbd_device [-swap] [-persist] [-nofork]
Or   : nbd-client -d nbd-device
Or   : nbd-client -c nbd device
Default values for blocksize is 1024 (recommended for ethernet)
Allowed values for blocksize are 512,1024,2048,2096
Note, that kernel 2.4.2 and older ones do not work correctly with
blocksizes other than 1024 without patches
connected /dev/nbd0
Activating...
Error: NBD_TYPE[0] contains unknown value
nbd-client.
 * Setting sensors limits                                                                                                                                                                          [ OK ]
It does not seem Authotkey is installed. Exiting...
 * Starting MTA                                                                                                                                                                                      [ OK ]
 * Starting the Windbind daemon windbind                                                                                                                                                 [  OK ]
saned disabled; edit etc/default/saned
Starting advanced periodic command scheduler: frcon.
 * Enabling additional executable binary formats binfmt-support                                                                                                                 [ OK ]
 * Checking battery state...                                                                                                                                                                      [  OK ]

```
Then a blinking cursor.

Any help would be great.
Thank you for your time

---

### Post by InTheMarket on 2010-11-24
Saned is just scanning, which I don't use. So that can't be it.

---

### Post by Zookalicious on 2010-11-24
Have you tried opening up the saned file from a LiveCD? I don't know what it does, so I'm just general-problemsolving here, but it might be worth a look. Also how long do you leave it to boot up? Sometimes people get impatient and shut down their machine, assuming its frozen when it's still working.

---

