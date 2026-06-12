---
title: "flash player installation problem"
date: 2009-12-26
forum: General Help
---

### Post by shariefbe on 2009-12-26
i am getting error when i install flash .deb package
i am getting the error status as
"Error: Conflicts with the installed package 'flashplugin-installer'"
what to do?

---

### Post by nerdy_kid on 2009-12-26
means that flash is already installed but if you still want to do it:
```

sudo apt-get purge flashplugin-installer

```
then install the .deb

---

### Post by shariefbe on 2009-12-26
i am gettg this error when i run that command
```

iqbal@iqbal-laptop:/etc/firefox-3.0$ sudo apt-get purge flashplugin-installer
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
iqbal@iqbal-laptop:/etc/firefox-3.0$ 

```

---

### Post by taurus on 2009-12-26
Do you have synaptic or software sources open?  Close it before you run the apt-get from a terminal.

---

### Post by shariefbe on 2009-12-26
No. i am using only terminal and tis browser. That all

---

### Post by taurus on 2009-12-26
There is something locking up your dpkg.  Look at the output of this command to see which one it is.

```
ps -A
```

---

### Post by shariefbe on 2009-12-26
i dont know how to see that. for your kind information see the output og that command and suggest me
```

iqbal@iqbal-laptop:/etc/firefox-3.0$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   12 ?        00:00:00 kstop/0
   13 ?        00:00:00 kstop/1
   14 ?        00:00:00 kintegrityd/0
   15 ?        00:00:00 kintegrityd/1
   16 ?        00:00:00 kblockd/0
   17 ?        00:00:00 kblockd/1
   18 ?        00:00:00 kacpid
   19 ?        00:00:00 kacpi_notify
   20 ?        00:00:00 cqueue
   21 ?        00:00:00 ata/0
   22 ?        00:00:01 ata/1
   23 ?        00:00:00 ata_aux
   24 ?        00:00:00 ksuspend_usbd
   25 ?        00:00:00 khubd
   26 ?        00:00:00 kseriod
   27 ?        00:00:00 kmmcd
   28 ?        00:00:00 btaddconn
   29 ?        00:00:00 btdelconn
   32 ?        00:00:03 kswapd0
   33 ?        00:00:00 aio/0
   34 ?        00:00:00 aio/1
   35 ?        00:00:00 ecryptfs-kthrea
   38 ?        00:00:00 scsi_eh_0
   39 ?        00:00:00 scsi_eh_1
   40 ?        00:00:00 scsi_eh_2
   41 ?        00:00:00 scsi_eh_3
   42 ?        00:00:03 scsi_eh_4
   43 ?        00:00:00 scsi_eh_5
   44 ?        00:00:00 kstriped
   45 ?        00:00:00 kmpathd/0
   46 ?        00:00:00 kmpathd/1
   47 ?        00:00:00 kmpath_handlerd
   48 ?        00:00:00 ksnapd
   49 ?        00:00:00 kondemand/0
   50 ?        00:00:00 kondemand/1
   51 ?        00:00:00 krfcommd
  729 ?        00:00:03 kjournald
  863 ?        00:00:00 udevd
 1518 ?        00:00:00 kpsmoused
 1568 ?        00:00:00 b43
 2165 tty4     00:00:00 getty
 2166 tty5     00:00:00 getty
 2170 tty2     00:00:00 getty
 2172 tty3     00:00:00 getty
 2174 tty6     00:00:00 getty
 2239 ?        00:00:00 acpid
 2284 ?        00:00:00 syslogd
 2307 ?        00:00:00 dd
 2309 ?        00:00:00 klogd
 2332 ?        00:00:07 dbus-daemon
 2371 ?        00:00:16 hald
 2374 ?        00:00:00 console-kit-dae
 2437 ?        00:00:05 hald-runner
 2467 ?        00:00:00 hald-addon-dell
 2468 ?        00:00:00 hald-addon-inpu
 2486 ?        00:00:00 hald-addon-gene
 2505 ?        00:00:00 hald-addon-cpuf
 2506 ?        00:00:00 hald-addon-acpi
 2507 ?        00:00:03 hald-addon-stor
 2529 ?        00:00:00 bluetoothd
 2570 ?        00:00:00 gdm
 2573 ?        00:00:00 gdm
 2577 tty7     00:14:58 Xorg
 2603 ?        00:00:04 NetworkManager
 2607 ?        00:00:00 wpa_supplicant
 2609 ?        00:00:00 nm-system-setti
 2628 ?        00:00:00 avahi-daemon
 2629 ?        00:00:00 avahi-daemon
 2664 ?        00:00:00 cupsd
 2692 ?        00:00:00 system-tools-ba
 2766 ?        00:00:00 atd
 2794 ?        00:00:00 cron
 2893 tty1     00:00:00 getty
 2918 ?        00:00:00 x-session-manag
 3020 ?        00:00:00 hald-addon-rfki
 3088 ?        00:00:00 ssh-agent
 3091 ?        00:00:00 dbus-launch
 3092 ?        00:00:00 dbus-daemon
 3098 ?        00:00:00 pulseaudio
 3099 ?        00:00:00 gconf-helper
 3101 ?        00:00:00 gconfd-2
 3110 ?        00:00:00 dhclient
 3116 ?        00:00:00 seahorse-agent
 3123 ?        00:00:05 gnome-settings-
 3125 ?        00:00:00 gnome-keyring-d
 3130 ?        00:00:00 gvfsd
 3137 ?        00:00:00 gvfs-fuse-daemo
 3141 ?        00:00:00 compiz
 3208 ?        00:00:59 compiz.real
 3210 ?        00:00:54 gnome-panel
 3272 ?        00:00:59 nautilus
 3274 ?        00:00:00 bonobo-activati
 3278 ?        00:00:00 bluetooth-apple
 3279 ?        00:00:00 nm-applet
 3281 ?        00:00:00 python
 3284 ?        00:00:00 evolution-alarm
 3293 ?        00:00:02 update-notifier
 3294 ?        00:00:01 gnome-power-man
 3297 ?        00:00:00 notify-osd
 3310 ?        00:00:00 trashapplet
 3326 ?        00:00:00 gvfs-hal-volume
 3330 ?        00:00:00 gvfs-gphoto2-vo
 3365 ?        00:00:02 gvfsd-trash
 3371 ?        00:00:00 fast-user-switc
 3374 ?        00:00:00 mixer_applet2
 3377 ?        00:00:00 indicator-apple
 3379 ?        00:00:00 sh
 3380 ?        00:00:00 compiz-decorato
 3382 ?        00:00:22 gtk-window-deco
 3387 ?        00:00:00 gvfsd-burn
 3536 ?        00:00:29 gnome-screensav
 5314 ?        00:00:21 gnome-terminal
 5318 ?        00:00:00 gnome-pty-helpe
 5319 pts/0    00:00:00 bash
 6479 pts/0    00:00:00 su
 6487 pts/0    00:00:00 bash
 6707 ?        00:00:00 pdflush
 7083 ?        00:00:00 pdflush
21851 pts/1    00:00:01 bash
22479 pts/0    00:00:00 vi
26403 pts/1    00:00:00 vim
26422 pts/1    00:00:00 vi
31202 pts/1    00:00:02 apt-get
31716 ?        00:00:47 opera
32009 pts/1    00:00:00 ps

```

---

### Post by taurus on 2009-12-26
Do you see a system update icon on the top right corner, probably next to a speaker or a network icon?

---

### Post by shariefbe on 2009-12-26
yes i got the solution. i closed all the terminals and i run this command"sudo apt-get purge flashplugin-installer" after that i installation process was fine.thanks a lot

---

