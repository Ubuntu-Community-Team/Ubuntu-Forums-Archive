---
title: "Making Customized Distro of Ubuntu Server (minimal)"
date: 2012-09-27
forum: General Help
---

### Post by fkasmani on 2012-09-27
I've made an Ubuntu installation from minimal with no X -  everything is based on CLI and added some apps to it. I've custom  designed it so it can be like a LAN-based web server and serve the  apps/data as necessary.
  I'm now trying to make a distro of this setup and tried with  Remastersys. While the process completed OK and he LiveCD works well,  the install option does nothing more than booting it in LiveCD mode.
  One of the lines I see while Remastersys is in the process,
  ```
Installing the Ubiquity GTK frontend 

grep: /etc/x11/default-display-manager: No such file or directory
```  I even tried removing Remastersys followed by a reinstall with no  luck. "Bing*ed*" around for some help and cam across some interesting  stuff which says Ubuntu does not have CLI based install process so it's  not Remastersys's fault. Some suggestion was that I install  ubiquity-frontend-debconf before installing Remastersys. I even tried  this but no luck.
  I do not need any graphical installer and there's no options to choose from at the time of install.
  I don't understand why they say Ubuntu can only install with a  graphical installer, when Ubuntu Server minimal edition does not seem to  use a graphical installer (correct me if I'm wrong, pls)
  How would I be able to go about with this, pls? Latest remastersys.log copied below:
```
Distribution Mode Selected
Enabling remastersys-firstboot
Checking filesystem type of the Working Folder
/home/remastersys/remastersys is on a ext4 filesystem
Making sure popularity contest is not installed
Installing the Ubiquity GTK frontend
Checking if the /home/remastersys/remastersys folder has been created
Creating /home/remastersys/remastersys/ISOTMP folder tree
Copying /var and /etc to temp area and excluding extra files  ... this will take a while so be patient
Cleaning up files not needed for the live in /home/remastersys/remastersys/dummysys
Cleaning up passwd, group, shadow and gshadow files for the live system
Making sure adduser and autologin functions of casper are set properly
Copying memtest86+ for the live system
Creating isolinux setup for the live system
Checking the ARCH of the system and setting the README.diskdefines file
Creating filesystem.manifest and filesystem.manifest-desktop
Creating the casper.conf file.
Checking and setting user-setup-apply for the live system
Setting up casper and ubiquity options for dist mode
Creating a new initial ramdisk for the live system
Copying your kernel and initrd for the livecd
Creating filesystem.squashfs   ... this will take a while so be patient
Adding stage 1 files/folders that the livecd requires
Adding stage 2 files/folders that the livecd requires
------------------------------------------------------
Mount information
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
------------------------------------------------------
Disk size information
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  3.3G  3.9G  46% /
udev            114M  4.0K  114M   1% /dev
tmpfs            49M  288K   49M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            122M     0  122M   0% /run/shm
------------------------------------------------------
Casper Script info
total 148
-rwxr-xr-x 1 root root  297 Apr 18 12:17 01integrity_check
-rwxr-xr-x 1 root root  467 Apr 18 12:17 05mountpoints
-rwxr-xr-x 1 root root  571 Apr 18 12:17 07remove_oem_config
-rwxr-xr-x 1 root root  400 Apr 18 12:17 12fstab
-rwxr-xr-x 1 root root  830 Apr 18 12:17 13swap
-rwxr-xr-x 1 root root 1221 Apr 18 12:17 14locales
-rwxr-xr-x 1 root root 2920 Apr 18 12:17 15autologin
-rwxr-xr-x 1 root root  577 Apr 18 12:17 18hostname
-rwxr-xr-x 1 root root 8878 Apr 18 12:17 19keyboard
-rwxr-xr-x 1 root root  546 Apr 18 12:17 20xconfig
-rwxr-xr-x 1 root root  624 Apr 18 12:17 22gnome_panel_data
-rwxr-xr-x 1 root root  867 Apr 18 12:17 22screensaver
-rwxr-xr-x 1 root root  577 Apr 18 12:17 22serialtty
-rwxr-xr-x 1 root root  410 Apr 18 12:17 22sslcert
-rwxr-xr-x 1 root root  380 Apr 18 12:17 23etc_modules
-rwxr-xr-x 1 root root 3786 Apr 18 12:33 23networking
-rwxr-xr-x 1 root root 2102 Apr 18 12:17 24preseed
-rwxr-xr-x 1 root root 3939 Apr 18 12:17 25adduser
-rwxr-xr-x 1 root root 1996 Apr 18 12:17 25configure_init
-rwxr-xr-x 1 root root  644 Apr 18 12:17 26disable_user_menu
-rwxr-xr-x 1 root root 1421 Apr 18 12:17 30accessibility
-rwxr-xr-x 1 root root 1152 Apr 18 12:17 31disable_update_notifier
-rwxr-xr-x 1 root root  463 Apr 18 12:17 32disable_hibernation
-rwxr-xr-x 1 root root  650 Apr 18 12:17 33enable_apport_crashes
-rwxr-xr-x 1 root root  928 Apr 18 12:17 34disable_kde_services
-rwxr-xr-x 1 root root  562 Apr 18 12:17 35fix_language_selector
-rwxr-xr-x 1 root root  407 Apr 18 12:17 36disable_trackerd
-rwxr-xr-x 1 root root  908 Apr 18 12:17 40install_driver_updates
-rwxr-xr-x 1 root root  561 Apr 18 12:17 41apt_cdrom
-rwxr-xr-x 1 root root  847 Apr 18 12:17 43disable_updateinitramfs
-rwxr-xr-x 1 root root  640 Apr 18 12:17 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  594 Apr 18 12:17 45jackd2
-rwxr-xr-x 1 root root  215 Apr 18 12:17 48kubuntu_disable_restart_notifications
-rwxr-xr-x 1 root root  169 Apr 18 12:17 49kubuntu_mobile_session
-rwxr-xr-x 1 root root  346 Apr 18 12:17 50ubiquity-bluetooth-agent
------------------------------------------------------
/etc/remastersys.conf info

#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES=""


# Here you can change the livecd/dvd username
LIVEUSER="custom"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Custom Live CD"


# Here you can change the name of the ISO file that is created
CUSTOMISO="custom-$1.iso"


# Here you can change the mksquashfs options
SQUASHFSOPTS="-no-recovery -always-use-fragments -b 1M -no-duplicates"


# Here you can prevent the Install icon from showing up on the desktop in backup mode. 0 - to not show 1 - to show 
BACKUPSHOWINSTALL="1"


# Here you can change the url for the usb-creator info
LIVECDURL="http://www.remastersys.com"
------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM

export USERNAME="custom"
export USERFULLNAME="Live session user"
export HOST="custom"
export BUILD_SYSTEM="Ubuntu"
export FLAVOUR="custom"
------------------------------------------------------
/etc/passwd info
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
whoopsie:x:103:107::/nonexistent:/bin/false
landscape:x:104:110::/var/lib/landscape:/bin/false
sshd:x:105:65534::/var/run/sshd:/usr/sbin/nologin
mysql:x:106:115:MySQL Server,,,:/nonexistent:/bin/false
zabbix:x:107:116::/var/run/zabbix/:/bin/false
snmp:x:108:117::/var/lib/snmp:/bin/false
postfix:x:109:118::/var/spool/postfix:/bin/false
nagios:x:110:120::/var/lib/nagios:/bin/false
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:
staff:x:50:
games:x:60:
users:x:100:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
vboxsf:x:104:
fuse:x:105:
messagebus:x:106:
whoopsie:x:107:
mlocate:x:108:
ssh:x:109:
landscape:x:110:
netdev:x:111:
lpadmin:x:112:
sambashare:x:113:
ssl-cert:x:114:
mysql:x:115:
zabbix:x:116:
snmp:x:117:
postfix:x:118:
postdrop:x:119:
nagios:x:120:www-data
nogroup:x:65534:
------------------------------------------------------
/etc/X11/default-display-manager info
------------------------------------------------------
/etc/skel info
/etc/skel
/etc/skel/.bashrc
/etc/skel/.profile
/etc/skel/.bash_logout
------------------------------------------------------
lsb-release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
------------------------------------------------------
remastersys version info
REMASTERSYSVERSION="3.0.3-1"
 
------------------------------------------------------
ISOTMP info
/home/remastersys/remastersys/ISOTMP:
total 24
drwxr-xr-x 2 root root 4096 Sep 26 22:20 casper
drwxr-xr-x 2 root root 4096 Sep 24 10:52 install
drwxr-xr-x 2 root root 4096 Sep 26 22:15 isolinux
-rw-r--r-- 1 root root  844 Sep 24 11:29 md5sum.txt
drwxr-xr-x 2 root root 4096 Sep 24 10:52 preseed
-rw-r--r-- 1 root root  195 Sep 26 22:15 README.diskdefines
-rw-r--r-- 1 root root    0 Sep 24 11:29 ubuntu

/home/remastersys/remastersys/ISOTMP/casper:
total 537732
-rw-r--r-- 1 root root     21881 Sep 26 22:15 filesystem.manifest
-rw-r--r-- 1 root root     21817 Sep 26 22:15 filesystem.manifest-desktop
-rw-r--r-- 1 root root        11 Sep 24 11:29 filesystem.size
-rw-r--r-- 1 root root 528551936 Sep 26 22:53 filesystem.squashfs
-rw-r--r-- 1 root root  17007298 Sep 26 22:20 initrd.gz
-rw-r--r-- 1 root root       195 Sep 26 22:15 README.diskdefines
-rw------- 1 root root   5011712 Sep 26 22:20 vmlinuz

/home/remastersys/remastersys/ISOTMP/install:
total 176
-rw-r--r-- 1 root root 176764 Sep 26 22:15 memtest

/home/remastersys/remastersys/ISOTMP/isolinux:
total 400
-rw-r--r-- 1 root root  24576 Sep 26 22:15 isolinux.bin
-rw-r--r-- 1 root root    896 Sep 26 22:15 isolinux.cfg
-rwxr-xr-x 1 root root 220583 Sep 26 22:15 splash.png
-rw-r--r-- 1 root root 155792 Sep 26 22:15 vesamenu.c32

/home/remastersys/remastersys/ISOTMP/preseed:
total 4
-rwxr-xr-x 1 root root 212 Sep 26 22:15 custom.seed
------------------------------------------------------
/home/remastersys/remastersys/tmpusers info
openemr
------------------------------------------------------
Command-line options = dist
------------------------------------------------------
Removing the ubiquity frontend as it has been included and is not needed on the normal system
Calculating the installed filesystem size for the installer
Removing remastersys-firstboot from system startup
Making disk compatible with Ubuntu Startup Disk Creator.
Creating md5sum.txt for the livecd/dvd
Creating custom-dist.iso in /home/remastersys/remastersys
Creating custom-dist.iso.md5 in /home/remastersys/remastersys
/home/remastersys/remastersys/custom-dist.iso which is 527M in size is ready to be burned or tested in a virtual machine.
```

---

### Post by kallon on 2013-01-30
Yes, I would like to know the answer to this also.

---

