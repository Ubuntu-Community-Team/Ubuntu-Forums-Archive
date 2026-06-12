---
title: "Home Network....need help!"
date: 2006-03-02
forum: General Help
---

### Post by Justbill on 2006-03-02
Hi All! 
I am new to Ubuntu, however I have been tinkering with Linux (FC4) for about a year now. I am a cabinet maker by trade, so the computer "jargon" is sometimes a little hard for me to understand (go easy on me guys).

Here is the problem, I have 2 computers sharing an internet connection using a Belkin router. This is a **wired** network.
Box 1 is a:
Compaq Presario SR1426NX
2.93Ghz Pentium 4
512Mb DDR2 SDRAM
160GB 7200RPM Serial ATA hard drive
dual booting Win XP and Fedora Core4

Box 2 is a HP Pavilion 6630
500Mhz Celeron
256Mb ram
80GB hard drive
Ubuntu 5.10

Box 1 hostname is Goliath, box 2 is Ulysses. From Goliath (box1) I can view my "home" on Ulysses using this command as root:

mount -t nfs Goliath.justbillsguitars.com:/home/bill /mnt
mount 
cd /mnt
ls

and at that point I can view my home on box 2. When I try the same thing from Ulysses (box2) as root, or sudo, I get this error:

bill@Ulysses:~$ su
Password:
root@Ulysses:/home/bill# mount -t nfs Goliath.justbillsguitars.com:/home/Bill /mnt
mount: RPC: Remote system error - No route to host

I checked my /etc/hosts file and I believe its alright, however I am new to this, so I will post it (from Ulysses) here:

bill@Ulysses:~$ cat /etc/hosts
127.0.0.1       Ulysses.justbillsguitars.com   localhost  localhost.localdomain
192.168.2.2     Goliath.justbillsguitars.com   localhost  localhost
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

In both computers I have the /etc/hosts.allow file set up like this:

bill@Ulysses:~$ cat /etc/hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
 ALL: .justbillsguitars.com

I believe (HOPE) this is correct.

If anyone can shed some light on this, it would be greatly appreciated! I really don't understand the mount: RPC: Remote system error - No route to host

Thanks much
Justbill

---

