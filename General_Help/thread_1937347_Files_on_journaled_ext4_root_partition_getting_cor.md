---
title: "Files on journaled ext4 root partition getting corrupted (by Opera browser?)"
date: 2012-03-07
forum: General Help
---

### Post by JuhazOne on 2012-03-07
I seem to have a recurring problem with files on my partition getting corrupted. It happened today again, and my Opera browser lost its settings, Eclipse IDE complains about something missing and Konsole forgot which tabs it had open (but curiously Konsole didn't forget its config). It seems that when this problem happens it affects Opera most of the time and some other files/programs some of the time. I'm wondering if someone has had similar problems or knows what I could do to prevent my files from getting corrupted.

Back when I was using Kubuntu 11.04 on this laptop there was a problem with the graphics driver (I believe) that caused X to lock up sometimes several times a day. The only way for me to fix this was to keep the power button pressed down until the laptop powered down. This caused corrupted files several times, so in the end I set up a backup system for my most important files and also tried setting my root partition (ext4) to full journaling mode. A few weeks ago I did a full reinstall using Kubuntu 11.10 on a fresh ext4 partition.

I'm not sure, but it's possible that I had to force shut down my computer some time ago (but not during this week, and I last booted my computer up earlier today). The graphics problem has gone away, though, so it shouldn't be common for files to get corrupted. Besides, I'm still using full journaling mode, so I wouldn't expect a lot corrupted files.

What has happened, though, is that yesterday I left my laptop idle for a moment while it the power cord was unplugged. After a while the laptop went into a hibernate/power save/whatever mode. When I pressed the power button it came back nicely and I didn't notice anything funny. I also powered the laptop up and down earlier today without problems. It was only today in the evening that I powered the laptop up and encountered problems:

On the first try the screen was just blank and nothing seemed to be happening. I pressed ctrl+alt+del and got the Kubuntu logo and it seemed that the system will reboot itself cleanly. After the reboot I was warned about the root partition not being clean (or something like that). It asked me what to do so I told it to run fsck, it fixed problems and booted up, but I encountered the problems I mentioned at the top of this post. I don't know if I've lost more files than those related to Opera, Konsole or Eclipse.

I checked /var/log/syslog and found out that there was some kind of a problem when shutting down the system earlier today. The log said something about segfault and it had thousands of null characters on two different lines. Here's an excerpt:

> Mar  7 17:29:24 my_computer_name dhclient: DHCPREQUEST of 10.10.50.116 on wlan0 to 10.10.50.1 port 67
Mar  7 17:29:24 my_computer_name dhclient: DHCPACK of 10.10.50.116 from 10.10.50.1
Mar  7 17:29:24 my_computer_name dhclient: bound to 10.10.50.116 -- renewal in 1380 seconds.
Mar  7 17:32:50 my_computer_name kernel: [28220.725137] operapluginwrap[15383]: segfault at 101000012 ip 00007f67ccd67f40 sp 00007fffc7c036e8 error 4 in libgobject-2.0.so.0.3000.0[7f67ccd35000+4e000]
Mar  7 17:33:25 my_computer_name kernel: [28255.267259] operapluginwrap[18367] general protection ip:7f0c499d0f40 sp:7fff736f1af8 error:0 in libgobject-2.0.so.0.3000.0[7f0c4999e000+4e000]
**[1032 null characters, then on the same line:]**
.808853] init: tty2 main process (1127) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: [28367.809023] init: tty3 main process (1129) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: [28367.809205] init: tty6 main process (1136) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: [28367.809991] init: cron main process (1154) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: [28367.810274] init: irqbalance main process (1152) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: [28367.810444] init: tty1 main process (1870) killed by TERM signal
Mar  7 17:35:17 my_computer_name kernel: Kernel logging (proc) stopped.
Mar  7 17:35:17 my_computer_name rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1019" x-info="http://www.rsyslog.com"] exiting on signal 15.
**[3239 null characters, then on the same line:]**
Mar  7 22:04:05 my_computer_name kernel: imklog 5.8.1, log source = /proc/kmsg started.
Mar  7 22:04:05 my_computer_name rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1005" x-info="http://www.rsyslog.com"] start
Mar  7 22:04:05 my_computer_name rsyslogd: rsyslogd's groupid changed to 103
Mar  7 22:04:05 my_computer_name rsyslogd: rsyslogd's userid changed to 101

The syslog stuff suggest that Opera had a problem. Fine, it would explain why Opera seems to be often affected by these corrupted files, but how can a problem with Opera corrupt other files, too?


My /lost+found directory contains 30 files recovered today. I checked this using the command:
```
> ls -lA /lost+found/ | grep 2012-03-07 | wc -l
30
```

My way of putting the root partition into full journaling mode was to edit /etc/default/grub and check that I have a line saying:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **rootflags=data=journal**"

I think this works since this command indicates that /dev/sda1 is in journaled data mode:
```
> dmesg | grep mount
[    4.081139] EXT4-fs (sda1): mounted filesystem with journalled data mode. Opts: data=journal
[    5.497821] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.000275] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   20.883446] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```

I don't know what commit=0 means, but it may also have something to do with journaling:
```
> mount | grep sda1
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
```

I've been running apt-get dist-upgrade pretty often so I shouldn't have terribly old packages in my system. My running kernel is:
```
> uname -a
Linux my_computer_name 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```


I sometimes use sshfs to mount a directory over ssh. These mounts are unrelated to the corrupted files, however, so I wouldn't expect this to mess up with files on my local hard disk.

---

### Post by oldfred on 2012-03-07
You are not the only one it looks like.
But they say it is a Opera or Flash issue.

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/902375](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/902375)

[http://lists.opensuse.org/opensuse-bugs/2011-12/msg03066.html](http://lists.opensuse.org/opensuse-bugs/2011-12/msg03066.html)

Also if forcing shutdown, do not power down but use REISUB.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by JuhazOne on 2012-03-07
Thanks, I haven't tried REISUB and the mnemonics for it sound useful. I've usually tried alt+sysrq+k in order to kill X (or the TTY and X along with it), but often this hasn't worked so I've pressed the power button. I don't know if REISUB would have worked in these cases (I'm not sure what alt+sysrq+r does) but I'll definitely try in the future.

Yeah, the crash that I experienced today was probably somehow related to Opera or Flash. However, I still can't figure out how a crash by Opera would corrupt other files, too... I'm also not sure if it's normal that syslog would include a lot of null characters.

---

### Post by JuhazOne on 2012-03-08
The problem is serious. It apparently corrupted my MySQL database, too. I wasn't able to repair the tables so I had to rename /var/lib/mysql and let mysqld create a new directory in its place. This means that I lost all the data in the old database. (I also reinstalled mysql, but I'm not sure if that was necessary.)

(Yeah, it's a good idea to back up your database periodically. The database didn't contain any critical information, though, so I haven't been backing it up.)

---

