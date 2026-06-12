---
title: "140 process running on Ubuntu Server"
date: 2010-03-05
forum: General Help
---

### Post by waloshin on 2010-03-05
I am running an Lamp ubuntu 9.10 server and are all these processes supposed to be running?

Memory:

1829 	www-data 	209080 kB 	/usr/sbin/apache2 -k start
2052 	www-data 	207560 kB 	/usr/sbin/apache2 -k start
1833 	www-data 	207300 kB 	/usr/sbin/apache2 -k start
2044 	www-data 	207296 kB 	/usr/sbin/apache2 -k start
4088 	www-data 	205760 kB 	/usr/sbin/apache2 -k start
1830 	www-data 	205208 kB 	/usr/sbin/apache2 -k start
4086 	www-data 	200368 kB 	/usr/sbin/apache2 -k start
1796 	root 	200276 kB 	/usr/sbin/apache2 -k start
4477 	www-data 	200276 kB 	/usr/sbin/apache2 -k start
4478 	www-data 	200276 kB 	/usr/sbin/apache2 -k start
4479 	www-data 	200276 kB 	/usr/sbin/apache2 -k start
1273 	mysql 	178992 kB 	/usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file ...
1385 	nobody 	142632 kB 	/usr/bin/memcached -m 64 -p 11211 -u nobody -l 127.0.0.1
671 	syslog 	126388 kB 	rsyslogd -c4
3852 	root 	118076 kB 	/usr/sbin/console-kit-daemon
1630 	root 	94088 kB 	/usr/sbin/smbd -D
1672 	root 	94088 kB 	/usr/sbin/smbd -D
1716 	root 	75016 kB 	/usr/sbin/cupsd -C /etc/cups/cupsd.conf
4526 	root 	70544 kB 	/home/*****/webmin-1.500/proc/index_size.cgi
4524 	root 	67676 kB 	/usr/bin/perl /home/*****/webmin-1.500/miniserv.pl /etc/webmin/miniserv.conf
4516 	root 	67668 kB 	/usr/bin/perl /home/*****/webmin-1.500/miniserv.pl /etc/webmin/miniserv.conf
1869 	root 	67556 kB 	/usr/bin/perl /home/*****/webmin-1.500/miniserv.pl /etc/webmin/miniserv.conf
1683 	root 	63536 kB 	/usr/sbin/winbindd
1690 	root 	63536 kB 	/usr/sbin/winbindd
1558 	root 	58336 kB 	/usr/sbin/nmbd -D
1838 	root 	55892 kB 	/usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock
1561 	root 	49072 kB 	/usr/sbin/sshd
1588 	postfix 	39232 kB 	qmgr -l -t fifo -u
4386 	postfix 	39072 kB 	pickup -l -t fifo -u -c
1478 	root 	37012 kB 	/usr/lib/postfix/master
900 	avahi 	31884 kB 	avahi-daemon: registering [server1.local]
902 	avahi 	31760 kB 	avahi-daemon: chroot helper
704 	messagebus 	23328 kB 	dbus-daemon --system --fork
1653 	root 	22628 kB 	/usr/sbin/vsftpd
442 	root 	21308 kB 	mountall --daemon --tmptime=0
1 	root 	19320 kB 	/sbin/init
1082 	root 	18708 kB 	cron
586 	root 	17236 kB 	udevd --daemon
470 	root 	17132 kB 	udevd --daemon
587 	root 	17128 kB 	udevd --daemon
1083 	daemon 	16512 kB 	atd
456 	root 	12636 kB 	upstart-udev-bridge --daemon
623 	root 	8192 kB 	dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
1318 	root 	6464 kB 	dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhc ...
1059 	root 	5988 kB 	/sbin/getty -8 38400 tty4
1062 	root 	5988 kB 	/sbin/getty -8 38400 tty5
1067 	root 	5988 kB 	/sbin/getty -8 38400 tty2
1068 	root 	5988 kB 	/sbin/getty -8 38400 tty3
1070 	root 	5988 kB 	/sbin/getty -8 38400 tty6
1870 	root 	5988 kB 	/sbin/getty -8 38400 tty1
1165 	root 	4004 kB 	/bin/sh /usr/bin/mysqld_safe
1274 	root 	3908 kB 	logger -t mysqld -p daemon.error
2 	root 	0 kB 	[kthreadd]
3 	root 	0 kB 	[migration/0]
4 	root 	0 kB 	[ksoftirqd/0]
5 	root 	0 kB 	[watchdog/0]
6 	root 	0 kB 	[migration/1]
7 	root 	0 kB 	[ksoftirqd/1]
8 	root 	0 kB 	[watchdog/1]
9 	root 	0 kB 	[migration/2]
10 	root 	0 kB 	[ksoftirqd/2]
11 	root 	0 kB 	[watchdog/2]
12 	root 	0 kB 	[migration/3]
13 	root 	0 kB 	[ksoftirqd/3]
14 	root 	0 kB 	[watchdog/3]
15 	root 	0 kB 	[events/0]
16 	root 	0 kB 	[events/1]
17 	root 	0 kB 	[events/2]
18 	root 	0 kB 	[events/3]
19 	root 	0 kB 	[cpuset]
20 	root 	0 kB 	[khelper]
21 	root 	0 kB 	[netns]
22 	root 	0 kB 	[async/mgr]
23 	root 	0 kB 	[kintegrityd/0]
24 	root 	0 kB 	[kintegrityd/1]
25 	root 	0 kB 	[kintegrityd/2]
26 	root 	0 kB 	[kintegrityd/3]
27 	root 	0 kB 	[kblockd/0]
28 	root 	0 kB 	[kblockd/1]
29 	root 	0 kB 	[kblockd/2]
30 	root 	0 kB 	[kblockd/3]
31 	root 	0 kB 	[kacpid]
32 	root 	0 kB 	[kacpi_notify]
33 	root 	0 kB 	[kacpi_hotplug]
34 	root 	0 kB 	[ata/0]
35 	root 	0 kB 	[ata/1]
36 	root 	0 kB 	[ata/2]
37 	root 	0 kB 	[ata/3]
38 	root 	0 kB 	[ata_aux]
39 	root 	0 kB 	[ksuspend_usbd]
40 	root 	0 kB 	[khubd]
41 	root 	0 kB 	[kseriod]
42 	root 	0 kB 	[kmmcd]
43 	root 	0 kB 	[bluetooth]
44 	root 	0 kB 	[khungtaskd]
45 	root 	0 kB 	[pdflush]
46 	root 	0 kB 	[pdflush]
47 	root 	0 kB 	[kswapd0]
48 	root 	0 kB 	[aio/0]
49 	root 	0 kB 	[aio/1]
50 	root 	0 kB 	[aio/2]
51 	root 	0 kB 	[aio/3]
52 	root 	0 kB 	[ecryptfs-kthrea]
53 	root 	0 kB 	[crypto/0]
54 	root 	0 kB 	[crypto/1]
55 	root 	0 kB 	[crypto/2]
56 	root 	0 kB 	[crypto/3]
63 	root 	0 kB 	[scsi_eh_0]
64 	root 	0 kB 	[scsi_eh_1]
67 	root 	0 kB 	[scsi_eh_2]
68 	root 	0 kB 	[scsi_eh_3]
76 	root 	0 kB 	[kstriped]
77 	root 	0 kB 	[kmpathd/0]
78 	root 	0 kB 	[kmpathd/1]
79 	root 	0 kB 	[kmpathd/2]
80 	root 	0 kB 	[kmpathd/3]
81 	root 	0 kB 	[kmpath_handlerd]
82 	root 	0 kB 	[ksnapd]
83 	root 	0 kB 	[kondemand/0]
84 	root 	0 kB 	[kondemand/1]
85 	root 	0 kB 	[kondemand/2]
86 	root 	0 kB 	[kondemand/3]
87 	root 	0 kB 	[kconservative/0]
88 	root 	0 kB 	[kconservative/1]
89 	root 	0 kB 	[kconservative/2]
90 	root 	0 kB 	[kconservative/3]
91 	root 	0 kB 	[krfcommd]
390 	root 	0 kB 	[kjournald2]
391 	root 	0 kB 	[ext4-dio-unwrit]
392 	root 	0 kB 	[ext4-dio-unwrit]
393 	root 	0 kB 	[ext4-dio-unwrit]
394 	root 	0 kB 	[ext4-dio-unwrit]
658 	root 	0 kB 	[kpsmoused]
674 	root 	0 kB 	[hd-audio0]
684 	root 	0 kB 	[i915/0]
685 	root 	0 kB 	[i915/1]
687 	root 	0 kB 	[i915/2]
689 	root 	0 kB 	[i915/3]

Cpu: 

4524 	root 	0.2 % 	/home/******/webmin-1.500/proc/index_cpu.cgi
1 	root 	0.0 % 	/sbin/init
2 	root 	0.0 % 	[kthreadd]
3 	root 	0.0 % 	[migration/0]
4 	root 	0.0 % 	[ksoftirqd/0]
5 	root 	0.0 % 	[watchdog/0]
6 	root 	0.0 % 	[migration/1]
7 	root 	0.0 % 	[ksoftirqd/1]
8 	root 	0.0 % 	[watchdog/1]
9 	root 	0.0 % 	[migration/2]
10 	root 	0.0 % 	[ksoftirqd/2]
11 	root 	0.0 % 	[watchdog/2]
12 	root 	0.0 % 	[migration/3]
13 	root 	0.0 % 	[ksoftirqd/3]
14 	root 	0.0 % 	[watchdog/3]
15 	root 	0.0 % 	[events/0]
16 	root 	0.0 % 	[events/1]
17 	root 	0.0 % 	[events/2]
18 	root 	0.0 % 	[events/3]
19 	root 	0.0 % 	[cpuset]
20 	root 	0.0 % 	[khelper]
21 	root 	0.0 % 	[netns]
22 	root 	0.0 % 	[async/mgr]
23 	root 	0.0 % 	[kintegrityd/0]
24 	root 	0.0 % 	[kintegrityd/1]
25 	root 	0.0 % 	[kintegrityd/2]
26 	root 	0.0 % 	[kintegrityd/3]
27 	root 	0.0 % 	[kblockd/0]
28 	root 	0.0 % 	[kblockd/1]
29 	root 	0.0 % 	[kblockd/2]
30 	root 	0.0 % 	[kblockd/3]
31 	root 	0.0 % 	[kacpid]
32 	root 	0.0 % 	[kacpi_notify]
33 	root 	0.0 % 	[kacpi_hotplug]
34 	root 	0.0 % 	[ata/0]
35 	root 	0.0 % 	[ata/1]
36 	root 	0.0 % 	[ata/2]
37 	root 	0.0 % 	[ata/3]
38 	root 	0.0 % 	[ata_aux]
39 	root 	0.0 % 	[ksuspend_usbd]
40 	root 	0.0 % 	[khubd]
41 	root 	0.0 % 	[kseriod]
42 	root 	0.0 % 	[kmmcd]
43 	root 	0.0 % 	[bluetooth]
44 	root 	0.0 % 	[khungtaskd]
45 	root 	0.0 % 	[pdflush]
46 	root 	0.0 % 	[pdflush]
47 	root 	0.0 % 	[kswapd0]
48 	root 	0.0 % 	[aio/0]
49 	root 	0.0 % 	[aio/1]
50 	root 	0.0 % 	[aio/2]
51 	root 	0.0 % 	[aio/3]
52 	root 	0.0 % 	[ecryptfs-kthrea]
53 	root 	0.0 % 	[crypto/0]
54 	root 	0.0 % 	[crypto/1]
55 	root 	0.0 % 	[crypto/2]
56 	root 	0.0 % 	[crypto/3]
63 	root 	0.0 % 	[scsi_eh_0]
64 	root 	0.0 % 	[scsi_eh_1]
67 	root 	0.0 % 	[scsi_eh_2]
68 	root 	0.0 % 	[scsi_eh_3]
76 	root 	0.0 % 	[kstriped]
77 	root 	0.0 % 	[kmpathd/0]
78 	root 	0.0 % 	[kmpathd/1]
79 	root 	0.0 % 	[kmpathd/2]
80 	root 	0.0 % 	[kmpathd/3]
81 	root 	0.0 % 	[kmpath_handlerd]
82 	root 	0.0 % 	[ksnapd]
83 	root 	0.0 % 	[kondemand/0]
84 	root 	0.0 % 	[kondemand/1]
85 	root 	0.0 % 	[kondemand/2]
86 	root 	0.0 % 	[kondemand/3]
87 	root 	0.0 % 	[kconservative/0]
88 	root 	0.0 % 	[kconservative/1]
89 	root 	0.0 % 	[kconservative/2]
90 	root 	0.0 % 	[kconservative/3]
91 	root 	0.0 % 	[krfcommd]
390 	root 	0.0 % 	[kjournald2]
391 	root 	0.0 % 	[ext4-dio-unwrit]
392 	root 	0.0 % 	[ext4-dio-unwrit]
393 	root 	0.0 % 	[ext4-dio-unwrit]
394 	root 	0.0 % 	[ext4-dio-unwrit]
442 	root 	0.0 % 	mountall --daemon --tmptime=0
456 	root 	0.0 % 	upstart-udev-bridge --daemon
470 	root 	0.0 % 	udevd --daemon
586 	root 	0.0 % 	udevd --daemon
587 	root 	0.0 % 	udevd --daemon
623 	root 	0.0 % 	dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
658 	root 	0.0 % 	[kpsmoused]
671 	syslog 	0.0 % 	rsyslogd -c4
674 	root 	0.0 % 	[hd-audio0]
684 	root 	0.0 % 	[i915/0]
685 	root 	0.0 % 	[i915/1]
687 	root 	0.0 % 	[i915/2]
689 	root 	0.0 % 	[i915/3]
704 	messagebus 	0.0 % 	dbus-daemon --system --fork
900 	avahi 	0.0 % 	avahi-daemon: registering [server1.local]
902 	avahi 	0.0 % 	avahi-daemon: chroot helper
1059 	root 	0.0 % 	/sbin/getty -8 38400 tty4
1062 	root 	0.0 % 	/sbin/getty -8 38400 tty5
1067 	root 	0.0 % 	/sbin/getty -8 38400 tty2
1068 	root 	0.0 % 	/sbin/getty -8 38400 tty3
1070 	root 	0.0 % 	/sbin/getty -8 38400 tty6
1082 	root 	0.0 % 	cron
1083 	daemon 	0.0 % 	atd
1165 	root 	0.0 % 	/bin/sh /usr/bin/mysqld_safe
1273 	mysql 	0.0 % 	/usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file ...
1274 	root 	0.0 % 	logger -t mysqld -p daemon.error
1318 	root 	0.0 % 	dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhc ...
1385 	nobody 	0.0 % 	/usr/bin/memcached -m 64 -p 11211 -u nobody -l 127.0.0.1
1478 	root 	0.0 % 	/usr/lib/postfix/master
1558 	root 	0.0 % 	/usr/sbin/nmbd -D
1561 	root 	0.0 % 	/usr/sbin/sshd
1588 	postfix 	0.0 % 	qmgr -l -t fifo -u
1630 	root 	0.0 % 	/usr/sbin/smbd -D
1653 	root 	0.0 % 	/usr/sbin/vsftpd
1672 	root 	0.0 % 	/usr/sbin/smbd -D
1683 	root 	0.0 % 	/usr/sbin/winbindd
1690 	root 	0.0 % 	/usr/sbin/winbindd
1716 	root 	0.0 % 	/usr/sbin/cupsd -C /etc/cups/cupsd.conf
1796 	root 	0.0 % 	/usr/sbin/apache2 -k start
1829 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
1830 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
1833 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
1838 	root 	0.0 % 	/usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock
1869 	root 	0.0 % 	/usr/bin/perl /home/*****/webmin-1.500/miniserv.pl /etc/webmin/miniserv.conf
1870 	root 	0.0 % 	/sbin/getty -8 38400 tty1
2044 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
2052 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
3852 	root 	0.0 % 	/usr/sbin/console-kit-daemon
4086 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
4088 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
4386 	postfix 	0.0 % 	pickup -l -t fifo -u -c
4477 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
4478 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
4479 	www-data 	0.0 % 	/usr/sbin/apache2 -k start
4516 	root 	0.0 % 	/usr/bin/perl /home/******/webmin-1.500/miniserv.pl /etc/webmin/miniserv.conf

---

### Post by dcstar on 2010-03-06
> **waloshin said:**
> I am running an Lamp ubuntu 9.10 server and are all these processes supposed to be running?
........

Sure, why not.

Is there any special reason **you** think that there is something wrong?

---

### Post by flippo on 2010-03-06
Many processes may run on a system at a given time.  The most telling about if a system is being stressed by to many processes is the "load" factor.  Load is essentially the number of parallel things your processor is trying to do at a given time.  Under normal uses load is well under 1 (mine is .08 right now and I'm running 4 terminals idling, thunderbird, firefox, and chrome streaming video).  You can view your load using "top" in a terminal (load is at the top part of the display).

---

### Post by Prendi on 2010-04-21
AFAIK, the processes in brackets are not actual programs, but parts of the Linux kernel. Windows would just list all of them as the single entry "System" in the task manager. Almost all of the remaining processes seem relevant to a LAMP-System.

---

