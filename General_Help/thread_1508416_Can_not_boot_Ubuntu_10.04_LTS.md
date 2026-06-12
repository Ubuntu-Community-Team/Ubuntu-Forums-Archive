---
title: "Can not boot Ubuntu 10.04 LTS"
date: 2010-06-12
forum: General Help
---

### Post by sajumuhamma on 2010-06-12
[B]I am using Ubuntu 10.04 LTS. Two  days ago I updated using update manager. After that I can not boot  Ubuntu.  When I trying to boot system showing  message 
[/B]

[B]" Ubuntu is running in low-graphics mode
Your screen, graphics card and input device settings could not be  detected correctly. You will need to configure these yourself"[/B]
 
**But I can not configure it.**


[B]I can not boot to  'recovery mode' also
[/B]
[B] 

/var/log/boot.log

[/B]```
fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 304282/1680960 files, 2964945/6723194 blocks
init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory

init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory

init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory

init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory

init: Failed to spawn rsyslog main process: unable to execute: No such file or directory

init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory

init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory

init: Failed to spawn network-manager main process: unable to execute: No such file or directory

init: avahi-daemon main process (696) terminated with status 2

init: avahi-daemon main process ended, respawning

init: gdm main process (695) terminated with status 2

init: Failed to spawn ufw pre-start process: unable to execute: No such file or directory

init: Failed to spawn ufw post-stop process: unable to execute: No such file or directory

init: Disconnected from system bus

init: alsa-mixer-save main process (813) terminated with status 2

init: usplash main process (818) terminated with status 2

Checking for running unattended-upgrades:  * Asking all remaining processes to terminate...       [80G 
[74G[ OK ]
 * All processes ended within 1 seconds....       [80G 
[74G[ OK ]
 * Deconfiguring network interfaces...       [80G 
[74G[ OK ]
 * Deactivating swap...       [80G 
[74G[ OK ]
 * Unmounting weak filesystems...       [80G 
[74G[ OK ]
mount: / is busy
 * Will now restart

```


**Now I am using Live CD.**


[B]Please help me
[/B]

**Thanks in advance**

---

### Post by claracc on 2010-06-13
From grub options at booting, you select the last kernel but in recovery mode. Then you can use the fix graphics option.

Regards

---

### Post by sajumuhamma on 2010-06-13
Thanks for the replay

I decided to reinstall OS

---

### Post by sajumuhamma on 2010-06-13
I decided to reinstall the OS

---

