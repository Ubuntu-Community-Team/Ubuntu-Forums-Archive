---
title: "Can't find application manager to stop"
date: 2010-06-27
forum: General Help
---

### Post by pumpkinpapa on 2010-06-27
Using Jaunty and trying to install a 56k modem driver with gdebi but when I go to install it tells me I have to close all other application managers. I cannot find any other application managers running in system monitor. Synaptic and update manager are both off at this point.

I'm in a dual boot with xp. Something tells me I should have bought that USR modem with the native Linux driver rather than the cheaper Aopen unit :)

I will be upgrading to Lucid in the coming weeks but would like to resolve this beforehand if possible.

---

### Post by mikewhatever on 2010-06-27
How about the Add/Remove program, aka gnome-app-install? Is it open?

---

### Post by pumpkinpapa on 2010-06-27
Nope, nothing is running. I'm going to try making a screenshot or a list of running apps and services.

---

### Post by mikewhatever on 2010-06-27
You can just post the terminal output of **ps aux**.

---

### Post by pumpkinpapa on 2010-06-27
Here is the output. How does one stop entries using the terminal?

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

root         1  0.4  0.0   2844  1692 ?        Ss   17:03   0:01 /sbin/init

root         2  0.0  0.0      0     0 ?        S<   17:03   0:00 [kthreadd]

root         3  0.0  0.0      0     0 ?        S<   17:03   0:00 [migration/0]

root         4  0.0  0.0      0     0 ?        S<   17:03   0:00 [ksoftirqd/0]

root         5  0.0  0.0      0     0 ?        S<   17:03   0:00 [watchdog/0]

root         6  0.0  0.0      0     0 ?        S<   17:03   0:00 [migration/1]

root         7  0.0  0.0      0     0 ?        S<   17:03   0:00 [ksoftirqd/1]

root         8  0.0  0.0      0     0 ?        S<   17:03   0:00 [watchdog/1]

root         9  0.0  0.0      0     0 ?        S<   17:03   0:00 [events/0]

root        10  0.0  0.0      0     0 ?        S<   17:03   0:00 [events/1]

root        11  0.0  0.0      0     0 ?        S<   17:03   0:00 [khelper]

root        46  0.0  0.0      0     0 ?        S<   17:03   0:00 [kblockd/0]

root        47  0.0  0.0      0     0 ?        S<   17:03   0:00 [kblockd/1]

root        50  0.0  0.0      0     0 ?        S<   17:03   0:00 [kacpid]

root        51  0.0  0.0      0     0 ?        S<   17:03   0:00 [kacpi_notify]

root       180  0.0  0.0      0     0 ?        S<   17:03   0:00 [kseriod]

root       222  0.0  0.0      0     0 ?        S    17:03   0:00 [pdflush]

root       223  0.0  0.0      0     0 ?        S    17:03   0:00 [pdflush]

root       224  0.0  0.0      0     0 ?        S<   17:03   0:00 [kswapd0]

root       265  0.0  0.0      0     0 ?        S<   17:03   0:00 [aio/0]

root       266  0.0  0.0      0     0 ?        S<   17:03   0:00 [aio/1]

root      1612  0.0  0.0      0     0 ?        S<   17:03   0:00 [ksuspend_usbd]

root      1613  0.0  0.0      0     0 ?        S<   17:03   0:00 [khubd]

root      1666  0.0  0.0      0     0 ?        S<   17:03   0:00 [ata/0]

root      1667  0.0  0.0      0     0 ?        S<   17:03   0:00 [ata/1]

root      1669  0.0  0.0      0     0 ?        S<   17:03   0:00 [ata_aux]

root      2395  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_0]

root      2396  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_1]

root      2397  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_2]

root      2398  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_3]

root      2399  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_4]

root      2400  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_5]

root      2479  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_6]

root      2482  0.0  0.0      0     0 ?        S<   17:03   0:00 [scsi_eh_7]

root      2903  0.0  0.0      0     0 ?        S<   17:03   0:00 [kjournald]

root      3109  0.0  0.0   2420   964 ?        S<s  17:03   0:00 /sbin/udevd --d

root      3609  0.0  0.0      0     0 ?        S<   17:03   0:00 [kpsmoused]

root      5118  0.0  0.0   1716   508 tty4     Ss+  17:03   0:00 /sbin/getty 384

root      5119  0.0  0.0   1716   508 tty5     Ss+  17:03   0:00 /sbin/getty 384

root      5123  0.0  0.0   1716   512 tty2     Ss+  17:03   0:00 /sbin/getty 384

root      5124  0.0  0.0   1716   508 tty3     Ss+  17:03   0:00 /sbin/getty 384

root      5126  0.0  0.0   1716   512 tty6     Ss+  17:03   0:00 /sbin/getty 384

root      6479  0.0  0.0   2456  1356 ?        Ss   17:03   0:00 /usr/sbin/acp

root      6517  0.0  0.0      0     0 ?        S<   17:03   0:00 [kondemand/1]

syslog    6594  0.0  0.0   1936   652 ?        Ss   17:03   0:00 /sbin/syslogd -

root      6651  0.0  0.0   1872   540 ?        S    17:03   0:00 /bin/dd bs 1 if

klog      6653  0.0  0.1   3300  2164 ?        Ss   17:03   0:00 /sbin/klogd -P

108       6675  0.0  0.0   2860  1340 ?        Ss   17:03   0:00 /usr/bin/dbus-d

root      6691  0.0  0.1  12776  2076 ?        Ssl  17:03   0:00 /usr/sbin/Netwo

root      6705  0.0  0.0   3416  1292 ?        Ss   17:03   0:00 /usr/sbin/Netwo

root      6718  0.0  0.0   4112  1104 ?        Ss   17:03   0:00 /usr/bin/system

avahi     6738  0.0  0.0   2760  1428 ?        Ss   17:03   0:00 avahi-daemon: r

avahi     6739  0.0  0.0   2760   468 ?        Ss   17:03   0:00 avahi-daemon: c

root      6782  0.0  0.1  14112  2616 ?        Ssl  17:03   0:00 /usr/sbin/cupsd

root      6838  0.0  0.0   6528  1304 ?        Ss   17:03   0:00 /usr/sbin/nmbd

root      6840  0.0  0.1  10124  2348 ?        Ss   17:03   0:00 /usr/sbin/smbd

root      6857  0.0  0.0  10124  1076 ?        S    17:03   0:00 /usr/sbin/smbd

root      6858  0.0  0.0   8084  1300 ?        Ss   17:03   0:00 /usr/sbin/winbi

root      6902  0.0  0.0   8084  1056 ?        S    17:03   0:00 /usr/sbin/winbi

root      6903  0.0  0.0   2020   900 ?        Ss   17:03   0:00 /usr/sbin/dhcdb

111       6922  0.0  0.2   6128  4268 ?        Ss   17:03   0:00 /usr/sbin/hald

root      6925  0.0  0.1   7764  2332 ?        Ssl  17:03   0:00 /usr/sbin/conso

root      6987  0.0  0.0   3236  1076 ?        S    17:03   0:00 hald-runner

root      7004  0.0  0.0   3300  1056 ?        S    17:03   0:00 hald-addon-inpu

111       7007  0.0  0.0   2204   904 ?        S    17:03   0:00 hald-addon-acpi

root      7034  0.0  0.0   3304  1040 ?        S    17:03   0:00 hald-addon-stor

root      7037  0.0  0.0   3304  1040 ?        S    17:03   0:00 hald-addon-stor

root      7060  0.0  0.0   3052  1224 ?        Ss   17:03   0:00 /usr/sbin/hcid

root      7066  0.0  0.0      0     0 ?        S<   17:03   0:00 [btaddconn]

root      7067  0.0  0.0      0     0 ?        S<   17:03   0:00 [btdelconn]

root      7078  0.0  0.0   2964  1220 ?        S    17:03   0:00 /usr/lib/blueto

root      7082  0.0  0.0   2900  1020 ?        S    17:03   0:00 /usr/lib/blueto

root      7088  0.0  0.0      0     0 ?        S<   17:03   0:00 [krfcommd]

root      7148  0.0  0.0  14068  1608 ?        Ss   17:03   0:00 /usr/sbin/gdm

root      7151  0.0  0.1  14524  3028 ?        S    17:03   0:00 /usr/sbin/gdm

root      7155  1.5  1.0  27844 21404 tty7     Ss+  17:03   0:03 /usr/bin/X :0 -

dhcp      7163  0.0  0.0   2440  1168 ?        S    17:03   0:00 /sbin/dhclient

daemon    7205  0.0  0.0   1984   424 ?        Ss   17:03   0:00 /usr/sbin/atd

root      7219  0.0  0.0   2104   888 ?        Ss   17:03   0:00 /usr/sbin/cron

root      7337  0.0  0.0   1716   512 tty1     Ss+  17:03   0:00 /sbin/getty 384

peter     7414  0.1  0.2   7352  4468 ?        S    17:03   0:00 /usr/lib/libgco

peter     7418  0.0  0.1  14248  2136 ?        S    17:03   0:00 /usr/bin/gnome-

peter     7419  0.0  0.3  28900  7536 ?        Ssl  17:03   0:00 x-session-manag

peter     7472  0.0  0.3  23100  6812 ?        Ss   17:03   0:00 /usr/bin/seahor

peter     7476  0.0  0.0   2700  1136 ?        Ss   17:03   0:00 dbus-daemon --f

peter     7477  0.0  0.4  40016 10252 ?        Sl   17:03   0:00 gnome-settings-


peter     7485  0.0  0.2  28476  5916 ?        Sl   17:03   0:00 /usr/bin/pulsea

peter     7488  0.0  0.1   5676  2204 ?        S    17:03   0:00 /usr/lib/pulsea

peter     7497  0.1  0.1  15228  2532 ?        Ss   17:03   0:00 gnome-screensav

peter     7502  0.5  0.5  20604 12084 ?        S    17:03   0:01 /usr/bin/metaci

peter     7503  2.4  2.5 104496 53404 ?        S    17:03   0:05 nautilus --sm-c

peter     7506  0.5  1.0  45124 20928 ?        Sl   17:03   0:01 gnome-panel --s

peter     7522  0.0  0.1  41176  3232 ?        Ssl  17:03   0:00 /usr/lib/bonobo

peter     7525  0.0  0.1   5376  2112 ?        S    17:03   0:00 /usr/lib/gvfs/g

peter     7529  0.0  0.4  29452  9676 ?        Sl   17:03   0:00 /usr/lib/evolut

peter     7530  0.0  0.2  14524  5708 ?        S    17:03   0:00 bluetooth-apple

peter     7536  0.0  0.2  15140  5500 ?        S    17:03   0:00 tracker-applet

peter     7537  0.0  0.4  31412 10348 ?        SNl  17:03   0:00 trackerd

peter     7547  0.0  0.5  24184 12132 ?        S    17:03   0:00 python /usr/sha

peter     7548  0.1  0.5  25232 11852 ?        S    17:03   0:00 nm-applet --sm-

peter     7549  0.0  0.2  20700  4640 ?        Ss   17:03   0:00 /usr/lib/gnome-

peter     7551  0.0  0.3  23496  7704 ?        Ss   17:03   0:00 gnome-power-man

peter     7554  0.0  0.0  29048  1976 ?        Ssl  17:03   0:00 /usr/lib/gvfs//

peter     7566  0.0  0.4  23364 10268 ?        S    17:03   0:00 /usr/lib/gnome-

peter     7569  0.0  0.1  23196  2796 ?        S    17:03   0:00 /usr/lib/gvfs/g

peter     7577  0.0  0.1   5372  2136 ?        S    17:03   0:00 /usr/lib/gvfs/g

peter     7586  0.0  0.7  44976 15300 ?        Sl   17:03   0:00 /usr/lib/gnome-

peter     7589  0.0  0.6  26568 13528 ?        S    17:03   0:00 /usr/lib/fast-u


root      7609  0.0  0.0   4000  1368 ?        Ss   17:04   0:00 /sbin/mount.ntf

peter     7763  0.0  0.1   8644  3400 ?        S    17:06   0:00 /usr/lib/gnome-

peter     7768  3.0  0.9  74716 20692 ?        Rl   17:07   0:00 gnome-terminal

peter     7770  0.0  0.0   2796   756 ?        S    17:07   0:00 gnome-pty-helpe

peter     7771  1.2  0.1   5716  3128 pts/0    Ss   17:07   0:00 bash

peter     7788  0.0  0.0   2644  1008 pts/0    R+   17:07   0:00 ps aux

---

### Post by mikewhatever on 2010-06-27
On the second thought, **ps -e** might have been a better choice. As you can see, many of the prosses' names are cut of towards the end.

---

### Post by pumpkinpapa on 2010-06-27
Yeah, that is a better command, lol.

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
   46 ?        00:00:00 kblockd/0 
   47 ?        00:00:00 kblockd/1 
   50 ?        00:00:00 kacpid 
   51 ?        00:00:00 kacpi_notify 
  180 ?        00:00:00 kseriod 
  222 ?        00:00:00 pdflush 
  223 ?        00:00:00 pdflush 
  224 ?        00:00:00 kswapd0 
  265 ?        00:00:00 aio/0 
  266 ?        00:00:00 aio/1 
 1612 ?        00:00:00 ksuspend_usbd 
 1615 ?        00:00:00 khubd 
 1661 ?        00:00:00 ata/0 
 1664 ?        00:00:00 ata/1 
 1667 ?        00:00:00 ata_aux 
 2399 ?        00:00:00 scsi_eh_0 
 2401 ?        00:00:00 scsi_eh_1 
 2462 ?        00:00:00 scsi_eh_2 
 2463 ?        00:00:00 usb-storage 
 2496 ?        00:00:00 scsi_eh_3 
 2497 ?        00:00:00 scsi_eh_4 
 2498 ?        00:00:00 scsi_eh_5 
 2499 ?        00:00:00 scsi_eh_6 
 2500 ?        00:00:00 scsi_eh_7 
 2501 ?        00:00:00 scsi_eh_8 
 2911 ?        00:00:00 kjournald 
 3118 ?        00:00:00 udevd 
 3677 ?        00:00:00 kpsmoused 
 5048 ?        00:00:00 sh 
 5049 ?        00:00:00 sleep 
 5152 tty4     00:00:00 getty 
 5153 tty5     00:00:00 getty 
 5157 tty2     00:00:00 getty 
 5158 tty3     00:00:00 getty 
 5160 tty6     00:00:00 getty 
 6513 ?        00:00:00 acpid 
 6550 ?        00:00:00 kondemand/0 
 6551 ?        00:00:00 kondemand/1 
 6628 ?        00:00:00 syslogd 
 6685 ?        00:00:00 dd 
 6687 ?        00:00:00 klogd 
 6709 ?        00:00:00 dbus-daemon 
 6725 ?        00:00:00 NetworkManager 
 6739 ?        00:00:00 NetworkManagerD 
 6752 ?        00:00:00 system-tools-ba 
 6772 ?        00:00:00 avahi-daemon 
 6773 ?        00:00:00 avahi-daemon 
 6816 ?        00:00:00 cupsd 
 6872 ?        00:00:00 nmbd 
 6874 ?        00:00:00 smbd 
 6891 ?        00:00:00 smbd 
 6892 ?        00:00:00 winbindd 
 6936 ?        00:00:00 dhcdbd 
 6952 ?        00:00:00 winbindd 
 6956 ?        00:00:00 hald 
 6959 ?        00:00:00 console-kit-dae 
 7021 ?        00:00:00 hald-runner 
 7039 ?        00:00:00 hald-addon-inpu 
 7042 ?        00:00:00 hald-addon-acpi 
 7068 ?        00:00:00 hald-addon-stor 
 7071 ?        00:00:00 hald-addon-stor 
 7074 ?        00:00:00 hald-addon-stor 
 7114 ?        00:00:00 hcid 
 7120 ?        00:00:00 btaddconn 
 7121 ?        00:00:00 btdelconn 
 7135 ?        00:00:00 bluetoothd-serv 
 7138 ?        00:00:00 krfcommd 
 7144 ?        00:00:00 bluetoothd-serv 
 7177 ?        00:00:00 gdm 
 7180 ?        00:00:00 gdm 
 7184 tty7     00:00:01 Xorg 
 7228 ?        00:00:00 atd 
 7242 ?        00:00:00 cron 
 7352 tty1     00:00:00 getty 
 7371 ?        00:00:00 gconfd-2 
 7376 ?        00:00:00 gnome-keyring-d 
 7377 ?        00:00:00 x-session-manag 
 7430 ?        00:00:00 seahorse-agent 
 7434 ?        00:00:00 dbus-daemon 
 7435 ?        00:00:00 gnome-settings- 
 7443 ?        00:00:00 pulseaudio 
 7446 ?        00:00:00 gconf-helper 
 7459 ?        00:00:00 gnome-screensav 
 7460 ?        00:00:00 metacity 
 7461 ?        00:00:00 nautilus 
 7464 ?        00:00:00 gnome-panel 
 7480 ?        00:00:00 bonobo-activati 
 7483 ?        00:00:00 gvfsd 
 7484 ?        00:00:00 update-notifier 
 7487 ?        00:00:00 evolution-alarm 
 7488 ?        00:00:00 bluetooth-apple 
 7491 ?        00:00:00 jockey-gtk 
 7494 ?        00:00:00 tracker-applet 
 7495 ?        00:00:00 trackerd 
 7502 ?        00:00:00 python 
 7503 ?        00:00:00 nm-applet 
 7504 ?        00:00:00 gnome-volume-ma 
 7505 ?        00:00:00 gnome-power-man 
 7514 ?        00:00:00 gvfs-fuse-daemo 
 7525 ?        00:00:00 trashapplet 
 7528 ?        00:00:00 gvfsd-trash 
 7535 ?        00:00:00 gvfsd-burn 
 7570 ?        00:00:00 mixer_applet2 
 7573 ?        00:00:00 fast-user-switc 
 7590 ?        00:00:00 gnome-terminal 
 7592 ?        00:00:00 gnome-pty-helpe 
 7593 pts/0    00:00:00 bash 
 7610 pts/0    00:00:00 ps

---

### Post by mikewhatever on 2010-06-28
Odd indeed, I don't see any package manager related process either.

---

### Post by pumpkinpapa on 2010-06-28
I'm updating to Lucid soon and will see if it's just a Jaunty bug, Thanks for your help.

---

### Post by pumpkinpapa on 2010-06-29
Well I solved it. I started up Synaptic and was presented with a dialog box telling me to run 'dpkg --reconfigure -a' or something like that. And then the modem driver installed fine.

---

