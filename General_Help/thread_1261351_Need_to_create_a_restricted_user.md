---
title: "Need to create a restricted user"
date: 2009-09-08
forum: General Help
---

### Post by ankushpandit on 2009-09-08
Hi,
I am a newbie to [Linux]("http://www.linuxforums.org/forum/#") and I want to create a user which can only execute network config commands like ifconfig and ping(to check the config). The following is what I did but failed.
1) Created a group called 'netconfig'.
2) added a user named 'user'.
3) added user to the 'netconfig' group.
4) Changed the permissions on /bin and /sbin directories so that only groups 'root' and 'netconfig' can Read & execute.
The Result
1) I can execute ping and ifconfig commands when I log on as 'root' and can configure the network(as Default ofcourse).
2) The problem arises when I execute this command and get the following response.
[A]
/bin/ping x.x.x.x [enter]
ping: icmp open socket: Operation not permitted
[b]
/sbin/ifconfig [enter]
eth0 Link encap:Ethernet HWaddr 00:00:00:00:00:00
inet addr x.x.x.x Bcast x.x.x.255 Mask:255.255.255.0
inet6 addr: aaaa::aaaa:aaaa:aaaa:9999/00 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1320 errors:0 dropped:0 overruns:0 frame:0
TX packets:991 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:138423 (135.1 KiB) TX bytes:178569 (174.3 KiB)
Memory:d0200000-d0220000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2343 errors:0 dropped:0 overruns:0 frame:0
TX packets:2343 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2709476 (2.5 MiB) TX bytes:2709476 (2.5 MiB)
[this seems to work fine till I dont execute the following line]
[C]
/sbin/ifconfig eth0 down [enter]
SIOCSIFFLAGS: Permission denied
I have 2 questions
a} Am I at a right path for my goal, i.e. Am I doing right steps for creating a user which has only access to 'ifconfig' and 'ping' command?
b} Is there a better way for creating a restricted user with access to only 2 commands?
Please help with this. Any examples and experiences are welcome.
Thanks in advance,
Ankush Pandit.

---

### Post by hal10000 on 2009-09-08
If you want your user to avoid changing network configuration, then i guess you just have to remove him/her from the [COLOR="Red"]admin[/COLOR] group, so he can not run sudo commands.

---

### Post by ankushpandit on 2009-09-09
well by restricted user i meant that the user is restricted to use all commands except ifconfig and ping.

---

### Post by ankushpandit on 2009-09-09
Hi

I found a solution not exactly up to the point but will like to share.

This is what I did(logged in as a root)

1) Added a group : groupadd netadmins
2) Added a user : useradd admin1
3) Gave a password for admin1 : passwd admin1
4) Added admin1 as a member of group netadmins : usermod -g netadmins admin1
5) Edited /etc/sudoers : vi /etc/sudoers

added two lines 

1st
#added this just after the "Cmnd_Alias NETWORKING decleration"
Cmnd_Alias TIGHTNETWORKING = /sbin/ifconfig, /bin/ping

2nd
#added this just after the "root    ALL=(ALL)       ALL"
%netadmins ALL = (ALL) NOPASSWD:TIGHTNETWORKING

saved the file with "wq!" as sudoers is a readonly file!
---------------------------------------------------------------------
The result 

logged off from root, logged in as admin1.
executed the ifconfig and ping using sudo

[admin1@177 ~] sudo /sbin/ifconfig eth0 up

It worked out fine.

[admin1@177 ~] sudo /bin/ping x.x.x.x

This worked on fine and I later realized that ping works without sudo too.

This solved a major part of my problem i.e. now a non admin user can execute 'ifconfig' if the user 

is a part of 'netadmins'.

Now does anyone has an idea how to disable all the other commands including "ll ls pwd ....etc etc"

Thankz in advance.

---

