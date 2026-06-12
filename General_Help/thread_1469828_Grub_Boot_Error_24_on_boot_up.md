---
title: "Grub Boot Error 24 on boot up"
date: 2010-05-02
forum: General Help
---

### Post by daml on 2010-05-02
First off, I am new to Ubuntu and Linux and i'm sick of windows and the constant BS it tends to offer so with that said, 

I've been running version 9.10 for about 2 weeks now, this forum has helped me get a lot of my hardware devices working but this one is stumping me. When i boot this pc (Homemade) it get's a Grub Boot Error # 24. after searching some on the forum's i found and typed the following command into terminal and recieved the following:

[PHP]ubuntu@ubuntu:~$ dmesg | tail
[  164.102354] wlan0: authenticate with AP 00:1f:33:fd:89:67
[  164.105931] wlan0: authenticated
[  164.105936] wlan0: associate with AP 00:1f:33:fd:89:67
[  164.108927] wlan0: RX ReassocResp from 00:1f:33:fd:89:67 (capab=0x421 status=0 aid=2)
[  164.108932] wlan0: associated
[  164.115465] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  167.217163] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  175.109515] wlan0: no IPv6 routers present
[ 1329.591230] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 384 not in group (block 385195977)!
[ 1329.591657] EXT3-fs: group descriptors corrupted!
[/PHP]


What does this mean and how can i fix it?!

[PHP][ 1329.591230] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 384 not in group (block 385195977)!
[ 1329.591657] EXT3-fs: group descriptors corrupted![/PHP]

I'm currently running from the CDrom so needless to say the OS is non-functional!
Also, Windows IS NOT installed as a second OS for dual boot.


Any and all help is appreciated! 

Thanks!

-D

---

### Post by daml on 2010-05-02
bump

---

### Post by frantid on 2010-05-02
I don't remember if the disk utility is on the livecd.  You can use gparted as well.

launch the app, select the bad partition, perform a "check"


I'm sure there's a cmd line for it, but I don't know it.

---

### Post by oldfred on 2010-05-02
This is the command line change sdb1 to what ever partition you want:

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1


If you want to know the parameters run this:
man e2fsck

---

### Post by daml on 2010-05-02
Thanks OldFred,
That fixed it. i was hoping there was a check disk utility i could run but i didn't know the command or if it would even work from the CD-rom. 

I'll be sure to keep this command handy as it should come in handy later on down the road.  Thanks Again!!

-D

---

