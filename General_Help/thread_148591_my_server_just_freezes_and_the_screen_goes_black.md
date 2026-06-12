---
title: "my server just freezes and the screen goes black"
date: 2006-03-22
forum: General Help
---

### Post by Nasso on 2006-03-22
Hi all.
I have a problem :( A huge one...

I have a shuttle with a 1GHZ celeron cpu, 256mb memory, 2 harddrives (10gb+30gb) and the rest integrated on the motherboard.

This is my server and it is running ubuntu 5.10 (installed using a normal cd but using the "server" install in the beginning), apache, webmin, nfs, ssh, php, mysql, vsftpd and some other stuff. I dont have x installed on it and it normally just sits in the closet with just a networkcable and the powercord connected to it.

Yesterday when i logged in to the server remotley via ssh to manage some torrents in a screen everything just froze up. the ssh-session stopped responding, and the server seemed to have been shut down, it didnt respond to pings, the webserver was down, etc.

When i came home and took a look into my closet i saw that it was still on but i couldnt reach it from any of the other computers in my apartment. Because it was in a closet and pretty hot i installed some more fans in it because i thought it might be a heatproblem. It wansnt :P

Now i have it connected to a monitor, a keyboard and the network for testing. When i start it up it take something like 10-30 minutes before it just completely freezes up and the screen goes completely black. It looks like it still is on though, the fans are spinning and LEDs are lit.

Does anyone have any ideas what the problem might be?
I have owned to computer for a few days and everything has just been installed. It ran for about 2 days before it started to crash but it didnt have very much load during those 2 days.

Whould be really helpful for any hints and tips on how i could locate the problem and "eliminate" it ;)

Thanks in advance.

---

### Post by Mustard on 2006-03-22
Are there any power saving processes running or are there power saving options enabled in bios?

---

### Post by Nasso on 2006-03-22
i can check it out in bios but how do i control it in ubuntu?

---

### Post by Mustard on 2006-03-22
[QUOTE=Nasso]i can check it out in bios but how do i control it in ubuntu?[/QUOTE]

I have no idea what is installed in a server installation, but in a desktop installation the 'powernowd' application handles power management.  I'd emphasise this is just a bit of guesswork on my part, since I have read of many lockup issues with power saving features enabled.  If there are no processes running in your server install with regard to power saving then I would try the bios settings.  If you have no success with that then I guess its back to square one.

I suppose you could try 'locate powernowd' to see if you can find any reference to it on your system.

---

### Post by Nasso on 2006-03-22
ok, thanks.

i disables all powermanagement in bios and im now running cpu and memorystress on it. it seems to work fine, have been running for ~20 minutes now.

will let it sqrt() its *** of for a few more hours and then report back again :)

---

### Post by Mustard on 2006-03-22
[QUOTE=Nasso]ok, thanks.

i disables all powermanagement in bios and im now running cpu and memorystress on it. it seems to work fine, have been running for ~20 minutes now.

will let it sqrt() its *** of for a few more hours and then report back again :)[/QUOTE]

That would be great, because I would love to know the answers myself for future troubleshooting. :)

---

### Post by Nasso on 2006-03-22
The problem seems to be solved :) Have been running stress for over 2 hours now.

Will let you know if it ever freezes up again. 

For now... thanks alot! :)

EDIT: It crashed again :P

It crashed after 10 minutes of screen/2xbtdownloadcurse but it could take over 2 hours of stress.
Running stress on it now again. Is there any powermanagement going on?

> 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.0   1564    72 ?        S    21:13   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   21:13   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   21:13   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   21:13   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   21:13   0:00 [kthread]
root        20  0.0  0.0      0     0 ?        S<   21:13   0:00 [kblockd/0]
root        59  0.0  0.0      0     0 ?        S    21:13   0:00 [pdflush]
root        60  0.0  0.0      0     0 ?        S    21:13   0:00 [pdflush]
root        62  0.0  0.0      0     0 ?        S<   21:13   0:00 [aio/0]
root        61  0.1  0.0      0     0 ?        S    21:13   0:00 [kswapd0]
root       648  0.0  0.0      0     0 ?        S    21:13   0:00 [kseriod]
root      1522  0.0  0.0      0     0 ?        S    21:13   0:00 [khubd]
root      2408  0.0  0.0      0     0 ?        S    21:14   0:00 [kjournald]
root      2583  0.0  0.0   1656    20 ?        S<s  21:14   0:00 udevd --daemon
root      3638  0.0  0.0      0     0 ?        S    21:14   0:00 [khpsbpkt]
root      4277  0.0  0.0      0     0 ?        S    21:14   0:00 [kgameportd]
root      4476  0.0  0.0      0     0 ?        S    21:14   0:00 [knodemgrd_0]
dhcp      4839  0.0  0.0   2304    20 ?        Ss   21:14   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
daemon    4856  0.0  0.0   1656    16 ?        Ss   21:14   0:00 /sbin/portmap
syslog    5178  0.0  0.0   1760    84 ?        Ss   21:14   0:00 /sbin/syslogd -u syslog
root      5192  0.0  0.0   1564    20 ?        Ss   21:14   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5194  0.0  0.0   2576    20 ?        Ss   21:14   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5237  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5238  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5239  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5240  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5241  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5242  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5243  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5244  0.0  0.0      0     0 ?        S    21:14   0:00 [nfsd]
root      5245  0.0  0.0      0     0 ?        S    21:14   0:00 [lockd]
root      5246  0.0  0.0      0     0 ?        S<   21:14   0:00 [rpciod/0]
root      5257  0.0  0.0   1760    20 ?        Ss   21:14   0:00 /usr/sbin/rpc.mountd
root      5271  0.0  0.0   3540   216 ?        Ss   21:14   0:00 /usr/sbin/sshd
root      5282  0.0  0.0   3096    16 ?        Ss   21:14   0:00 /usr/sbin/vsftpd
root      5296  0.0  0.0   1724    20 ?        Ss   21:14   0:00 /sbin/rpc.statd
daemon    5308  0.0  0.0   1752    20 ?        Ss   21:14   0:00 /usr/sbin/atd
root      5318  0.0  0.0   1808    20 ?        Ss   21:14   0:00 /usr/sbin/cron
root      5330  0.0  0.0  13780    92 ?        Ss   21:14   0:00 /usr/sbin/apache2 -k start -DSSL
root      5338  0.0  0.0   1560    20 tty1     Ss+  21:14   0:00 /sbin/getty 38400 tty1
root      5340  0.0  0.0   1556    20 tty2     Ss+  21:14   0:00 /sbin/getty 38400 tty2
root      5341  0.0  0.0   1560    20 tty3     Ss+  21:14   0:00 /sbin/getty 38400 tty3
root      5342  0.0  0.0   1560    20 tty4     Ss+  21:14   0:00 /sbin/getty 38400 tty4
root      5343  0.0  0.0   1556    20 tty5     Ss+  21:14   0:00 /sbin/getty 38400 tty5
root      5344  0.0  0.0   1556    20 tty6     Ss+  21:14   0:00 /sbin/getty 38400 tty6
www-data  5368  0.0  0.0  13780    64 ?        S    21:14   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5369  0.0  0.0  13780    64 ?        S    21:14   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5370  0.0  0.0  13780    64 ?        S    21:14   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5371  0.0  0.0  13780    64 ?        S    21:14   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5372  0.0  0.0  13780    64 ?        S    21:14   0:00 /usr/sbin/apache2 -k start -DSSL
root      5373  0.0  0.2   8880   628 ?        Ss   21:14   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
nasso     5407  0.0  0.0   4900    20 ?        Ss   21:17   0:00 SCREEN
nasso     5408  0.0  0.0   5416    20 pts/1    Ss   21:17   0:00 /bin/bash
nasso     5417  0.0  0.0   1560    24 pts/1    S+   21:17   0:00 stress -c 10 -m 1
nasso     5418  8.9  0.0   1560    44 pts/1    R+   21:17   0:44 stress -c 10 -m 1
nasso     5419 11.6 21.0 263708 52304 pts/1    R+   21:17   0:58 stress -c 10 -m 1
nasso     5420  8.7  0.0   1560    44 pts/1    R+   21:17   0:43 stress -c 10 -m 1
nasso     5421  8.6  0.0   1560    44 pts/1    R+   21:17   0:43 stress -c 10 -m 1
nasso     5422  8.6  0.0   1560    44 pts/1    R+   21:17   0:43 stress -c 10 -m 1
nasso     5423  8.7  0.0   1560    44 pts/1    R+   21:17   0:43 stress -c 10 -m 1
nasso     5424  8.9  0.0   1560    44 pts/1    R+   21:17   0:44 stress -c 10 -m 1
nasso     5425  8.7  0.0   1560    44 pts/1    R+   21:17   0:43 stress -c 10 -m 1
nasso     5426  8.9  0.0   1560    44 pts/1    R+   21:17   0:44 stress -c 10 -m 1
nasso     5427  8.6  0.0   1560    44 pts/1    R+   21:17   0:42 stress -c 10 -m 1
nasso     5428  8.9  0.0   1560    44 pts/1    R+   21:17   0:44 stress -c 10 -m 1
root      5445  0.0  0.5   6280  1456 ?        Ss   21:24   0:00 sshd: nasso [priv]
nasso     5447  0.1  0.6   6280  1580 ?        S    21:24   0:00 sshd: nasso@pts/0
nasso     5448  0.1  0.7   5396  1968 pts/0    Ss   21:24   0:00 -bash
nasso     5461  0.0  0.4   4596  1044 pts/0    R+   21:25   0:00 ps aux
nasso     5462  0.0  0.7   5396  1972 pts/0    R+   21:25   0:00 -bash


lots of processes :p

---

### Post by Mustard on 2006-03-22
I can't see anything that jumps out at me.  Unfortunately that was my one and only guess. :)

---

### Post by Nasso on 2006-03-23
i have been stressing it for over 24 hours without crashes. i then ran screen with a btdownloadcurses and it crashed in just a few minutes. :P

doesnt seem to be some powersaving crashing it either. i left it idle for a few hours and it didnt crash. so i guess the problem has something to do with either the network or btdownloadcurses.

im thinking about installing dapper drake instead and install rtorrent. its in dappers repos but not breezys. having troubles compiling it. is dapper stable enough? im not going to use x.

---

### Post by Nasso on 2006-03-24
this is so wierd! 

i tried to update to dapper using apt-get dist-upgrade. so that i could use rtorrnet instead of btdownloadcurses.
it freezes while it is setting the locales. when i restart the computer and run dpkg --configure -a it continues setting locales, finnishes the one that it crashed on last and continues with the next one, and then crashes again :P it sometimes finishes more the one before it crashes :P

the problem doesnt seem to be btdownloadcurses...

---

