---
title: "Boot Problems udevadm trigger"
date: 2010-09-03
forum: General Help
---

### Post by Robert Lutken on 2010-09-03
Hi, i was updating my ubuntu last night and i had a power failure, when i booted up again it gave me this message
"udevadm trigger is not permmited while udev is unconfigured.
gave up waiting for root device common problems
-Boot args (cat /proc/cmdline)
-Check rootdelay = (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing moduales (cat /proc/modules; ls /dev)
ALET! /dev/disk/by-uuid/c25e67f7-2adb-499a-a57f-3507191abf does
pping to a shell!
busybox v1.13.3 (Ubuntu 1:1.13.3-1 ubuntu11) built in shell (ash)

 i have no idea what any of this means or where to go from here please help.
Thanks 
Welshy Rob

---

### Post by Francis 24/24 on 2010-09-03
I installed the last recommended updates, which some involve udev,
and reboot failed with this same message. There was no power failure. I reloaded my system from a backup, boot went fine, installed only the security updates, reboot is ok.

I would say there is a bug within this last - september 2 ? - batch of
updated packages. Since they are only recommended, I will wait a bit 
before trying to install them again.

---

### Post by Francis 24/24 on 2010-09-08
In order to avoid boot to stop with "udevadm trigger is not permitted ..."
after installing the last recommended updates for 10.04, as many
people have suffered, I suggest :

- install updates with Update Manager as usual

- DO NOT accept to reboot right now

- as root :

# cd /boot
# sudo update-initramfs -u -k 2.6.32-24-386
# sudo update-initramfs -u -k 2.6.32-24-generic

- reboot

Worked fine for me.

Cheers !

---

