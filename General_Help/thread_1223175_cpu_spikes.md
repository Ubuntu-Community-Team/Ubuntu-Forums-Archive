---
title: "cpu spikes"
date: 2009-07-25
forum: General Help
---

### Post by Jesten on 2009-07-25
i just installed 9.04 on a dell b120. about every ten sec my cpu usage spikes up to about 60% then back down to 20%. my buddy that got me on ubuntu said there was a command to run where u can see that but he cant remember it. i do have a lot of crap running and not knowing what they are for the most part. can i get a little help. cant seem to find a way to make this thing run smoother.

---

### Post by masterkoppa on 2009-07-25
The command your friend is probably refereing to is: ```
top
```

As for your problem could you open up a terminal and post the result of the following command: ```
ps -e
```

This will help on diagnosing why your system is running this way.

---

### Post by dlmarti on 2009-07-25
gnome-system-monitor is another good one to run

---

### Post by Jesten on 2009-07-25
jesten@jesten-laptop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:03 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
    8 ?        00:00:00 kstop/0
    9 ?        00:00:00 kintegrityd/0
   10 ?        00:00:00 kblockd/0
   11 ?        00:00:00 kacpid
   12 ?        00:00:00 kacpi_notify
   13 ?        00:00:00 cqueue
   14 ?        00:00:02 ata/0
   15 ?        00:00:00 ata_aux
   16 ?        00:00:00 ksuspend_usbd
   17 ?        00:00:00 khubd
   18 ?        00:00:00 kseriod
   19 ?        00:00:00 kmmcd
   20 ?        00:00:00 btaddconn
   21 ?        00:00:00 btdelconn
   24 ?        00:00:18 kswapd0
   25 ?        00:00:00 aio/0
   26 ?        00:00:00 ecryptfs-kthrea
   29 ?        00:00:01 scsi_eh_0
   30 ?        00:00:00 scsi_eh_1
   31 ?        00:00:00 kstriped
   32 ?        00:00:00 kmpathd/0
   33 ?        00:00:00 kmpath_handlerd
   34 ?        00:00:00 ksnapd
   35 ?        00:00:00 kondemand/0
   36 ?        00:00:00 krfcommd
  686 ?        00:00:27 kjournald
  820 ?        00:00:00 udevd
 1403 ?        00:00:00 kpsmoused
 1473 ?        00:00:21 b43
 2023 ?        00:00:00 dhclient
 2078 tty4     00:00:00 getty
 2079 tty5     00:00:00 getty
 2085 tty2     00:00:00 getty
 2087 tty3     00:00:00 getty
 2088 tty6     00:00:00 getty
 2152 ?        00:00:00 acpid
 2197 ?        00:00:00 syslogd
 2220 ?        00:00:00 dd
 2222 ?        00:00:00 klogd
 2245 ?        00:00:52 dbus-daemon
 2284 ?        00:01:26 hald
 2287 ?        00:00:03 console-kit-dae
 2350 ?        00:00:19 hald-runner
 2380 ?        00:00:00 hald-addon-dell
 2385 ?        00:00:00 hald-addon-inpu
 2422 ?        00:00:07 hald-addon-stor
 2426 ?        00:00:00 hald-addon-acpi
 2446 ?        00:00:00 bluetoothd
 2479 ?        00:00:00 gdm
 2482 ?        00:00:00 gdm
 2484 ?        00:04:40 firefox
 2486 tty7     00:30:05 Xorg
 2508 ?        00:00:41 NetworkManager
 2512 ?        00:00:01 wpa_supplicant
 2514 ?        00:00:00 nm-system-setti
 2534 ?        00:00:00 avahi-daemon
 2537 ?        00:00:00 avahi-daemon
 2564 ?        00:00:00 cupsd
 2592 ?        00:00:00 system-tools-ba
 2666 ?        00:00:00 atd
 2694 ?        00:00:00 cron
 2793 tty1     00:00:00 getty
 2809 ?        00:00:00 hald-addon-rfki
 2815 ?        00:00:00 ipolldevd
 2852 ?        00:00:00 hald-addon-leds
 3057 ?        00:00:00 gnome-keyring-d
 3072 ?        00:00:01 x-session-manag
 3182 ?        00:00:00 ssh-agent
 3185 ?        00:00:00 dbus-launch
 3186 ?        00:00:01 dbus-daemon
 3191 ?        00:01:07 pulseaudio
 3192 ?        00:00:00 gconf-helper
 3194 ?        00:00:11 gconfd-2
 3205 ?        00:00:00 seahorse-agent
 3208 ?        00:00:00 gvfsd
 3213 ?        00:00:10 gnome-settings-
 3218 ?        00:00:00 gvfs-fuse-daemo
 3233 ?        00:00:00 compiz
 3296 ?        00:04:01 compiz.real
 3297 ?        00:01:07 gnome-panel
 3298 ?        00:00:29 nautilus
 3300 ?        00:00:00 bonobo-activati
 3303 ?        00:00:00 evolution-alarm
 3313 ?        00:00:00 python
 3315 ?        00:00:02 update-notifier
 3316 ?        00:00:42 nm-applet
 3321 ?        00:00:04 notify-osd
 3322 ?        00:00:05 gnome-power-man
 3330 ?        00:00:10 gvfsd-trash
 3337 ?        00:00:00 trashapplet
 3393 ?        00:00:00 gvfs-hal-volume
 3395 ?        00:00:00 gvfs-gphoto2-vo
 3398 ?        00:00:00 sh
 3399 ?        00:00:00 compiz-decorato
 3401 ?        00:00:37 gtk-window-deco
 3406 ?        00:00:00 gvfsd-burn
 3410 ?        00:00:00 fast-user-switc
 3413 ?        00:00:00 mixer_applet2
 3416 ?        00:00:00 indicator-apple
 3528 ?        00:00:30 gnome-screensav
 3536 ?        00:00:00 evolution-data-
 3540 ?        00:00:00 evolution-excha
 3604 ?        00:00:00 gvfsd-http
 3883 ?        00:00:00 pdflush
16253 ?        00:00:08 transmission
18337 ?        00:00:00 gedit
18339 ?        00:00:00 gnome-terminal
18340 ?        00:00:00 gnome-pty-helpe
18341 pts/0    00:00:00 bash
18374 pts/0    00:00:00 ps
27724 ?        00:00:00 pdflush
jesten@jesten-laptop:~$

---

### Post by fanboy on 2009-07-26
I just noticed the same problem. I, however, have been running ubuntu for quite a long time, and haven't seen the problem before. So it seem to me that it's one of the latest updates that has caused this problems.

So it seems to be the halrunner that causes it. It fires ut the hal-system-smbios every now and then to poll some driver. Not sure which yet. The reason why you ps command doesn't show it is that you have to run the command exactly at cpu peak. I used top and setting the update to 1 second (hit the 's'). Then I could see the hal-system-smbios on the top of cpu usage every 5-10 seconds or so.

My computer is an old dell c640 laptop (2.4 Ghz, 512 Meg).

---

### Post by Jesten on 2009-07-26
ive tried to capture it. but i think there is a slight delay on the graph due to the cpu spike. whatever it is its annoying

---

### Post by fanboy on 2009-07-27
Seems like a lot of other pepole have the same problem:
[http://ubuntuforums.org/showthread.php?p=7549951#post7549951](http://ubuntuforums.org/showthread.php?p=7549951#post7549951)

The workaround is currently to downgrade hal:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/394663](https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/394663)

I did, and the peak is now gone :)

---

### Post by Jesten on 2009-07-29
wow that fixed it and the post had nothing to do with their cpu's spiking. thanks for the fix my laptop smoothed out some.

---

### Post by Jesten on 2009-07-30
ok that fixed my cpu spike problem but now im having trouble with my wireless staying connected to my wireless router. it just drops and takes forever to reconnect. i re-upgraded hal and now my wireless works fine but the spikes are back. guess ill have to wait for an update to the hal that will keep my wireless the same but fix my spikes

---

