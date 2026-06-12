---
title: "mount : / is busy, because of lightdm"
date: 2012-06-22
forum: General Help
---

### Post by blitzter47 on 2012-06-22
Hello,

I have Ubuntu 12.04
When I do shutdown/reboot normally, I got, at the end, the error
```
...
**mount : / is busy**
* Will now halt 
```Then when Ubuntu boots, shell indicates that there's a recovery on hard drive where Ubuntu system resides:
```
[B][    7.252288] EXT4-fs (sdb5): INFO: recovery required on readonly filesystem
[    7.252353] EXT4-fs (sdb5): write access will be enabled during recovery
[   11.201583] EXT4-fs (sdb5): recovery complete[/B]
[   11.203425] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)

```
But, if I stop *lightdm* through Terminal before shutdown/reboot, the error messages disappear.
So in terminal:
```
sudo stop lightdm
```then log in through tty for entering shutdown/reboot command, the "mount : / is busy" error disappears before powering computer off, and booting Ubuntu doesn't have to do recovery.

I suppose that there's permission problem for terminating *lightdm* process during shutdown/reboot process or something wrong while terminating *lightdm* process (and maybe child processes also)

How to investigate/debug shutdown process step by step or solve permission problem while terminating processes? Do you have any other idea?

Thanks.
By the way, to bypass this error, I used Terminal or created a script to execute the following commands for shutdowns and reboots:
```
sudo stop lightdm & sudo reboot
sudo stop lightdm & sudo shutdown -h now
```

---

### Post by blitzter47 on 2012-07-28
Fixed.

**_[SIZE=4]Summary[/SIZE]_**
It seems that there's a root's abnormal process (in my case) "***/sbin/plymouthd --mode=shutdown***" that doesn't terminate at all and is still active while shutting down/rebooting, causing unclean unmount. But if I manually terminate lightdm (or gdm) first, then reboot, system unmount will be clean, without problem.

_[SIZE=3]**Of course, it can be not only *plymouthd*, but also any other application/process that hangs (eg. mysql, apache, etc.) Just try manual diagnostic by yourself in "Methodology" section to see what's wrong.**[/SIZE]_

_**[SIZE=4]Symptoms[/SIZE]**_
When shutting down/rebooting, (without *"splash*", nor "*quiet*" parameters in *grub*), in console, it displays
> [...]
mount: / is busy
* Will now haltThen when booting Ubuntu (without *"splash*," nor "*quiet*" parameters in *grub*), it displays recovery message:
> [    7.252288] EXT4-fs (sdb5): INFO: recovery required on readonly filesystem
[    7.252353] EXT4-fs (sdb5): write access will be enabled during recovery
[   11.201583] EXT4-fs (sdb5): recovery complete
[   11.203425] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)**_[SIZE=4]Methodology[/SIZE]_**
The source of problem is known by creating bash script manually, containing code:```
#! /bin/sh

ps -Af >> process.log
```executed during reboot (or shut down), in /etc/rc6.d (reboot) directory, placed before *"S60umountroot*" script file (in numerical order). After reboot, *"process.log"*  file is created in hard drive root / directory, which will log the problematic "***/sbin/plymouthd --mode=shutdown***" process, that is not supposed to be present, at the right side, at the end of file, like this (in bold):
> UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 00:28 ?        00:00:01 /sbin/init
root         2     0  0 00:28 ?        00:00:00 [kthreadd]
root         3     2  0 00:28 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 00:28 ?        00:00:00 [kworker/u:0]
root         6     2  0 00:28 ?        00:00:00 [migration/0]
root         7     2  0 00:28 ?        00:00:00 [watchdog/0]
root         8     2  0 00:28 ?        00:00:00 [cpuset]
root         9     2  0 00:28 ?        00:00:00 [khelper]
root        10     2  0 00:28 ?        00:00:00 [kdevtmpfs]
root        11     2  0 00:28 ?        00:00:00 [netns]
root        12     2  0 00:28 ?        00:00:00 [sync_supers]
root        13     2  0 00:28 ?        00:00:00 [bdi-default]
root        14     2  0 00:28 ?        00:00:00 [kintegrityd]
root        15     2  0 00:28 ?        00:00:00 [kblockd]
root        16     2  0 00:28 ?        00:00:00 [ata_sff]
root        17     2  0 00:28 ?        00:00:00 [khubd]
root        18     2  0 00:28 ?        00:00:00 [md]
root        19     2  0 00:28 ?        00:00:00 [kworker/u:1]
root        20     2  0 00:28 ?        00:00:00 [kworker/0:1]
root        21     2  0 00:28 ?        00:00:00 [khungtaskd]
root        22     2  0 00:28 ?        00:00:00 [kswapd0]
root        23     2  0 00:28 ?        00:00:00 [ksmd]
root        24     2  0 00:28 ?        00:00:00 [khugepaged]
root        25     2  0 00:28 ?        00:00:00 [fsnotify_mark]
root        26     2  0 00:28 ?        00:00:00 [ecryptfs-kthrea]
root        27     2  0 00:28 ?        00:00:00 [crypto]
root        35     2  0 00:28 ?        00:00:00 [kthrotld]
root        37     2  0 00:28 ?        00:00:00 [scsi_eh_0]
root        38     2  0 00:28 ?        00:00:00 [scsi_eh_1]
root        41     2  0 00:28 ?        00:00:00 [kworker/0:2]
root        61     2  0 00:28 ?        00:00:00 [devfreq_wq]
root       202     2  0 00:28 ?        00:00:00 [ttm_swap]
root       252     2  0 00:28 ?        00:00:00 [jbd2/sda7-8]
root       253     2  0 00:28 ?        00:00:00 [ext4-dio-unwrit]
root       773     2  0 00:28 ?        00:00:00 [krfcommd]
root      1139     2  0 00:28 ?        00:00:00 [flush-8:0]
root      5886     2  0 00:33 ?        00:00:00 [kworker/0:0]
root      8221     1  0 00:35 ?        00:00:00 /bin/sh /etc/init.d/rc 6
**root      8255     1  3 00:35 ?        00:00:00 /sbin/plymouthd --mode=shutdown** _*#should not be present for normal shut down/reboot*_
root      8467  8221  0 00:35 ?        00:00:00 /bin/sh /etc/rc6.d/S60perso-script stop
root      8471  8467  0 00:35 ?        00:00:00 ps -AfIf you would like to check that yourself  **(all with sudo)**:

[LIST]
[*] Do  following renaming  in /etc/rc6.d (reboot) directory:[U][B]
##original filename ----->--------renamed to --------->------customized filename##
S60[/B][/U] _umountroot-------------->------renamed to ---------->---------**S61**umountroot_
[/LIST]
 
[LIST]
[*] Then create bash script (containing above code) (with _executable attribute_) before "***S61**umountroot*" by naming it ***"S60**perso-script"* in same directory. 

By the way, our script is after "*S59cryptdisks-early" *file* (according to S## order number)*.
[*]Then reboot and look at *process.log* file in hard drive root /, which will contain "***/sbin/plymouthd --mode=shutdown***" at the right side, at the end of file, like above example.
[/LIST]
 
[U]**[SIZE=4] My solutions[/SIZE]**[SIZE=4] (need  sudo)[/SIZE][B][SIZE=4]
[/SIZE][/B][/U] The best way, I think, is to kill *plymouthd* just before system is unmounting.

So still with the early manually created bash script ***"****S60**perso-script"* in /etc/rc6.d (reboot) directory, replace the file content by :
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:
# Required-Stop:
# Should-Stop:       
# Default-Start:
# Default-Stop:      0 6
# Short-Description: Kill freezing plymouthd
### END INIT INFO

PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

case "$1" in
  start)
    
    killall -9 plymouthd
    
    ;;
  restart|reload|force-reload)
    
    ;;
  stop)
    
    killall -9 plymouthd
    
    ;;
  *)

    ;;
esac

:

```Then do same thing in /etc/rc0.d (shut down) directory (with renaming **"S60**umountroot" to "**S61**umountroot"). Then you can  create symbolic link or copy our script from /etc/rc6.d to /etc/rc0.d.

So same file, with same content, same filename and executable attribute, in /etc/rc6.d and /etc/rc0.d.
So killing *plymouthd* command will execute not only for reboots, but also for shut downs.

Alternative solution (which can unfortunately add delay displaying shut down splash screen or console message):
To avoid computer to invoke *plymouthd* during shut down/reboot. just edit (with sudo) /etc/init/plymouth.conf file by adding # to comment the following line (line 21):
```
***Final result file***
[...]
21|        **#**exec /sbin/plymouthd --mode=shutdown
```Then save.

---

