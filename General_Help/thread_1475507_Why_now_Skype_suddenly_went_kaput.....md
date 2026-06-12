---
title: "Why now? Skype suddenly went kaput...."
date: 2010-05-06
forum: General Help
---

### Post by josta7 on 2010-05-06
I'm using 10.04... I've been successfully using the newest version of Skype that they have listed on their website with my Logitech webcam and the hack I found on here somewhere: 
```
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
```
The last couple days it has seemed less stable than it used to be, crashing when it never used to...and today it crashed and now it won't come back, saying:
> 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
skype: pcm_null.c:130: snd_pcm_null_start: Assertion `null->state == SND_PCM_STATE_PREPARED' failed.
Aborted

I THINK it has an issue to do with the sound... I have to reassign it to use the ALSA sound instead of the Pulse Audio that I uninstalled? But I don't know how to do that.... Could anyone tell me if this guess is right & how to fix it? I'd really appreciate it.
:-k

---

### Post by powerofpi on 2010-05-06
Skype and I have gone round and round... As of version 2.1, it exclusively supports PulseAudio. My particular issue was that it thought my microphone channel was dual-channel rather than mono. I had to install pavucontrol and drag one of the two mic "channels" to zero volume, and then my mic worked perfectly with Skype 2.1 and Lucid. Of course this could have nothing to do with your problem :)

I would try uninstalling Skype, going to your home folder, hitting Ctrl-H, and deleting the hidden .pulse folder, rebooting, reinstalling Skype, and seeing if your problem is fixed.

---

### Post by tgalati4 on 2010-05-07
Sometimes pulseaudio balls up, especially when there are many things going on.  Too many dropped frames and pulseaudio will crash.

Try to restart it.  Close skype.  Open a terminal:

pulseaudio -k

Restart skype.

---

### Post by josta7 on 2010-05-07
OK! Thank you for your suggestion, I will try it out & report back.

---

### Post by josta7 on 2010-05-07
> **powerofpi said:**
> Skype and I have gone round and round... As of version 2.1, it exclusively supports PulseAudio. My particular issue was that it thought my microphone channel was dual-channel rather than mono. I had to install pavucontrol and drag one of the two mic "channels" to zero volume, and then my mic worked perfectly with Skype 2.1 and Lucid. Of course this could have nothing to do with your problem :)

I would try uninstalling Skype, going to your home folder, hitting Ctrl-H, and deleting the hidden .pulse folder, rebooting, reinstalling Skype, and seeing if your problem is fixed.


OK, well I tried this... got the same result as before. :neutral: Hmmm... I really don't want to mess with Pulse Audio if I can avoid it, it really doesn't agree with the rest of my setup (my soundcard is a VIA8227 built into the motherboard, it definitely likes ALSA better, from what I can tell). :-k

---

### Post by tgalati4 on 2010-05-07
pulseaudio is a sound server that uses ALSA to talk to your sound card.  It also allows mixing and volume control of each application.  So each application can send sound, at an appropriate volume level, at the same time and it will be mixed and put out to your sound card.

Removing pulseaudio can be done, but it can cause breakage because it is thoroughly embedded into the desktop environment.

Sometimes you have to reboot because you have a rogue process that is taking control of pulseaudio.  Sometimes you simply have to restart pulseaudio using the -k swich which really just kills the current instance.

Because you are using the V4L hack, it's possible that V4L is balled up, not pulse.  

Open a terminal:

ps -ef

ps -ef | grep v4l
ps -ef | grep V4L

sudo killall v4l     (or whatever the v4l task shows up as.)

---

### Post by josta7 on 2010-05-07
> **tgalati4 said:**
> pulseaudio is a sound server that uses ALSA to talk to your sound card.  It also allows mixing and volume control of each application.  So each application can send sound, at an appropriate volume level, at the same time and it will be mixed and put out to your sound card.

Removing pulseaudio can be done, but it can cause breakage because it is thoroughly embedded into the desktop environment.

Sometimes you have to reboot because you have a rogue process that is taking control of pulseaudio.  Sometimes you simply have to restart pulseaudio using the -k swich which really just kills the current instance.

Because you are using the V4L hack, it's possible that V4L is balled up, not pulse.  

Open a terminal:

ps -ef

ps -ef | grep v4l
ps -ef | grep V4L

sudo killall v4l     (or whatever the v4l task shows up as.)

OK - help me understand what's going on here... 

1st - can pulse audio get balled up if it's not even installed? B/c it's not... maybe Skype is getting stuck if it's trying to search for it. It DOES start; for 2 seconds, goes through the above, and then closes.

2nd -  what does the 
> ps -ef do?
It brings up this:
> UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 May06 ?        00:00:00 /sbin/init
root         2     0  0 May06 ?        00:00:00 [kthreadd]
root         3     2  0 May06 ?        00:00:00 [migration/0]
root         4     2  0 May06 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 May06 ?        00:00:00 [watchdog/0]
root         6     2  0 May06 ?        00:00:00 [events/0]
root         7     2  0 May06 ?        00:00:00 [cpuset]
root         8     2  0 May06 ?        00:00:00 [khelper]
root         9     2  0 May06 ?        00:00:00 [netns]
root        10     2  0 May06 ?        00:00:00 [async/mgr]
root        11     2  0 May06 ?        00:00:00 [pm]
root        12     2  0 May06 ?        00:00:00 [sync_supers]
root        13     2  0 May06 ?        00:00:00 [bdi-default]
root        14     2  0 May06 ?        00:00:00 [kintegrityd/0]
root        15     2  0 May06 ?        00:00:00 [kblockd/0]
root        16     2  0 May06 ?        00:00:00 [kacpid]
root        17     2  0 May06 ?        00:00:00 [kacpi_notify]
root        18     2  0 May06 ?        00:00:00 [kacpi_hotplug]
root        19     2  0 May06 ?        00:00:04 [ata/0]
root        20     2  0 May06 ?        00:00:00 [ata_aux]
root        21     2  0 May06 ?        00:00:00 [ksuspend_usbd]
root        22     2  0 May06 ?        00:00:00 [khubd]
root        23     2  0 May06 ?        00:00:00 [kseriod]
root        24     2  0 May06 ?        00:00:00 [kmmcd]
root        27     2  0 May06 ?        00:00:00 [khungtaskd]
root        28     2  0 May06 ?        00:00:00 [kswapd0]
root        29     2  0 May06 ?        00:00:00 [ksmd]
root        30     2  0 May06 ?        00:00:00 [aio/0]
root        31     2  0 May06 ?        00:00:00 [ecryptfs-kthrea]
root        32     2  0 May06 ?        00:00:00 [crypto/0]
root        36     2  0 May06 ?        00:00:00 [kstriped]
root        37     2  0 May06 ?        00:00:00 [kmpathd/0]
root        38     2  0 May06 ?        00:00:00 [kmpath_handlerd]
root        39     2  0 May06 ?        00:00:00 [ksnapd]
root        40     2  0 May06 ?        00:00:00 [kondemand/0]
root        41     2  0 May06 ?        00:00:00 [kconservative/0]
root       220     2  0 May06 ?        00:00:00 [scsi_eh_0]
root       221     2  0 May06 ?        00:00:00 [khpsbpkt]
root       222     2  0 May06 ?        00:00:00 [scsi_eh_1]
root       223     2  0 May06 ?        00:00:00 [scsi_eh_2]
root       224     2  0 May06 ?        00:00:00 [scsi_eh_3]
root       228     2  0 May06 ?        00:00:00 [knodemgrd_0]
root       234     2  0 May06 ?        00:00:00 [usbhid_resumer]
root       260     2  0 May06 ?        00:00:02 [jbd2/sda1-8]
root       261     2  0 May06 ?        00:00:00 [ext4-dio-unwrit]
root       292     2  0 May06 ?        00:00:00 [flush-8:0]
root       322     1  0 May06 ?        00:00:00 upstart-udev-bridge --daemon
root       324     1  0 May06 ?        00:00:00 udevd --daemon
root       554     2  0 May06 ?        00:00:00 [kpsmoused]
root       569     2  0 May06 ?        00:00:00 [scsi_eh_4]
root       579     2  0 May06 ?        00:00:00 [usb-storage]
root       652     2  0 May06 ?        00:00:00 [radeon/0]
root       653     2  0 May06 ?        00:00:00 [ttm_swap]
root       681   324  0 May06 ?        00:00:00 udevd --daemon
root       689   324  0 May06 ?        00:00:00 udevd --daemon
root       703     2  0 May06 ?        00:00:00 [kgameportd]
syslog     710     1  0 May06 ?        00:00:00 rsyslogd -c4
root       726     2  0 May06 ?        00:00:00 [phy0]
102        729     1  0 May06 ?        00:00:00 dbus-daemon --system --fork
avahi      748     1  0 May06 ?        00:00:00 avahi-daemon: registering [Grizz
avahi      752   748  0 May06 ?        00:00:00 avahi-daemon: chroot helper
root       816     1  0 May06 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       822     1  0 May06 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       829     1  0 May06 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       831     1  0 May06 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       835     1  0 May06 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       838     1  0 May06 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root       839     1  0 May06 ?        00:00:02 gdm-binary
root       841     1  0 May06 ?        00:00:00 cron
daemon     842     1  0 May06 ?        00:00:00 atd
root       867     1  0 May06 ?        00:00:00 /usr/sbin/console-kit-daemon --n
root       937   839  0 May06 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
nobody     957     1  0 May06 ?        00:00:06 /usr/games/wesnothd
root       982     1  0 May06 ?        00:00:00 /usr/sbin/winbindd
root       987   937  2 May06 tty7     00:30:58 /usr/bin/X :0 -nr -verbose -auth
root       999   982  0 May06 ?        00:00:00 /usr/sbin/winbindd
root      1007     1  0 May06 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root      1099   937  0 May06 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
root      1116     1  0 May06 tty1     00:00:00 /sbin/getty -8 38400 tty1
josta     1123  1099  0 May06 ?        00:00:01 gnome-session
root      1141     1  0 May06 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /
josta     1190  1123  0 May06 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
josta     1193     1  0 May06 ?        00:00:00 /usr/bin/dbus-launch --exit-with
josta     1196     1  0 May06 ?        00:00:20 /bin/dbus-daemon --fork --print-
josta     1225     1  0 May06 ?        00:00:15 /usr/lib/libgconf2-4/gconfd-2
josta     1248     1  0 May06 ?        00:00:00 gnome-keyring-daemon --start --c
josta     1251     1  0 May06 ?        00:00:32 /usr/lib/gnome-settings-daemon/g
josta     1253     1  0 May06 ?        00:00:00 /usr/lib/gvfs/gvfsd
josta     1258     1  0 May06 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
josta     1262  1123  0 May06 ?        00:02:34 compiz --sm-client-id 10761b8ad4
root      1275     1  0 May06 ?        00:00:01 /usr/lib/udisks/udisks-daemon
josta     1276  1123  0 May06 ?        00:00:57 avant-window-navigator --startup
josta     1277  1123  0 May06 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
josta     1279  1123  0 May06 ?        00:00:00 python /usr/share/screenlets-man
root      1280  1275  0 May06 ?        00:00:05 udisks-daemon: polling /dev/sdc 
josta     1281  1123  0 May06 ?        00:00:06 gnome-panel --sm-client-id 10947
josta     1282  1123  0 May06 ?        00:00:02 gnome-terminal --sm-client-id 10
josta     1283  1123  0 May06 ?        00:00:03 mono /usr/lib/tomboy/Tomboy.exe
josta     1284  1123  4 May06 ?        00:47:20 nautilus --sm-client-id 10947de0
josta     1285  1123  0 May06 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.3/f
josta     1288  1123  3 May06 ?        00:39:55 wally -session 104261fecd4ca41bc
josta     1292  1123  0 May06 ?        00:02:22 pidgin --session 104261fecd4ca41
root      1298     1  0 May06 ?        00:00:00 /usr/lib/policykit-1/polkitd
josta     1311  1285  0 May06 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.3/r
josta     1314  1123  0 May06 ?        00:00:01 gnome-power-manager
josta     1316  1123  0 May06 ?        00:00:00 bluetooth-applet
josta     1323  1311  4 May06 ?        00:45:38 /usr/lib/firefox-3.6.3/firefox-b
root      1325     1  0 May06 ?        00:00:00 /usr/lib/upower/upowerd
josta     1363     1  0 May06 ?        00:00:00 /usr/lib/bonobo-activation/bonob
josta     1371     1  0 May06 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
josta     1377     1  0 May06 ?        00:00:34 /usr/lib/gnome-netstatus/gnome-n
josta     1378     1  0 May06 ?        00:00:22 /usr/lib/gnome-applets/multiload
107       1381     1  0 May06 ?        00:00:00 /usr/sbin/hald
root      1382  1381  0 May06 ?        00:00:00 hald-runner
josta     1408  1262  0 May06 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
root      1409  1382  0 May06 ?        00:00:00 hald-addon-input: Listening on /
josta     1410  1408  0 May06 ?        00:00:02 /usr/bin/gtk-window-decorator
root      1411  1382  0 May06 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-k
root      1428  1382  0 May06 ?        00:00:13 hald-addon-storage: polling /dev
root      1431  1382  0 May06 ?        00:00:00 hald-addon-storage: polling /dev
107       1434  1382  0 May06 ?        00:00:00 hald-addon-acpi: listening on ac
josta     1435  1282  0 May06 ?        00:00:00 gnome-pty-helper
josta     1436  1282  0 May06 pts/0    00:00:00 bash
josta     1459     1  0 May06 ?        00:00:00 gnome-screensaver
josta     1460  1276  0 May06 ?        00:00:06 awn-applet -p /usr/share/avant-w
josta     1462  1276  0 May06 ?        00:00:03 awn-applet -p /usr/share/avant-w
josta     1463  1276  0 May06 ?        00:00:06 awn-applet -p /usr/share/avant-w
josta     1464  1276  0 May06 ?        00:00:00 awn-applet -p /usr/share/avant-w
josta     1465  1276  0 May06 ?        00:00:00 python /usr/share/avant-window-n
josta     1466  1276  0 May06 ?        00:00:01 awn-applet -p /usr/share/avant-w
josta     1467  1276  0 May06 ?        00:00:01 awn-applet -p /usr/share/avant-w
josta     1468  1276  0 May06 ?        00:00:00 awn-applet -p /usr/share/avant-w
josta     1469  1276  0 May06 ?        00:00:10 python /usr/share/avant-window-n
josta     1470  1276  0 May06 ?        00:00:00 python /usr/share/avant-window-n
josta     1476     1  0 May06 ?        00:00:01 /usr/lib/gnome-panel/clock-apple
josta     1477     1  0 May06 ?        00:00:00 /usr/lib/gnome-applets/gweather-
josta     1486  1123  0 May06 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-
josta     1553     1  0 May06 ?        00:00:01 /usr/lib/gvfs/gvfs-afc-volume-mo
josta     1556     1  0 May06 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
josta     1568     1  0 May06 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
josta     1589  1123  0 May06 ?        00:00:13 python /usr/share/system-config-
josta     1654     1  0 May06 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
josta     1674  1123  0 May06 ?        00:00:00 update-notifier
josta     2352     1  0 00:08 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
root      2820     1  0 00:29 pts/0    00:00:00 dbus-launch --autolaunch 87a91ec
root      2821     1  0 00:29 ?        00:00:00 /bin/dbus-daemon --fork --print-
root     10806     1  0 08:03 ?        00:00:00 /usr/bin/python /usr/lib/system-
josta    19430  1436  0 17:31 pts/0    00:00:00 ps -ef


and then with each grep
josta    19436  1436  0 17:31 pts/0    00:00:00 grep --color=auto [COLOR="Red"]v4l[/COLOR]
josta    19445  1436  0 17:32 pts/0    00:00:00 grep --color=auto [COLOR="Red"]V4L[/COLOR]

sudo killall V4L & it told me no process found... did I do any of that wrong? I'm still so new at all of this!:-?

---

### Post by no2498 on 2010-05-08
from what i have been seeing all webcms use v4l2 
ubuntu has put the 2 together v4l and v4l2
and give it to cheese to maintain 

look at how this looks
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

is 1 in the package manager v4l/so/v4l2/so
some thing like that

---

