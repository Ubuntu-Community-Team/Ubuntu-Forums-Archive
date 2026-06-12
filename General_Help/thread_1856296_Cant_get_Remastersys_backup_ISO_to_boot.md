---
title: "Cant get Remastersys backup ISO to boot"
date: 2011-10-07
forum: General Help
---

### Post by cybernetic toaster pastry on 2011-10-07
I have tried so many times to create a backup of my whole system because  way too many times I have had to do fresh installs after tweaking my  system. Don't get me wrong I have learned a lot about command line  screens and such and it's taught me a lot but I'm tired of the worry of  IF I can go back.

The last time I tried to use Remastersys to create a backup and it  didn't work I checked the remastersys.log and saw several folders the it  skipped because they where in use and some because no permission. 
So what I did was reboot into the command line screen and logged in as root then ran remastersys backup.

When it was done I rebooted the computer and opened VMware player4 and  installed the ISO. When it started to load it showed the VMware bios  screen like normal then just went to a black screen with this

 "ISOLINUX 3.82 2009-06-09 ETCD Copyright (C) 1994-2009 H. Peter Anvin et al" 

and it just sits there. I left it like that for 20min incase that was just a loading screen but it just sits there.

Any help is much appreciated.

Here is my remastersys.log file
```
Source directory entry tmp already used! - trying tmp_1
Source directory entry sys already used! - trying sys_1
Source directory entry dev already used! - trying dev_1
Source directory entry etc already used! - trying etc_1
Source directory entry media already used! - trying media_1
Source directory entry var already used! - trying var_1
Source directory entry proc already used! - trying proc_1
Source directory entry mnt already used! - trying mnt_1
------------------------------------------------------
Mount information
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
nfsd on /proc/fs/nfsd type nfsd (rw)
vmware-vmblock on /var/run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
------------------------------------------------------
Casper Script info
total 144
-rwxr-xr-x 1 root root  297 2011-01-20 09:30 01integrity_check
-rwxr-xr-x 1 root root  383 2011-01-20 09:30 05mountpoints
-rwxr-xr-x 1 root root  571 2011-01-20 09:30 07remove_oem_config
-rw-r--r-- 1 root root 3375 2011-01-20 09:30 10adduser
-rwxr-xr-x 1 root root  400 2011-01-20 09:30 12fstab
-rwxr-xr-x 1 root root  830 2011-01-20 09:30 13swap
-rwxr-xr-x 1 root root 1431 2011-01-20 09:30 14locales
-rw-r--r-- 1 root root 1751 2011-01-20 09:30 15autologin
-rwxr-xr-x 1 root root  577 2011-01-20 09:30 18hostname
-rwxr-xr-x 1 root root 7529 2011-01-20 09:30 19keyboard
-rwxr-xr-x 1 root root  546 2011-01-20 09:30 20xconfig
-rwxr-xr-x 1 root root  531 2011-01-20 09:30 22gnome_panel_data
-rwxr-xr-x 1 root root  904 2011-01-20 09:30 22screensaver
-rwxr-xr-x 1 root root  577 2011-01-20 09:30 22serialtty
-rwxr-xr-x 1 root root  410 2011-01-20 09:30 22sslcert
-rwxr-xr-x 1 root root  380 2011-01-20 09:30 23etc_modules
-rwxr-xr-x 1 root root 3006 2011-01-20 09:30 23networking
-rwxr-xr-x 1 root root 1979 2011-01-20 09:30 24preseed
-rwxr-xr-x 1 root root 1996 2011-01-20 09:30 25configure_init
-rwxr-xr-x 1 root root 9144 2011-01-20 09:30 30accessibility
-rwxr-xr-x 1 root root  759 2011-01-20 09:30 31disable_update_notifier
-rwxr-xr-x 1 root root  817 2011-01-20 09:30 32disable_hibernation
-rwxr-xr-x 1 root root  369 2011-01-20 09:30 33enable_apport_crashes
-rwxr-xr-x 1 root root  892 2011-01-20 09:30 34disable_kde_services
-rwxr-xr-x 1 root root  562 2011-01-20 09:30 35fix_language_selector
-rwxr-xr-x 1 root root  407 2011-01-20 09:30 36disable_trackerd
-rwxr-xr-x 1 root root  908 2011-01-20 09:30 40install_driver_updates
-rwxr-xr-x 1 root root  432 2011-01-20 09:30 41apt_cdrom
-rwxr-xr-x 1 root root  847 2011-01-20 09:32 43disable_updateinitramfs
-rwxr-xr-x 1 root root 1261 2011-01-20 09:30 44pk_allow_ubuntu
-rwxr-xr-x 1 root root  325 2011-01-20 09:30 45disable_guest_account
-rwxr-xr-x 1 root root 1191 2011-01-20 09:30 47une_ubiquity
-rwxr-xr-x 1 root root  214 2011-01-20 09:30 48kubuntu_disable_restart_notifications
------------------------------------------------------
/etc/remastersys.conf info
#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/"


# Here you can add any other files or directories to be excluded from the live filesystem
# Separate each entry with a space
EXCLUDES="/BLOCK"


# Here you can change the livecd/dvd username
LIVEUSER="dan"


# Here you can change the name of the livecd/dvd label
LIVECDLABEL="Custom Live CD"


# Here you can change the name of the ISO file that is created
CUSTOMISO="Danbuntu.iso"


# Here you can change the url for the usb-creator info
LIVECDURL="http://www.geekconnection.org/remastersys"

------------------------------------------------------
/etc/casper.conf info
# This file should go in /etc/casper.conf
# Supported variables are:
# USERNAME, USERFULLNAME, HOST, BUILD_SYSTEM
 
export USERNAME="dan"
export USERFULLNAME="Live session user"
export HOST="dan"
export BUILD_SYSTEM="Ubuntu"
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
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:105::/var/run/dbus:/bin/false
avahi-autoipd:x:103:108:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:109:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
usbmux:x:106:46:usbmux daemon,,,:/home/usbmux:/bin/false
speech-dispatcher:x:107:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:117:RealtimeKit,,,:/proc:/bin/false
saned:x:111:118::/home/saned:/bin/false
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:113:120:Gnome Display Manager:/var/lib/gdm:/bin/false
dan:x:1000:0:dan,,,:/home/dan:/bin/bash
haldaemon:x:114:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false
statd:x:115:65534::/var/lib/nfs:/bin/false
sshd:x:116:65534::/var/run/sshd:/usr/sbin/nologin
------------------------------------------------------
/etc/group info
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:dan
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:dan
fax:x:21:dan
voice:x:22:
cdrom:x:24:dan
floppy:x:25:dan
tape:x:26:
sudo:x:27:
audio:x:29:pulse,dan
dip:x:30:dan
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:dan
sasl:x:45:
plugdev:x:46:dan
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:dan
messagebus:x:105:
mlocate:x:106:
ssh:x:107:
avahi-autoipd:x:108:
avahi:x:109:
netdev:x:110:dan
lpadmin:x:111:dan
ssl-cert:x:112:
couchdb:x:113:
pulse:x:114:
pulse-access:x:115:
utempter:x:116:
rtkit:x:117:
saned:x:118:
admin:x:119:dan
gdm:x:120:
nopasswdlogin:x:121:
dan:x:1000:
sambashare:x:122:dan
haldaemon:x:123:
head-honcho:x:1001:dan
winbindd_priv:x:124:
------------------------------------------------------
Command-line options = backup
------------------------------------------------------
 Calculating the installed filesystem size for the installer
```

---

### Post by cybernetic toaster pastry on 2011-10-08
I guess my problem is a rarity. Everything seems in order but it never works no matter how I try it. Does any one know of another way I can back up my entire system?

---

### Post by Frogs Hair on 2011-10-08
Remastersys is a dead project here is a similar project . [http://re-linux.sourceforge.net/](http://re-linux.sourceforge.net/)

---

### Post by cybernetic toaster pastry on 2011-10-08
Thank you for your reply. I didn't know it was a dead project. A while back I googled backing up ubuntu system and almost all results were about Remastersys so I went with it. Thank you for pointing me in the right direction.

---

### Post by mike555 on 2011-10-08
relinux puts the .iso in a different folder (fyi)you can find it in /root/relinux (instead of root home folder) , also you might need to sudo nautilus and change permissions on that folder ...
  otherwise seems to work ok ...

update , it appears newer versions of relinux do put the iso in home/relinux , at least it did on my Xubuntu 11.10 just now , and the iso worked except for complaining something about not being Debian.

---

### Post by cybernetic toaster pastry on 2011-10-08
Haha, I'm still trying to figure out how to install it. the install directions say to run
 ```
 sudo cp -R usr etc /
``` in the terminal but when I do I get 
```
cp: cannot stat `usr': No such file or directory
cp: cannot stat `etc': No such file or directory
```and if I do it as root I get 
```
cp: `/usr' and `/usr' are the same file
cp: `/etc' and `/etc' are the same file
```Any ideas. It looks like its trying to merge it's usr and etc folders with the ones that already exist. Should I do that manually?

---

### Post by inameiname on 2011-10-14
> **mike555 said:**
> relinux puts the .iso in a different folder (fyi)you can find it in /root/relinux (instead of root home folder) , also you might need to sudo nautilus and change permissions on that folder ...
  otherwise seems to work ok ...

update , it appears newer versions of relinux do put the iso in home/relinux , at least it did on my Xubuntu 11.10 just now , and the iso worked except for complaining something about not being Debian.


Relinux is indeed coming along fairly well. A lot of issues have been addressed just in the past few days, with plans to address/fix many more. It is looking to be a good replacement for the now dead remastersys, a greatly-missed program for many of us.

Here is an article about it from the developer:

[http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)

Also, here is another thread on here about it:

[http://ubuntuforums.org/showthread.php?t=1857376&highlight=relinux](http://ubuntuforums.org/showthread.php?t=1857376&highlight=relinux)

---

