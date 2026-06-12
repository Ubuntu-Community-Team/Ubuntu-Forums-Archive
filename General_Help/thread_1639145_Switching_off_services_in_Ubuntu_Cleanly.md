---
title: "Switching off services in Ubuntu Cleanly"
date: 2010-12-06
forum: General Help
---

### Post by Chint on 2010-12-06
Hi All

I have just got a VPS with Ubuntu on it. I have downloaded chkconfig and can see services but doesnt let me switch them off it errors when I try switch apache2 off. 

I want to harden the unit by switching off all non-essential services and the order they come in. Which ones can I turn off (and delete the script cleanly as not needed) and how in Ubuntu? I see a lot of the scripts in etc/init.d have got a sym link does it matter when I delete them?

Which ones can I delete in this list without affecting networking, core system and user maintenence (Bearbone system)?? And what the heck is plymouth services?

```
root@chicago:/etc/rc0.d# chkconfig --list
apache2                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
bind9                     0:off  1:off  2:off  3:off  4:off  5:off  6:off
bootlogd                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
console-screen.sh         0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
cron                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
fetchmail                 0:off  1:off  2:off  3:off  4:off  5:off  6:off
hostname                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
hwclock                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
hwclock-save              0:off  1:off  2:off  3:off  4:off  5:off  6:off
keymap.sh                 0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
killprocs                 0:off  1:on   2:off  3:off  4:off  5:off  6:off
klogd                     0:off  1:off  2:off  3:off  4:off  5:off  6:off
libpam-foreground         0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
module-init-tools         0:off  1:off  2:off  3:off  4:off  5:off  6:off
modules_dep.sh            0:off  1:off  2:on   3:on   4:on   5:on   6:off
network-interface         0:off  1:off  2:off  3:off  4:off  5:off  6:off
network-interface-security  0:off  1:off  2:off  3:off  4:off  5:off  6:off
networking                0:on   1:off  2:off  3:off  4:off  5:off  6:off
nmbd                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
ondemand                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-log              0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-splash           0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-stop             0:off  1:off  2:off  3:off  4:off  5:off  6:off
portmap                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
procps                    0:off  1:off  2:off  3:off  4:off  5:off  6:off
quota                     0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
quotarpc                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
rc.local                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
rcS                       0:off  1:off  2:off  3:off  4:off  5:off  6:off
rsync                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
saslauthd                 0:off  1:off  2:on   3:on   4:on   5:on   6:off
screen-cleanup            0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
sendmail                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
sendsigs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
smbd                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
ssh                       0:off  1:off  2:off  3:off  4:off  5:off  6:off
stop-bootlogd             0:off  1:off  2:off  3:off  4:off  5:off  6:off
stop-bootlogd-single      0:off  1:off  2:off  3:off  4:off  5:off  6:off
sysklogd                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
udev                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
udev-finish               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevmonitor               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevtrigger               0:off  1:off  2:off  3:off  4:off  5:off  6:off
umountfs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountnfs.sh              0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountroot                0:on   1:off  2:off  3:off  4:off  5:off  6:off
urandom                   0:on   1:off  2:off  3:off  4:off  5:off  6:off  S:on
vzquota                   0:on   1:on   2:on   3:on   4:on   5:on   6:off
wide-dhcpv6-client        0:off  1:off  2:off  3:off  4:off  5:off  6:off
xinetd                    0:off  1:off  2:on   3:on   4:on   5:on   6:off

```

---

