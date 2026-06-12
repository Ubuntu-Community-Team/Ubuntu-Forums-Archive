---
title: "lxdm or startlubuntu issue when the disk is full"
date: 2012-03-13
forum: General Help
---

### Post by hrok on 2012-03-13
I am a **L**ubuntu user. Now the story goes that one day lxdm didn't let me login (even though i entered the correct username and password). At that time i didn't have any ideas why, so i reinstalled lubuntu. The second time that happened i found out in recovery mode that the disk was 100% full so i thought that maybe the the startlubuntu command doesn't work because the disk is full. So i erased some data that i didn't need (5G) and than lxdm started lubuntu normaly. Now yesterday it happened again, so i started to erase data in recovery mode, but to my amazement i had to erase around 15GB of data so that the df -h showed less than 100% usage. Now i would really like to come to the bottom of this. Why wouldn't lxdm start lubuntu if the disk is full? And maybe more importantly why does the system work one day, but the next day i have to erase 15GB and df -h still shows 100% usage? 

My df -h output now is
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G  271G  4.8G  99% /
udev                  1.5G  4.0K  1.5G   1% /dev
tmpfs                 604M  964K  603M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.5G   80K  1.5G   1% /run/shm

and the lxdm.log when the problem occurred looked like this
** Message: find greeter (nil)

** Message: find idle (nil)

** Message: add xserver watch


X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux stroj 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=37dd0d8f-6b0a-4695-81b8-2b554af97d17 ro recovery nomodeset
Build Date: 19 October 2011  05:21:26AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 12 12:52:21 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
** Message: add 0x1590300

** Message: prepare greeter on :0

** Message: start greeter on :0

** (process:1661): DEBUG: user rok auth ok

** (process:1661): DEBUG: login user rok session /usr/bin/startlubuntu lang 

** Message: find greeter (nil)

** Message: find idle 0x1590300

** Message: add 0x1590300

** Message: prepare greeter on :0

** Message: start greeter on :0

** Message: quit code 0

** Message: exit cb

** Message: free session

arc 1
 ddxSigGiveUp: Closing log

Now the first error about nv module is normal. I would really appreciate if someone helps me understand this issue.

---

### Post by miklcct on 2012-03-13
Have you fscked your drive? After that, you should consider reducing the reserved blocks to about 1%.

---

### Post by hrok on 2012-03-13
Yes i did fsck in recovery mode before i started erasing. It had little effect.

---

