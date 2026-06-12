---
title: "boot.log error fix needed"
date: 2011-07-10
forum: General Help
---

### Post by Jony35359595 on 2011-07-10
Hi everyine,
In my 11.04 boot.log file I found this:

> fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 405948/7200768 files, 19542826/28798720 blocks
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/gdm-guest-session (/etc/apparmor.d/gdm-guest-session line 49): profile /usr/share/gdm/guest-session/Xsession network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Warning from /etc/apparmor.d/sbin.dhclient (/etc/apparmor.d/sbin.dhclient line 73): profile /sbin/dhclient network rules not enforced
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-trunk
Cache read/write disabled: /sys/kernel/security/apparmor/features interface file missing. (Kernel needs AppArmor 2.4 compatibility patch.)
 * Starting mDNS/DNS-SD daemon[154G[ OK ]
Warning from /etc/apparmor.d/usr.sbin.tcpdump (/etc/apparmor.d/usr.sbin.tcpdump line 54): profile /usr/sbin/tcpdump network rules not enforced
 * Stopping cold plug devices[154G[ OK ]
 * Stopping log initial device creation[154G[ OK ]
 * Starting configure virtual network devices[154G[ OK ]
 * Starting configure network device security[154G[ OK ]
 * Starting save udev log and update rules[154G[ OK ]
 * Stopping configure virtual network devices[154G[ OK ]
 * Stopping save udev log and update rules[154G[ OK ]
 * Starting network connection manager[154G[ OK ]

So, how can I disable fsck autorun on every boot?
And what's that network errors? How to fix it?

P.S. All works fine but boot time is much longer then it was earlier.

Thanks!

---

