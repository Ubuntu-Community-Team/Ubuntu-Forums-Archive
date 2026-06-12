---
title: "Active Process During System Backup??"
date: 2011-10-02
forum: General Help
---

### Post by max1e6 on 2011-10-02
Hi,


I have a new 10.04 install. For some reason setting-up this computer was a bear and, having it working, I want a system backup. I followed the instructions at hxxps://help.ubuntu.com/community/BackupYourSystem/TAR. I am using the recommended command: 

sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 

Several times I tried this, including after a reboot. It fails at the same spot every time:

/lib32/libpam.so.0.82.2
/srv/
tar: /: file changed as we read it
tar: Exiting with failure status due to previous errors

I am not touching the computer during backup.

Any ideas?

PS:

Could there be a background process (perhaps malicious) that is changing a file during the tar? Here is a list of processes:

max@mark-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 cpuset
   20 ?        00:00:00 khelper
   21 ?        00:00:00 async/mgr
   22 ?        00:00:00 pm
   24 ?        00:00:00 sync_supers
   25 ?        00:00:00 bdi-default
   26 ?        00:00:00 kintegrityd/0
   27 ?        00:00:00 kintegrityd/1
   28 ?        00:00:00 kintegrityd/2
   29 ?        00:00:00 kintegrityd/3
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kblockd/1
   32 ?        00:00:00 kblockd/2
   33 ?        00:00:00 kblockd/3
   34 ?        00:00:00 kacpid
   35 ?        00:00:00 kacpi_notify
   36 ?        00:00:00 kacpi_hotplug
   37 ?        00:00:00 ata/0
   38 ?        00:00:00 ata/1
   39 ?        00:00:00 ata/2
   40 ?        00:00:00 ata/3
   41 ?        00:00:00 ata_aux
   42 ?        00:00:00 ksuspend_usbd
   43 ?        00:00:00 khubd
   44 ?        00:00:00 kseriod
   45 ?        00:00:00 kmmcd
   51 ?        00:00:00 khungtaskd
   52 ?        00:00:00 kswapd0
   53 ?        00:00:00 kswapd1
   54 ?        00:00:00 ksmd
   55 ?        00:00:00 aio/0
   56 ?        00:00:00 aio/1
   57 ?        00:00:00 aio/2
   58 ?        00:00:00 aio/3
   59 ?        00:00:00 ecryptfs-kthrea
   60 ?        00:00:00 crypto/0
   61 ?        00:00:00 crypto/1
   62 ?        00:00:00 crypto/2
   63 ?        00:00:00 crypto/3
   78 ?        00:00:00 kstriped
   79 ?        00:00:00 kmpathd/0
   80 ?        00:00:00 kmpathd/1
   81 ?        00:00:00 kmpathd/2
   82 ?        00:00:00 kmpathd/3
   83 ?        00:00:00 kmpath_handlerd
   84 ?        00:00:00 ksnapd
   85 ?        00:00:00 kondemand/0
   86 ?        00:00:00 kondemand/1
   87 ?        00:00:00 kondemand/2
   88 ?        00:00:00 kondemand/3
   89 ?        00:00:00 kconservative/0
   90 ?        00:00:00 kconservative/1
   91 ?        00:00:00 kconservative/2
   92 ?        00:00:00 kconservative/3
  243 ?        00:00:00 scsi_eh_0
  253 ?        00:00:00 scsi_eh_1
  275 ?        00:00:00 khpsbpkt
  282 ?        00:00:00 scsi_eh_2
  283 ?        00:00:00 scsi_eh_3
  284 ?        00:00:00 scsi_eh_4
  285 ?        00:00:00 scsi_eh_5
  292 ?        00:00:00 knodemgrd_0
  295 ?        00:00:00 knodemgrd_1
  300 ?        00:00:00 scsi_eh_6
  301 ?        00:00:00 usb-storage
  308 ?        00:00:00 usbhid_resumer
  335 ?        00:00:00 jbd2/sdc5-8
  336 ?        00:00:00 ext4-dio-unwrit
  337 ?        00:00:00 ext4-dio-unwrit
  338 ?        00:00:00 ext4-dio-unwrit
  339 ?        00:00:00 ext4-dio-unwrit
  372 ?        00:00:02 flush-8:32
  405 ?        00:00:00 upstart-udev-br
  408 ?        00:00:00 udevd
  594 ?        00:00:00 edac-poller
  902 ?        00:00:00 phy0
 1015 ?        00:00:00 rsyslogd
 1025 ?        00:00:00 dbus-daemon
 1037 ?        00:00:00 gdm-binary
 1044 ?        00:00:00 avahi-daemon
 1046 ?        00:00:00 avahi-daemon
 1051 ?        00:00:00 console-kit-dae
 1133 ?        00:00:00 gdm-simple-slav
 1194 tty4     00:00:00 getty
 1198 tty5     00:00:00 getty
 1204 tty2     00:00:00 getty
 1205 tty3     00:00:00 getty
 1207 tty6     00:00:00 getty
 1210 ?        00:00:00 acpid
 1212 ?        00:00:00 irqbalance
 1234 ?        00:00:00 atd
 1235 ?        00:00:00 cron
 1486 ?        00:00:00 exim4
 1487 tty7     00:03:56 Xorg
 1538 ?        00:00:01 wicd
 1554 ?        00:00:00 wicd-monitor
 1561 ?        00:00:00 winbindd
 1563 ?        00:00:00 winbindd
 1583 ?        00:00:00 cupsd
 1686 tty1     00:00:00 getty
 1705 ?        00:00:00 dbus-launch
 1721 ?        00:00:00 gdm-session-wor
 1723 ?        00:00:00 upowerd
 1731 ?        00:00:00 polkitd
 1785 ?        00:00:00 udevd
 1787 ?        00:00:00 udevd
 1828 ?        00:00:00 dhclient <defunct>
 1837 ?        00:00:00 hald
 1838 ?        00:00:00 hald-runner
 1861 ?        00:00:00 hald-addon-inpu
 1870 ?        00:00:00 hald-addon-rfki
 1871 ?        00:00:00 hald-addon-leds
 1878 ?        00:00:00 hald-addon-stor
 1879 ?        00:00:00 hald-addon-stor
 1881 ?        00:00:00 hald-addon-stor
 1882 ?        00:00:00 hald-addon-stor
 1885 ?        00:00:00 hald-addon-stor
 1892 ?        00:00:00 hald-addon-cpuf
 1893 ?        00:00:00 hald-addon-acpi
 1894 ?        00:00:00 hald-addon-stor
 1912 ?        00:00:00 dhclient
 1925 ?        00:00:00 gnome-keyring-d
 1943 ?        00:00:00 gnome-session
 1977 ?        00:00:00 ssh-agent
 1980 ?        00:00:00 dbus-launch
 1981 ?        00:00:00 dbus-daemon
 1984 ?        00:00:00 gconfd-2
 1991 ?        00:00:00 gnome-settings-
 1993 ?        00:00:00 gvfsd
 1998 ?        00:00:00 gvfs-fuse-daemo
 2003 ?        00:00:00 metacity
 2005 ?        00:00:00 pulseaudio
 2007 ?        00:00:00 rtkit-daemon
 2010 ?        00:00:00 gnome-power-man
 2012 ?        00:00:00 gnome-panel
 2015 ?        00:00:00 nautilus
 2016 ?        00:00:00 polkit-gnome-au
 2017 ?        00:00:00 wicd-client
 2021 ?        00:00:00 gconf-helper
 2026 ?        00:00:00 gvfs-gdu-volume
 2028 ?        00:00:00 udisks-daemon
 2029 ?        00:00:00 udisks-daemon
 2031 ?        00:00:00 gvfsd-trash
 2033 ?        00:00:00 gvfs-afc-volume
 2036 ?        00:00:00 gvfs-gphoto2-vo
 2040 ?        00:00:00 bonobo-activati
 2047 ?        00:00:00 indicator-apple
 2049 ?        00:00:00 clock-applet
 2050 ?        00:00:00 indicator-apple
 2059 ?        00:00:00 gvfsd-metadata
 2061 ?        00:00:00 indicator-appli
 2063 ?        00:00:00 indicator-messa
 2065 ?        00:00:00 indicator-sound
 2068 ?        00:00:00 indicator-sessi
 2070 ?        00:00:00 indicator-me-se
 2085 ?        00:00:00 gvfsd-burn
 2101 ?        00:00:00 gnome-screensav
 2108 ?        00:00:00 gdu-notificatio
 2124 ?        00:00:00 evolution-alarm
 2126 ?        00:00:00 python
 2139 ?        00:00:44 gnome-terminal
 2140 ?        00:00:00 gnome-pty-helpe
 2141 pts/0    00:00:00 bash
 2161 ?        00:00:00 update-notifier
 2321 ?        00:00:40 firefox
 2331 ?        00:00:00 firefox <defunct>
 2456 pts/1    00:00:00 bash
 2472 pts/1    00:00:00 ps
max@mark-desktop:~$ clear

---

### Post by 2F4U on 2011-10-02
There are a lot of background processes on any Linux system that are constantly running. However, these are not malicious. An operating systems does things in the background even if you don't touch it and there is nothing you can do about it. I would suggest to exclude those folders/files so that the backup is able to continue.
Is there any reason why you need include those system files in your backup? These files rarely change. I think a better approach could be to create an image from your root partition and only backup the user files. The image would be taken "offline", for example from a dedicated liveCD, so that there are no running processes.

---

### Post by max1e6 on 2011-10-02
My usual approach is to backup my user files only and then simply reinstall Ubuntu if the need arises. This particular install is on an old Tyan S2885 system with some pretty weird hardware. Because configuring my install on the machine is very convoluted I would, in this case, prefer to be able to record my current install in a tar and simply restore it (if needed).

The approach I was taking is based on the Ubuntu tutorial, "Backup Your System Tar", at hxxps://help.ubuntu.com/community/BackupYourSystem/TAR. The tutorial suggests that the method will enable a complete restoration of an install. I have actually used the method on other machines in the past... never got the "file changed as we read it" error provided I didn't attempt to use the machine when the tar was being created. 

As far as backing up the system using the method, I'm not too fussy about how I do it. Just never found such a nice tutorial for a fella of my limited brainpower. I suppose I could use the method after mounting my install from the live disk. 

But...now I'm paranoid. Why is this install running a process that changes system files? Never happened before. One of the things I hate most about Windows Systems is the way they covertly do stuff in the background. Frankly, it exposes these systems to hacks. Can anybody see a process in my list that should be disabled? That is, is there anything unusual that could be interfering with the approach recommended in the Ubuntu tutorial?

Thanks

---

### Post by max1e6 on 2011-10-04
Still pondering. I guess to focus my question, the create backup tar approach always chokes when it gets to my lib32 directory. 

I learned that it is the demons that are most likely to be running background tasks. Evidently, I am not the only one out there that is concerned about this from a control and security standpoint.

I still get "file changing as we read it" error when taring  /lib32 even after temporally killing all the daemons in system monitor except (except dbus).

What is the best way to back-up an installation (not just my files)? A step-by-step like the Back-up System Tar tutorial would help me on the way - but, it's not critical.

---

### Post by Mark Phelps on 2011-10-04
For ease of recovery, the best way I've found is using Clonezilla.  It allows you to image your partitions off to external media.  Recovery is then a simple restore from that external media.

If you go to their website and read through their FAQs, there is even a way to install Clonezilla to your hard drive so you can select it from GRUB.  That way, you don't even have to boot from CD to do a backup or recovery.

---

