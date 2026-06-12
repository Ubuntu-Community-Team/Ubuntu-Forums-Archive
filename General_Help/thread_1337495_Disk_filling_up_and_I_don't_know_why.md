---
title: "Disk filling up and I don't know why"
date: 2009-11-25
forum: General Help
---

### Post by cguy on 2009-11-25
my /home is on the / partition.

Yesterday I lost several Gigs and I have no idea what uses the disk space.

Today I freed 500MB (removed some of my files) since the computer was behaving really weird with no disk space.

Curiously, the disk fills up again.
I have 300 MB left as I write this post.

What is going on?

Using Karmic.

---

### Post by cguy on 2009-11-25
150MB free now...

---

### Post by cguy on 2009-11-25
zero :-|

Help!

---

### Post by ajgreeny on 2009-11-25
If you can now do anything at all with your machine let's see the output of 
```
df -h
sudo fdisk -l
```
in terminal, one line at a time.  This will show us the free disk space on the disk and the partitions on it as well.  It may also be worth looking to see how big the hidden .xsession-errors file in your home is. Occasionally this can grow at an exponential rate if there are major display problems.

---

### Post by drs305 on 2009-11-25
Here's a guide I wrote about Disk Space - how to find what's filling up a drive and how to solve it.

Usually it is a backup made to the system partition instead of to a backup partition, large log files or undeleted trash.

Community doc:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Original thread:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by cguy on 2009-11-25
```
george@george-desktop:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G   19G     0 100% /
udev                 1007M  268K 1007M   1% /dev
none                 1007M  440K 1007M   1% /dev/shm
none                 1007M  1.2M 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda2              16G  7.6G  6.7G  54% /media/sda2
/dev/sda3              19G   13G  4.7G  73% /media/sda3
/dev/sda4              96G   70G   26G  74% /media/sda4
/dev/sdb1              19G   18G  110M 100% /media/sdb1

```

```
george@george-desktop:/media$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079f50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612        4601    15984675   83  Linux
/dev/sda3            4602        7011    19358325   83  Linux
/dev/sda4            7012       19458    99968000    6  FAT16

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf621f621

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux

```
.xsession-errors is 3.6MB and has millions of lines saying
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)


```
george@george-desktop:/$ sudo find / -name '*' -size +1G
find: `/proc/4801/task/4801/fd/5': No such file or directory
find: `/proc/4801/task/4801/fdinfo/5': No such file or directory
find: `/proc/4801/fd/5': No such file or directory
find: `/proc/4801/fdinfo/5': No such file or directory
/media/sda2/matlab_iso/Matlab 7.7 2008b.zip
/media/sda3/poze/poze stagiu 2008.zip
/home/george/Documents/Windows XP.vdi
find: `/home/inginerie/.gvfs': Permission denied

```

```
george@george-desktop:/var/log$ sudo du -h /var/log
4.0K	/var/log/chkrootkit
1.1M	/var/log/cups
12K	/var/log/fsck
396K	/var/log/gdm
4.0K	/var/log/news
4.0K	/var/log/pure-ftpd
824K	/var/log/ConsoleKit
4.0K	/var/log/sysstat
4.0K	/var/log/speech-dispatcher
4.0K	/var/log/samba/cores/nmbd
4.0K	/var/log/samba/cores/smbd
4.0K	/var/log/samba/cores/winbindd
16K	/var/log/samba/cores
316K	/var/log/samba
148K	/var/log/apt
4.0K	/var/log/unattended-upgrades
4.0K	/var/log/apparmor
1.1M	/var/log/installer
48K	/var/log/dist-upgrade/20091118-2129
1.2M	/var/log/dist-upgrade
1.6G	/var/log

```
the top two files in /var/log:
708M -rw-r-----  1 syslog            adm  708M 2009-11-25 03:44 syslog.1
705M -rw-r-----  1 syslog            adm  705M 2009-11-25 21:00 user.log

I'm waiting for them to open. Will be reporting after a LONG time :D

---

### Post by ajgreeny on 2009-11-25
Can you tell us the size of your home folder (right click and choose properties), then we will know if the offending files filling your space are system or home files.

Also if you can and if 9.10 has it in the menu look at Disk Usage Analyser, which will show where the space is actually being used, ie which folders.

---

### Post by Divider on 2009-11-25
isn't this an irc exploit?

---

### Post by cguy on 2009-11-25
The only thing that is out of the place with my home folder is a huge, 575.6MB file named "root" in
/home/inginerie/.local/share/gvfs-metadata
filetype - unknown; nothing readable inside it as far as I can tell

[email]george@george-desktop:~/.local[/email]/share/gvfs-metadata$ file root
root: data


/var/log/user.log has an unmentionable number of lines saying
Nov 25 00:35:20 george-desktop pulseaudio[24041]: socket-server.c: accept():  Too many open files

Nov 25 00:35:58 george-desktop pulseaudio[24041]: alsa-sink.c: Error opening PCM device surround51:0: Too many open files

But these are from the other day, when I had the same problem.
No logs for today in user.log (weird, huh? could be because there was no disk space available, but for a good time there was some; nothing happened back then?)



syslog.1 also has data from the other day and nothing from today
Nov 25 03:38:02 george-desktop nullmailer[1612]: Sending failed:  Host not found
Nov 25 03:38:02 george-desktop nullmailer[1612]: Starting delivery: protocol: smtp host: mail. file: 1254351167.4340
Nov 25 03:38:02 george-desktop nullmailer[28550]: smtp: Failed: Connect failed
^^ LOTS of these three


Also, check the thread I opened yesterday and got no replies...
[http://ubuntuforums.org/showthread.php?t=1336671](http://ubuntuforums.org/showthread.php?t=1336671)
See that Log Viewer could not find many logs at one time. I tried again later and it worked -- can't tell if it was a weird behavior caused by no disk space.


How could it be an IRC exploit? I never used IRC on this system :-/

---

### Post by drs305 on 2009-11-25
I don't know if you looked closely at the "Disk Space" thread but one thing to do is to shut down all your apps and unmount every non-system partition. You can unmount them with:
```

sudo umount -a

```

The reason for doing this when you are trying to find out what is taking up space is that you may have data in a system folder (a large backup file, for instance) that would be hidden if something else is mounted *on top of it*.

With everything unmounted except the system partitions, run your commands again and see if any of them look particularly large. For instance, /mnt and /media should be very small once other partitions are unmounted.
```
sudo du -h --max-depth=1 / | sort
```

---

### Post by jrz on 2009-11-30
I'm having a somewhat similar problem after upgrading my IBM thinkpad R40 to 9.10, but my xsession-errors file is 1.4 GB, and my root file is only 504 bytes. In my case it appears to have something to do with a bug related to the video driver (ATI Radeon Mobility M6 LY), and several programs open with a corrupted video display, all the Open Office Org programs, the system monitor and Wicd Network manager. Do you have that problem as well? Each time I open one of those programs my xsession-errors file grows by leaps and bounds. I have 9.10 running on another system with no problems.

---

