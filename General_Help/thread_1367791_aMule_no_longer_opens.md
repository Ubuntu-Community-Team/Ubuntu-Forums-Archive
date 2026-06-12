---
title: "aMule no longer opens"
date: 2009-12-29
forum: General Help
---

### Post by peyre on 2009-12-29
It's a strange thing...I've been using aMule for a while now, off and on.  Then the other day, seemingly out of the blue, it stopped opening.  I click on Applications, Network, aMule, and--nothing.  Same happens if I navigate out to /usr/bin and double-click on aMule.  If I run ./amule from the Terminal window in that directory, it tells me there's already an instance of aMule running--but it doesn't show in top or in Gnome System Monitor.  Anyone have any ideas?

---

### Post by taurus on 2009-12-29
Why don't you kill the one already running in the background and start it again from a terminal to see what's wrong with it.

```
sudo killall amule
amule
```

---

### Post by peyre on 2009-12-29
Good idea!  Lemme try...

Wha...?  This is what happened:

leon@peyre:/usr/bin$ sudo killall amule
[sudo] password for leon: 
amule: no process found
leon@peyre:/usr/bin$ ./amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/leon/.aMule/muleLock)Raising current running instance.
leon@peyre:/usr/bin$

---

### Post by taurus on 2009-12-29
Post the output of this command.

```
ps -A
```
Otherwise, you can always log out and back in (or perhaps reboot).  Then run amule from a terminal.

---

### Post by peyre on 2009-12-29
Here it is:

leon@peyre:/usr/bin$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 kintegrityd/0
   16 ?        00:00:00 kintegrityd/1
   17 ?        00:00:00 kblockd/0
   18 ?        00:00:00 kblockd/1
   19 ?        00:00:00 kacpid
   20 ?        00:00:00 kacpi_notify
   21 ?        00:00:00 kacpi_hotplug
   22 ?        00:00:00 ata/0
   23 ?        00:00:00 ata/1
   24 ?        00:00:00 ata_aux
   25 ?        00:00:00 ksuspend_usbd
   26 ?        00:00:00 khubd
   27 ?        00:00:00 kseriod
   28 ?        00:00:00 kmmcd
   29 ?        00:00:00 bluetooth
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 pdflush
   33 ?        00:00:00 kswapd0
   34 ?        00:00:00 aio/0
   35 ?        00:00:00 aio/1
   36 ?        00:00:00 ecryptfs-kthrea
   37 ?        00:00:00 crypto/0
   38 ?        00:00:00 crypto/1
   42 ?        00:00:01 scsi_eh_0
   43 ?        00:00:00 scsi_eh_1
   45 ?        00:00:00 kstriped
   46 ?        00:00:00 kmpathd/0
   47 ?        00:00:00 kmpathd/1
   48 ?        00:00:00 kmpath_handlerd
   49 ?        00:00:00 ksnapd
   50 ?        00:00:00 kondemand/0
   51 ?        00:00:00 kondemand/1
   52 ?        00:00:00 kconservative/0
   53 ?        00:00:00 kconservative/1
   54 ?        00:00:00 krfcommd
  288 ?        00:00:00 scsi_eh_2
  289 ?        00:00:01 usb-storage
  361 ?        00:00:00 kjournald2
  422 ?        00:00:00 upstart-udev-br
  425 ?        00:00:00 udevd
  679 ?        00:00:00 dbus-daemon
  685 ?        00:00:00 dd
  687 ?        00:00:00 rsyslogd
  688 ?        00:00:00 hald
  689 ?        00:00:00 NetworkManager
  692 ?        00:00:00 avahi-daemon
  695 ?        00:00:00 avahi-daemon
  697 ?        00:00:00 modem-manager
  698 ?        00:00:00 console-kit-dae
  763 ?        00:00:00 hald-runner
  764 ?        00:00:00 kpsmoused
  800 ?        00:00:00 wpa_supplicant
  842 ?        00:00:00 hd-audio0
  982 ?        00:00:00 hald-addon-inpu
  985 ?        00:00:00 hald-addon-stor
  988 ?        00:00:00 hald-addon-cpuf
  989 ?        00:00:00 hald-addon-acpi
  992 ?        00:00:00 hald-addon-stor
  995 ?        00:00:00 hald-addon-stor
 1006 ?        00:00:00 hald-addon-stor
 1009 ?        00:00:00 hald-addon-stor
 1010 ?        00:00:00 hald-addon-stor
 1038 ?        00:00:00 hald-addon-stor
 1051 tty4     00:00:00 getty
 1054 tty5     00:00:00 getty
 1069 tty2     00:00:00 getty
 1071 tty3     00:00:00 getty
 1074 tty6     00:00:00 getty
 1087 ?        00:00:00 acpid
 1108 ?        00:00:00 cron
 1109 ?        00:00:00 atd
 1208 ?        00:00:00 nmbd
 1217 ?        00:00:00 smbd
 1218 ?        00:00:00 smbd
 1238 ?        00:00:00 winbindd
 1239 ?        00:00:00 winbindd
 1299 ?        00:00:00 cupsd
 1503 tty1     00:00:00 getty
 1526 ?        00:00:00 gdm-binary
 1533 ?        00:00:00 gdm-simple-slav
 1534 tty7     00:00:42 Xorg
 1598 ?        00:00:00 dbus-launch
 1616 ?        00:00:00 gdm-session-wor
 1650 ?        00:00:00 gnome-keyring-d
 1665 ?        00:00:00 sh
 1700 ?        00:00:00 ssh-agent
 1703 ?        00:00:00 dbus-daemon
 1704 ?        00:00:00 dbus-launch
 1715 ?        00:00:00 xfce4-session
 1717 ?        00:00:00 gconfd-2
 1719 ?        00:00:00 xfconfd
 1726 ?        00:00:00 gnome-screensav
 1728 ?        00:00:00 xfwm4
 1729 ?        00:00:00 xfsettingsd
 1732 ?        00:00:05 xfce4-panel
 1734 ?        00:00:00 xfce4-power-man
 1736 ?        00:00:00 notify-osd
 1738 ?        00:00:00 gam_server
 1739 ?        00:00:00 xfce4-settings-
 1745 ?        00:00:08 Thunar
 1746 ?        00:00:02 xfce4-menu-plug
 1747 ?        00:00:01 xfce4-places-pl
 1749 ?        00:00:00 gvfsd
 1752 ?        00:00:00 xfce4-mixer-plu
 1756 ?        00:00:01 pulseaudio
 1764 ?        00:00:00 audacious2
 1765 ?        00:05:58 firefox
 1766 ?        00:00:03 nautilus
 1772 ?        00:00:02 update-notifier
 1774 ?        00:00:00 gnome-volume-co
 1776 ?        00:00:00 python
 1779 ?        00:00:00 devkit-disks-da
 1780 ?        00:00:01 devkit-disks-da
 1783 ?        00:00:00 xfce4-volumed
 1791 ?        00:00:00 polkit-gnome-au
 1793 ?        00:00:00 nm-applet
 1795 ?        00:00:00 polkitd
 1799 ?        00:00:12 chrome
 1802 ?        00:00:00 xfce4-terminal
 1805 ?        00:00:00 chrome
 1807 ?        00:00:00 chrome
 1823 ?        00:00:00 gvfsd-trash
 1842 ?        00:00:00 gnome-pty-helpe
 1845 ?        00:00:00 gvfs-gdu-volume
 1847 ?        00:00:00 gvfsd-burn
 1851 ?        00:00:00 gvfs-gphoto2-vo
 1885 ?        00:00:02 xfdesktop
 1902 ?        00:00:00 gvfsd-metadata
 2137 ?        00:00:14 chrome
 2149 ?        00:00:26 exe
 2361 ?        00:00:00 udevd
 2362 ?        00:00:00 udevd
 2436 pts/1    00:00:00 bash
 2833 pts/1    00:00:00 ps

---

### Post by taurus on 2009-12-29
Maybe you want to remove the lock file in ~/.aMule/muleLock.

---

### Post by peyre on 2009-12-29
Whoa!  I had a reboot, and suddenly I'm able to open it now.  Maybe I needed to reboot after removing and reinstalling.

---

### Post by Logan 1229 on 2010-01-14
I'm having similar/same problem which started recently.  Amule started closing for unknown reason.  Previously solved problem using:
     [http://ubuntuforums.org/showthread.php?t=857986](http://ubuntuforums.org/showthread.php?t=857986)
But hasn't helped this time.  

  While troubleshooting, opened Amule using terminal & received:
Initialising aMule 2.2.4 using wxGTK2 v2.8.9
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/primary/.aMule/muleLock)Raising current running instance.

  Tried to kill thru terminal as suggested & got:
amule: no process killed

  Tried ps -A & got:
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
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
   22 ?        00:00:00 ata/1
   23 ?        00:00:00 ata_aux
   24 ?        00:00:00 ksuspend_usbd
   25 ?        00:00:00 khubd
   26 ?        00:00:00 kseriod
   27 ?        00:00:00 kmmcd
   28 ?        00:00:00 btaddconn
   29 ?        00:00:00 btdelconn
   30 ?        00:00:00 pdflush
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 kswapd0
   33 ?        00:00:00 aio/0
   34 ?        00:00:00 aio/1
   35 ?        00:00:00 ecryptfs-kthrea
   38 ?        00:00:00 scsi_eh_0
   39 ?        00:00:00 scsi_eh_1
   40 ?        00:00:00 scsi_eh_2
   41 ?        00:00:00 scsi_eh_3
   42 ?        00:00:00 scsi_eh_4
   43 ?        00:00:00 scsi_eh_5
   44 ?        00:00:00 scsi_eh_6
   45 ?        00:00:00 scsi_eh_7
   46 ?        00:00:00 kstriped
   47 ?        00:00:00 kmpathd/0
   48 ?        00:00:00 kmpathd/1
   49 ?        00:00:00 kmpath_handlerd
   50 ?        00:00:00 ksnapd
   51 ?        00:00:00 kondemand/0
   52 ?        00:00:00 kondemand/1
   53 ?        00:00:00 krfcommd
  767 ?        00:00:00 kjournald
  901 ?        00:00:00 udevd
 1655 ?        00:00:06 ath5k_pci
 2238 tty4     00:00:00 getty
 2239 tty5     00:00:00 getty
 2246 tty2     00:00:00 getty
 2247 tty3     00:00:00 getty
 2248 tty6     00:00:00 getty
 2319 ?        00:00:00 acpid
 2364 ?        00:00:00 syslogd
 2387 ?        00:00:00 dd
 2389 ?        00:00:00 klogd
 2412 ?        00:00:00 dbus-daemon
 2551 ?        00:00:00 hald
 2554 ?        00:00:00 console-kit-dae
 2617 ?        00:00:00 hald-runner
 2646 ?        00:00:00 hald-addon-inpu
 2683 ?        00:00:00 hald-addon-stor
 2699 ?        00:00:00 hald-addon-acpi
 2703 ?        00:00:00 bluetoothd
 2738 ?        00:00:00 gdm
 2741 ?        00:00:00 gdm
 2745 tty7     00:00:38 Xorg
 2767 ?        00:00:00 NetworkManager
 2778 ?        00:00:00 wpa_supplicant
 2784 ?        00:00:00 nm-system-setti
 2791 ?        00:00:00 avahi-daemon
 2792 ?        00:00:00 avahi-daemon
 2819 ?        00:00:00 cupsd
 2847 ?        00:00:00 system-tools-ba
 2920 ?        00:00:00 atd
 2948 ?        00:00:00 cron
 3055 tty1     00:00:00 getty
 3081 ?        00:00:00 gnome-keyring-d
 3093 ?        00:00:00 x-session-manag
 3149 ?        00:00:00 ssh-agent
 3152 ?        00:00:00 dbus-launch
 3153 ?        00:00:00 dbus-daemon
 3158 ?        00:00:01 pulseaudio
 3159 ?        00:00:00 gconf-helper
 3161 ?        00:00:00 gconfd-2
 3172 ?        00:00:00 seahorse-agent
 3175 ?        00:00:00 gvfsd
 3181 ?        00:00:00 gvfs-fuse-daemo
 3191 ?        00:00:00 gnome-settings-
 3197 ?        00:00:00 compiz
 3250 ?        00:00:05 compiz.real
 3251 ?        00:00:01 gnome-panel
 3252 ?        00:00:07 nautilus
 3254 ?        00:00:00 bonobo-activati
 3257 ?        00:00:00 update-notifier
 3260 ?        00:00:00 evolution-alarm
 3263 ?        00:00:00 nm-applet
 3266 ?        00:00:00 python
 3269 ?        00:00:00 bluetooth-apple
 3272 ?        00:00:00 gnome-power-man
 3275 ?        00:00:00 notify-osd
 3283 ?        00:00:00 gvfsd-trash
 3287 ?        00:00:00 trashapplet
 3290 ?        00:00:00 gvfs-hal-volume
 3292 ?        00:00:00 gvfs-gphoto2-vo
 3295 ?        00:00:00 fast-user-switc
 3299 ?        00:00:00 mixer_applet2
 3302 ?        00:00:00 indicator-apple
 3305 ?        00:00:00 sh
 3306 ?        00:00:00 compiz-decorato
 3308 ?        00:00:00 gtk-window-deco
 3311 ?        00:00:00 gvfsd-burn
 3353 ?        00:00:00 dhclient
 3364 ?        00:00:00 kjournald
 3459 ?        00:00:00 gnome-screensav
 3530 ?        00:00:24 gnome-system-mo
 3571 ?        00:00:17 firefox
 3723 ?        00:00:00 gnome-terminal
 3724 ?        00:00:00 gnome-pty-helpe
 3725 pts/0    00:00:00 bash
 3754 pts/0    00:00:00 ps

Restart did not solve problem though.

> **taurus said:**
> Maybe you want to remove the lock file in ~/.aMule/muleLock.

  Can you explain this statement please? Not sure what this file is for, or why/how to safely remove...

Found this explanation: 
  [http://wiki.amule.org/index.php/MuleLock_file](http://wiki.amule.org/index.php/MuleLock_file)
But doesn't solve the "closing" by itself problem.
Anyone have suggestions for that?

---

### Post by Bernabé on 2010-07-14
I had the same problem, I solved it making:
> cat .aMule/muleLock
This file contains the PID number of aMule, so now you can kill easily it:
> kill (PID number) without the brackets.
Finally, you can start aMule normally and it should work well.

---

### Post by peyre on 2010-07-14
Thanks!  I'll use that next time.

---

### Post by Logan 1229 on 2010-08-07
Curious.  I also will try next time (& post results) if happens again.  
  I did noticed Amule would start randomly working again.  I believe I had narrowed the problem down to the number of downloads in the download 'transfer file'.  There seems to be a sweet spot between 300-400 files (above 400 inceased chances of crashing).
  I have just upgraded to Lucid so we'll see how well it continues to work.
Thanks for feedback!

---

