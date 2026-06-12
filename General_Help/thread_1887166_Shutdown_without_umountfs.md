---
title: "Shutdown without umountfs"
date: 2011-11-26
forum: General Help
---

### Post by bkleine on 2011-11-26
I have reported this problem already for ubuntu 11.04. After a clean new install of Ubuntu 11.10 (no relicts from previous versions, etc, usr, var all new and reformatted) umountfs worked. However, when I updated to get the most up-to-date versions, drives are no longer umounted upon shutdown. Even going to "init 1" and to shutdown from there, drives are not umounted. This is really strange. 

in /etc/rc0.d there is  S01umountfs as link to the script umountfs which should umount all drives. This script is either not working or never reached. When I had the init 1 level, I tried "init 0", but the script did not run. There should at least be be the message: umounting local file systems, this message does not show up. I can manually umount all non-active filesystems from init 1, but /usr, /var, and / are not umounted and need recovery on every booting.

Which script should call S01umountfs?

I will be glad to delve deeper in this issue, but I need help.

Any help welcome

Bernhard

---

### Post by bkleine on 2011-11-26
No idea?

---

### Post by wicoociw on 2011-12-04
Hi,


is your reboot-job a S01reboot-Symlink (a higher number than S01umountfs)? I had the same problem and on my side, reboot was S03reboot, so this was called before S03umounfs etc. are executed... I had to rename S03reboot to S06reboot in rc0.d.

Maybe, something is wrong with your SysV-Order in rc6 and/or rc0?


Greetings,
Martin

---

