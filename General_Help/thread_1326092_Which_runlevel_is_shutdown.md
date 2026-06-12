---
title: "Which runlevel is shutdown?"
date: 2009-11-14
forum: General Help
---

### Post by pullmoll on 2009-11-14
Hi all,
I wonder which runlevel is entered when I shutdown or reboot from gnome. It may be 6 or 0 as far as I know, but I'm unsure. Also, is the runlevel "started" or "stopped", i.e. which set of script links is run?

My problem is that nothing is unmounted before the system resets, thus leaving the mounts dirty and requiring fsck or journal replay.

Thanks,
pullmoll

---

### Post by scoon on 2009-11-14
Hey there, 

runlevel 6 is for restart and runlevel 0 is for shutdown.  I think it is a safe assumption that gnome is calling the correct runlevels.  Have you scanned syslog to see if anything jumps out?

Thanks.

---

### Post by pullmoll on 2009-11-14
> **scoon said:**
> Hey there, 

runlevel 6 is for restart and runlevel 0 is for shutdown.  I think it is a safe assumption that gnome is calling the correct runlevels.  Have you scanned syslog to see if anything jumps out?

Thanks.

Well, the syslog does have next to nothing regarding the shutdown. All I see is ```
Nov 14 13:14:55 ubuntu kernel: Kernel logging (proc) stopped.
```Here's the complete log from session 1, shutdown, session 2 (current): [syslog]("http://pastebin.com/m7d021c05")
The whole shutdown or restart after clicking on *restart now* takes 2 or 3 seconds and I don't see any line telling *unmounting ...*

To me it looks like the S01umountfs isn't run at all.
Here's the runlevel dirs contents:
```
pm@ubuntu:/etc$ ls rc0.d
K01alsa-utils        K20virtualbox-ose-guest-utils  S01umountnfs.sh
K01kerneloops        K31atieventsd                  S01umountroot
K01laptop-mode       README                         S01unattended-upgrades
K01tinyproxy         S01halt                        S02urandom
K02bluetooth         S01networking                  S02wpa-ifupdown
K20clamav-freshclam  S01sendsigs                    S06cryptdisks-early
K20virtualbox-ose    S01umountfs                    S08cryptdisks
pm@ubuntu:/etc$ ls rc6.d
K01alsa-utils        K20virtualbox-ose-guest-utils  S01umountnfs.sh
K01kerneloops        K31atieventsd                  S01umountroot
K01laptop-mode       README                         S01unattended-upgrades
K01tinyproxy         S01halt                        S02urandom
K02bluetooth         S01networking                  S02wpa-ifupdown
K20clamav-freshclam  S01sendsigs                    S06cryptdisks-early
K20virtualbox-ose    S01umountfs                    S08cryptdisks

```

---

### Post by pullmoll on 2009-11-15
Solved by reinstalling Karmic Koala. I don't know what caused the problems in the first hand, though.

---

