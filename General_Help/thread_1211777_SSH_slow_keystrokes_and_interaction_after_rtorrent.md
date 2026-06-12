---
title: "SSH: slow keystrokes and interaction after rtorrent install"
date: 2009-07-13
forum: General Help
---

### Post by RudeIota on 2009-07-13
I know this sounds weird but...

Whenever I login to my Ubuntu file server over my local network via SSH, interaction is abnormally slow. The login itself is nice and smooth (user name and password), but after I'm logged in, it takes nearly a second for keystrokes to show in the terminal. This happens on two Windows clients using putty and Ponderosa... So I think I've narrowed this to the file server itself.

I use the Ubuntu computer primarily as a file server with only the "server" install package, several CLI programs installed and no desktop manager.

I don't know how this could be related, but it started *immediately *after I run rtorrent 8.4 for the first time (configured, made and make installed the latest versions of libtorrent and rtorrent moments before). rtorrent started up pretty roughly and the interface was not responsive. I mashed the CTRL + Q buttons several times and it finally quit after 20 seconds or so. Ever since then, SSH has been dog slow.

Of course, I tried rebooting both computers and checked for processes that might be using CPU, but I don't see anything.

Everything on my network is wired. I'm still able to transfer files via SMB from the server to the client at over 9MB/sec, so it doesn't appear to be a network issue (another possible cause of poor SSH responsiveness).

My Ubuntu system is an Athlon XP @ 1GHz with 1GB RAM running Ubuntu 8.04 (Kernel 2.6.24-24-server). I shouldn't have anything unusual running in the background.. It's pretty stock and has served me well for a few years. I haven't made any changes to it in over a year, with the exception of an update from 7.10 to 8.04 a few weeks ago and the upgrade for libtorrent and rtorrent I performed today.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2844  1692 ?        Ss   20:55   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   20:55   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   20:55   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   20:55   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   20:55   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   20:55   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   20:55   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   20:55   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   20:55   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   20:55   0:00 [kacpi_notify]
root       107  0.0  0.0      0     0 ?        S<   20:55   0:00 [kseriod]
root       145  0.0  0.0      0     0 ?        S    20:55   0:00 [pdflush]
root       146  0.0  0.0      0     0 ?        S    20:55   0:00 [pdflush]
root       147  0.0  0.0      0     0 ?        S<   20:55   0:00 [kswapd0]
root       191  0.0  0.0      0     0 ?        S<   20:55   0:00 [aio/0]
root      1334  0.0  0.0      0     0 ?        S<   20:55   0:00 [ksuspend_usbd]
root      1340  0.0  0.0      0     0 ?        S<   20:55   0:00 [khubd]
root      1347  0.0  0.0      0     0 ?        S<   20:55   0:00 [ata/0]
root      1354  0.0  0.0      0     0 ?        S<   20:55   0:00 [ata_aux]
root      1853  0.0  0.0      0     0 ?        S<   20:55   0:00 [scsi_eh_0]
root      1855  0.0  0.0      0     0 ?        S<   20:55   0:00 [scsi_eh_1]
root      1857  0.0  0.0      0     0 ?        S<   20:55   0:00 [scsi_eh_2]
root      2129  0.0  0.0      0     0 ?        S<   20:55   0:00 [scsi_eh_3]
root      2131  0.0  0.0      0     0 ?        S<   20:55   0:00 [scsi_eh_4]
root      2428  0.0  0.0      0     0 ?        S<   20:55   0:00 [kjournald]
root      2587  0.0  0.0   2220   668 ?        S<s  20:55   0:00 /sbin/udevd --daemon
root      2942  0.0  0.0      0     0 ?        S<   20:55   0:00 [kgameportd]
root      2955  0.0  0.0      0     0 ?        S<   20:55   0:00 [kpsmoused]
root      3737  0.0  0.0      0     0 ?        S<   20:55   0:00 [khpsbpkt]
root      3884  0.0  0.0      0     0 ?        S<   20:55   0:00 [kjournald]
root      4282  0.0  0.0   1716   512 tty4     Ss+  20:55   0:00 /sbin/getty 38400 tty4
root      4284  0.0  0.0   1716   512 tty5     Ss+  20:55   0:00 /sbin/getty 38400 tty5
root      4291  0.0  0.0   1716   512 tty2     Ss+  20:55   0:00 /sbin/getty 38400 tty2
root      4294  0.0  0.0   1716   512 tty3     Ss+  20:55   0:00 /sbin/getty 38400 tty3
root      4296  0.0  0.0   1716   516 tty6     Ss+  20:55   0:00 /sbin/getty 38400 tty6
syslog    4331  0.0  0.0   1936   648 ?        Rs   20:55   0:00 /sbin/syslogd -u syslog
root      4350  0.0  0.0   1868   540 ?        S    20:55   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4352  0.0  0.2   3160  2040 ?        Ss   20:55   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4371  0.0  0.1   5316  1020 ?        Ss   20:55   0:00 /usr/sbin/sshd
root      4390  0.0  0.1   6528  1344 ?        Ss   20:55   0:00 /usr/sbin/nmbd -D
root      4392  0.0  0.2  10152  2540 ?        Ss   20:55   0:00 /usr/sbin/smbd -D
daemon    4416  0.0  0.0   1980   420 ?        Ss   20:55   0:00 /usr/sbin/atd
root      4423  0.0  0.1  10152  1032 ?        S    20:55   0:00 /usr/sbin/smbd -D
root      4428  0.0  0.0   2100   768 ?        Ss   20:55   0:00 /usr/sbin/cron
root      4449  0.0  0.6  10412  6472 ?        Ss   20:55   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/web
root      4456  0.0  0.0   1716   508 tty1     Ss+  20:55   0:00 /sbin/getty 38400 tty1
root      4517  0.0  0.3  10476  3288 ?        S    20:59   0:01 /usr/sbin/smbd -D
root      4586  0.0  0.2   8056  2540 ?        Ss   21:08   0:00 sshd: rudeiota [priv]
rudeiota      4588  0.0  0.1   8056  1680 ?        R    21:08   0:00 sshd: rudeiota@pts/0
rudeiota      4589  0.0  0.3   5560  2968 pts/0    Rs   21:08   0:00 -bash
root      4628  0.0  0.2   8056  2400 ?        Ss   21:11   0:00 sshd: rudeiota [priv]
rudeiota      4630  0.0  0.1   8204  1672 ?        S    21:11   0:00 sshd: rudeiota@notty
rudeiota      4631  0.0  0.1   4572  1404 ?        Ss   21:11   0:00 /usr/lib/openssh/sftp-server
root      4632  0.0  0.2   8056  2500 ?        Ss   21:15   0:00 sshd: rudeiota [priv]
rudeiota      4634  0.0  0.1   8056  1556 ?        S    21:15   0:00 sshd: rudeiota@pts/1
rudeiota      4635  0.0  0.3   5560  2940 pts/1    Ss+  21:15   0:00 -bash
rudeiota      4676  0.0  0.4   7576  4624 pts/0    T    22:18   0:00 lynx google.com
```

Any ideas? Thanks.

---

### Post by RudeIota on 2009-07-13
On whim, I just upgraded my OpenSSH (old version available in the repository) with the latest version directly from their website. 5.2

For what it is worth, that didn't fix the problem.

I'd also like to mention that it isn't just typing - it's the refresh rate of everything. wget, for example, went from 0 to 100% when download a 1MB file... no progress in between. rtorrent is nearly unusable.

---

### Post by GoldenSun on 2009-07-13
This happens to me when I start deluge.  It's just using too much bandwidth.  When I'm up/down and ssh from offsite everything is very slow and I find myself having to use the command "killall deluge" so that it is useable.  

A good way to check this is to install a bandwidth monitor.
sudo aptitude install bwm-ng

---

### Post by RudeIota on 2009-07-14
> **GoldenSun said:**
> This happens to me when I start deluge.  It's just using too much bandwidth.
[QUOTE=RudeIota]Everything on my network is wired. I'm still able to transfer files via SMB from the server to the client at over 9MB/sec, so it doesn't appear to be a network issue (another possible cause of poor SSH responsiveness).[/QUOTE]
Thank you for the response, but this is not the issue.
[LIST]
[*]I'm getting 9MB/sec down through Samba
[*]This happens when **rtorrent is not running** or resident in memory
[*]I'm on a hardwired LAN and even while copying, running and downloading all sorts of stuff, I've never had this issue before
[/LIST]
```
 bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  |         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             eth0:           0.00 KB/s            0.00 KB/s            0.00 KB/s
  ------------------------------------------------------------------------------
            total:           0.00 KB/s            0.00 KB/s            0.00 KB/s
```

By the way, bmw-ng is impossibly slow and acts just rtorrent.

---

### Post by nothingspecial on 2009-07-14
I`ve been having this issue lately.

I have the same rtorrent.

It only seems to happen while running screen.

---

### Post by RudeIota on 2009-07-14
> **nothingspecial said:**
> It only seems to happen while running screen.Interesting. 

If you have this problem while connected remotely via Internet, a common reason is your upload might be set to high. You might want to look into limiting your upload well below your connection's max upload speed. Also, too many connections at once will choke most routers (Think: PeerXchange/DHT).

The slowness I'm experiencing happens immediately after I login with my user/pass. Unfortunately, screen is not running (and neither is rtorrent), but I usually do run rtorrent in screen.

---

### Post by RudeIota on 2009-07-20
I'm not a Linux pro, so I'd really like to get at the root of the problem instead of just 'solving' it by reinstalling ubuntu.

Pretty much everything I see on the net is related to a slow connection: that is not the issue here.

Anyone care to take a stab or have a suggestion as to where I might find a solution?

---

### Post by meditatingfrog on 2009-10-01
Did you get this solved yet?

---

### Post by Giblet5 on 2009-10-01
At the risk of sounding like a goof, what happens when you ```
sudo apt-get remove rtorrent --purge
```

Classic "If it hurts when you hit your thumb with a hammer..." logic.

You could also run iostat, top, and even System Monitor and get a pretty good idea of where the bottleneck is.

---

### Post by JudFromHud on 2010-03-09
I would like to know if anyone has a solution to this as I am having a similar problem.  The machine runs fine with either by itself.  Once I have rtorrent installed (not even running) and screen (byobu) activated the machine slows to a crawl once I log in.  I'm running 9.10 server 32bit and have installed libtorrent 0.12.5 and rtorrent 0.8.5.  The only difference is that it's not slow through ssh but rather when I log in directly.  Another thing to note is that the cpu is barely over 2%.

---

