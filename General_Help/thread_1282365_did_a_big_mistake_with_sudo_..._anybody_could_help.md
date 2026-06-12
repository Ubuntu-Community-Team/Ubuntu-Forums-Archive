---
title: "did a big mistake with sudo ... anybody could help ?"
date: 2009-10-04
forum: General Help
---

### Post by fabianus on 2009-10-04
Hello all !

For a bad reason I did the following : 


sudo chmod -R 777 /etc/

I know that it was stupid, but now it is done ...

I did not yet restart the computer and I hope you could help me out. 

Because for any sudo I try to execute I get : 

sudo: /etc/sudoers is mode 0777, should be 0440

and even if I try this : 

pbx@pbx:~$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440

So I am stuck. Do you have any idea how I could repair this :-( ?

Thanks a lot for any help as this is an asterisk production server and it'll be a mess if I may not get this fixed !

Regards, 
Fabianus

---

### Post by x C0MMAND0 x on 2009-10-04
Don't reboot yet unless somebody has a better idea...

But you could reboot, then go into the recovery console which will let you login as root.  Then cd to /etc/ and change permissions on /etc/sudoers/

That's all I can think of that might work.  Like I said, I would WAIT to reboot just to be safe in case somebody has a better idea.

---

### Post by fabianus on 2009-10-04
Hello X Command0 x, 

Thanks a lot for your fast reply ! As you suggested I will wait for other suggestions. 

In meanwhile I have two questions: 
1) How to I enter into the recovery console ?
2) Do you think that my command "sudo chmod -R 777 /etc/" has any other consequences other than this one that might block the system ?

Thanks for any further feedback !

Regards, 
Fabianus

---

### Post by Steel-Bunz on 2009-10-04
Are you able to view the contents of the sudoers file? (*sudo cat /etc/sudoers*)

To edit the sudoers file, you need to use "visudo" command. Not sure, if it will work for chmod; you can give it a try, but, I am fairly new to Linux, so be warned. :)

---

### Post by wojox on 2009-10-04
I think you need to boot into recovery mode and 

```
chmod 0440 /etc
```

---

### Post by SuperSonic4 on 2009-10-04
> **x C0MMAND0 x said:**
> Don't reboot yet unless somebody has a better idea...

But you could reboot, then go into the recovery console which will let you login as root.  Then cd to /etc/ and change permissions on /etc/sudoers/

That's all I can think of that might work.  Like I said, I would WAIT to reboot just to be safe in case somebody has a better idea.

I don't have a better idea.

To get into recovery mode press esc before it boots into ubuntu

---

### Post by fela on 2009-10-04
If you have set a root password then you can just:

```
su
```

(enter root password)

Then do what it says:

```
chmod 0440 /etc/sudoers
```

Why did you give the whole of /etc and everything in it read, write and execute permissions for everyone though? Are you interested in borking your system?

---

### Post by fabianus on 2009-10-04
Hi fela, 

the problem is that I did not set a root password. And to do so I need sudo ...

:-(

Or do you have another solution to set the root password ?

Regards, 
Fabianus

---

### Post by Vaphell on 2009-10-04
firing up live cd, mounting the partition with /etc and chmoding from there should work i think

---

### Post by GrandpaLeaman on 2009-10-04
I think I did something like this before to "sudoers" As I recall I installed my trusty live CD, opened a terminal and ran gksudo nautilus and was able to navigate to that file and change the permissions back. At least that is what I recall.

---

### Post by barthel on 2009-10-04
LiveCD is probably the only way to go to fix  your sudoer permissions, but that's probably not enough. Since you did a recursive chmod, your system may not reboot with incorrect permissions on other files. So, while you're in the LiveCD session, it would be best to fix as much as possible.

WARNING: This will be painful.

Personally, I would start a root terminal for this (or do 'sudo su' to get to a root prompt) to keep things simple.

You'll need to replace "/etc" in the examples below with the correct absolute path. Or cd to your hard drive's /etc and use "." in place of "/etc".

1st fix the directories. These generally have to be writable by root but readable and executable by everyone.
```
find /etc -type d -exec chmod 755 {} \; 
```

Fortunately, symlinks need to have 777 permissions and 'chmod -R' doesn't alter the link targets.

Next, you want to fix the files. For these, we generally want the same pattern as for the directories, without execute permissions.
```
find /etc -type f -exec chmod 644 {} \; 
```

/etc contains many executable shell scripts. Fortunately, most of these have the .sh extension.
```
find /etc -iname "*.sh" -type f -exec chmod 755 {} \; 
```

Finally, the tough part--you need to restrict any files that should not be readable by anyone other than root.

To help you out, I've done a 'ls -lr' of my /etc and deleted all the lines the previous commands would have corrected. This may not fix all the files on your system, but it should cover the most critical ones, since they'll be part of the base system.

```
/etc:
-rw-------  1 root root         0 2008-04-22 13:03 .pwd.lock
-rw-r-----  1 root daemon     144 2007-02-20 08:05 at.deny
drwxr-s---  2 root dip       4096 2009-07-25 06:12 chatscripts/
-rw-r-----  1 root fuse       216 2008-02-26 12:25 fuse.conf
-rw-------  1 root root      1051 2009-08-02 23:59 group-
-rw-r-----  1 root shadow     897 2009-08-02 23:59 gshadow
-rw-------  1 root root       890 2009-08-02 23:59 gshadow-
-rw-------  1 root root      1816 2009-07-25 08:00 passwd-
-rwxr-xr-x  1 root root       306 2008-04-22 13:03 rc.local*
-rwxr-xr-x  1 root root       268 2008-04-04 06:06 rmt*
-rw-rw----  1 root sasl     12288 2008-04-29 08:03 sasldb2
-rw-r-----  1 root shadow    1151 2009-07-25 08:01 shadow
-rw-------  1 root root      1178 2009-07-25 08:00 shadow-
-r--r-----  1 root root       470 2008-04-27 16:54 sudoers
-rw-r-----  1 root dialout     66 2008-04-22 13:24 wvdial.conf

/etc/NetworkManager/dispatcher.d:
-rwxr-xr-x 1 root root 1299 2009-02-27 16:29 01ifupdown*

/etc/X11:
-rwxr-xr-x 1 root root  3730 2008-03-13 10:10 Xsession*
-rw------- 1 root root   614 2008-04-22 13:05 Xwrapper.config

/etc/X11/xinit:
-rwxr-xr-x 1 root root   98 2008-02-01 22:14 xserverrc*

/etc/alsa/modprobe-post-install.d:
-rwxr-xr-x 1 root root 400 2009-04-07 19:08 alsa-utils*

/etc/apm/event.d:
-rwxr-xr-x 1 root root 2265 2008-03-28 17:27 20hdparm*
-rwxr-xr-x 1 root root  753 2007-03-05 08:32 anacron*
-rwxr-xr-x 1 root root  961 2007-10-04 15:48 ppp*

/etc/apm/scripts.d:
-rwxr-xr-x 1 root root 216 2008-03-08 20:24 alsa*

/etc/apparmor:
-rwxr-xr-x 1 root root 13253 2009-04-08 09:40 rc.apparmor.functions*

/etc/apt:
-rw------- 1 root root    0 2008-04-22 13:04 secring.gpg
-rw------- 1 root root 1200 2008-04-22 13:04 trustdb.gpg

/etc/avahi:
-rwxr-xr-x 1 root root 2272 2008-12-18 12:43 avahi-autoipd.action*

/etc/ca-certificates/update.d:
-rwxr-xr-x 1 root root 1988 2008-11-03 01:32 jks-keystore*

/etc/chatscripts:
-rw-r----- 1 root dip  656 2008-04-22 13:19 provider

/etc/cron.daily:
-rwxr-xr-x 1 root root  311 2007-03-05 08:32 0anacron*
-rwxr-xr-x 1 root root  299 2009-04-29 09:32 apport*
-rwxr-xr-x 1 root root 8686 2009-04-16 23:26 apt*
-rwxr-xr-x 1 root root  314 2008-04-04 04:53 aptitude*
-rwxr-xr-x 1 root root  502 2007-12-12 09:31 bsdmainutils*
-rwxr-xr-x 1 root root   89 2006-06-19 14:14 logrotate*
-rwxr-xr-x 1 root root  954 2008-03-12 08:28 man-db*
-rwxr-xr-x 1 root root  646 2008-06-26 09:19 mlocate*
-rwxr-xr-x 1 root root 2149 2008-11-17 03:52 popularity-contest*
-rwxr-xr-x 1 root root 3349 2009-05-12 16:55 standard*
-rwxr-xr-x 1 root root 1309 2007-11-23 03:02 sysklogd*

/etc/cron.monthly:
-rwxr-xr-x 1 root root 313 2007-03-05 08:32 0anacron*
-rwxr-xr-x 1 root root 129 2008-04-08 13:13 standard*

/etc/cron.weekly:
-rwxr-xr-x 1 root root  312 2007-03-05 08:32 0anacron*
-rwxr-xr-x 1 root root  107 2009-01-31 08:44 apt-xapian-index*
-rwxr-xr-x 1 root root  528 2008-03-12 08:28 man-db*
-rwxr-xr-x 1 root root 2016 2008-10-20 11:14 popularity-contest*
-rwxr-xr-x 1 root root 1220 2007-11-23 03:02 sysklogd*

/etc/cups:
-rw------- 1 root lp     82 2009-08-28 20:33 classes.conf
-rw------- 1 root lp    754 2009-09-11 18:08 printers.conf
-rw------- 1 root lp    714 2009-09-06 18:35 printers.conf.O
drwx------ 2 root lp   4096 2008-04-22 13:05 ssl/
-rw-r----- 1 root lp    110 2009-08-30 05:33 subscriptions.conf
-rw-r----- 1 root lp    395 2009-08-28 20:35 subscriptions.conf.O

/etc/dbus-1/event.d:
-rwxr-xr-x 1 root root 1684 2008-03-31 16:19 26NetworkManagerDispatcher.dpkg-backup*

/etc/default:
-rw------- 1 root root  384 2008-11-03 01:32 cacerts
-r--r--r-- 1 root root 1919 2009-07-25 06:14 console-setup

/etc/dhcp3/dhclient-enter-hooks.d:
-rwxr-xr-x 1 root root 1037 2008-12-18 12:43 avahi-autoipd*
-rwxr-xr-x 1 root root 1736 2009-03-27 14:36 samba*

/etc/dhcp3/dhclient-exit-hooks.d:
-rwxr-xr-x 1 root root 1039 2008-12-18 12:43 zzz_avahi-autoipd*

/etc/gdm:
-rwxr-xr-x 1 root root  4182 2008-04-21 11:04 XKeepsCrashing*
-rwxr-xr-x 1 root root  6259 2008-05-13 10:33 Xsession*
-rwxr-xr-x 1 root root  8620 2009-03-17 03:59 failsafeDexconf*
-rwxr-xr-x 1 root root  4582 2008-10-23 08:40 failsafeXServer*
-rwxr-xr-x 1 root root  8528 2009-03-26 13:52 failsafeXinit*

/etc/gdm/Init:
-rwxr-xr-x 1 root root 2670 2009-04-03 03:28 Default*

/etc/gdm/PostLogin:
-rwxr-xr-x 1 root root 443 2008-04-21 11:04 Default.sample*

/etc/gdm/PostSession:
-rwxr-xr-x 1 root root 339 2008-10-15 05:09 Default*

/etc/gdm/PreSession:
-rwxr-xr-x 1 root root 1744 2008-10-15 05:09 Default*

/etc/gre.d:
-rwxr-xr-x 1 root root 78 2009-09-02 12:36 1.9.0.14.system.conf*

/etc/grub.d:
-rwxr-xr-x 1 root root 407 2009-03-27 15:12 20_memtest86+*

/etc/init.d:
-rwxr-xr-x 1 root root  1822 2009-04-14 07:37 NetworkManager*
-rwxr-xr-x 1 root root  1766 2008-03-31 16:19 NetworkManager.dpkg-backup*
-rwxr-xr-x 1 root root   762 2007-08-30 21:48 acpi-support*
-rwxr-xr-x 1 root root  3187 2009-04-22 14:45 acpid*
-rwxr-xr-x 1 root root 10150 2009-04-07 19:08 alsa-utils*
-rwxr-xr-x 1 root root  1297 2008-09-02 18:38 anacron*
-rwxr-xr-x 1 root root  2727 2009-04-08 09:39 apparmor*
-rwxr-xr-x 1 root root  2630 2009-04-06 18:45 apport*
-rwxr-xr-x 1 root root  1018 2008-07-10 10:02 atd*
-rwxr-xr-x 1 root root  2590 2009-03-23 05:17 avahi-daemon*
-rwxr-xr-x 1 root root  4524 2008-10-26 19:28 bluetooth*
-rwxr-xr-x 1 root root  2231 2008-10-14 08:02 bootlogd*
-rwxr-xr-x 1 root root  2031 2009-03-17 22:48 brltty*
-rwxr-xr-x 1 root root  1670 2008-11-27 12:48 console-setup*
-rwxr-xr-x 1 root root  2653 2009-05-12 16:55 cron*
-rwxr-xr-x 1 root root  2526 2009-06-01 10:26 cups*
-rwxr-xr-x 1 root root  4632 2009-07-07 11:01 dbus*
-rwxr-xr-x 1 root root  8040 2009-03-05 10:31 dkms_autoinstaller*
-rwxr-xr-x 1 root root  1235 2009-02-20 11:56 dns-clean*
-rwxr-xr-x 1 root root  3598 2009-04-03 03:26 gdm*
-rwxr-xr-x 1 root root  2091 2008-10-26 03:56 hal*
-rwxr-xr-x 1 root root  1329 2008-10-14 08:02 halt*
-rwxr-xr-x 1 root root   917 2009-04-06 09:32 hotkey-setup*
-rwxr-xr-x 1 root root  1404 2008-11-27 12:48 keyboard-setup*
-rwxr-xr-x 1 root root  1484 2008-10-14 08:02 killprocs*
-rwxr-xr-x 1 root root  1816 2009-01-23 12:48 klogd*
-rwxr-xr-x 1 root root  2290 2009-03-30 03:37 laptop-mode*
-rwxr-xr-x 1 root root   349 2008-04-10 17:57 linux-restricted-modules-common*
-rwxr-xr-x 1 root root  1399 2008-02-25 15:20 module-init-tools*
-rwxr-xr-x 1 root root  1321 2008-10-14 08:02 mountoverflowtmp*
-rwxr-xr-x 1 root root  5755 2008-03-27 21:34 mysql*
-rwxr-xr-x 1 root root  2515 2008-03-27 21:34 mysql-ndb*
-rwxr-xr-x 1 root root  1905 2008-03-27 21:34 mysql-ndb-mgm*
-rwxr-xr-x 1 root root  2211 2008-06-19 02:48 nethack-common*
-rwxr-xr-x 1 root root  2417 2009-03-05 09:02 networking*
-rwxr-xr-x 1 root root   882 2009-03-31 04:11 ondemand*
-rwxr-xr-x 1 root root  2398 2009-03-09 11:46 pcmciautils*
-rwxr-xr-x 1 root root   687 2008-10-08 02:03 policykit*
-rwxr-xr-x 1 root root  4695 2008-09-03 09:34 postfix*
-rwxr-xr-x 1 root root   420 2009-02-20 12:25 pppd-dns*
-rwxr-xr-x 1 root root  1247 2009-03-18 17:35 procps*
-rwxr-xr-x 1 root root  2186 2009-07-14 13:25 pulseaudio*
-rwxr-xr-x 1 root root 10042 2009-03-31 04:01 rc*
-rwxr-xr-x 1 root root   788 2008-10-14 08:02 rc.local*
-rwxr-xr-x 1 root root   117 2009-03-31 04:01 rcS*
-rwxr-xr-x 1 root root  1758 2008-10-27 07:23 readahead*
-rwxr-xr-x 1 root root  2180 2008-10-27 07:23 readahead-desktop*
-rwxr-xr-x 1 root root   639 2008-10-14 08:02 reboot*
-rwxr-xr-x 1 root root   941 2008-10-14 08:02 rmnologin*
-rwxr-xr-x 1 root root  5200 2009-02-26 19:55 rsync*
-rwxr-xr-x 1 root root  1713 2009-03-27 03:17 saned*
-rwxr-xr-x 1 root root  8055 2009-06-23 14:09 saslauthd*
-rwxr-xr-x 1 root root   918 2008-06-13 05:23 screen-cleanup*
-rwxr-xr-x 1 root root  2283 2008-10-14 08:02 sendsigs*
-rwxr-xr-x 1 root root   590 2008-10-14 08:02 single*
-rwxr-xr-x 1 root root  2710 2008-12-18 04:09 smartmontools*
-rwxr-xr-x 1 root root   525 2008-10-14 08:02 stop-bootlogd*
-rwxr-xr-x 1 root root  1096 2008-10-14 08:02 stop-bootlogd-single*
-rwxr-xr-x 1 root root  1063 2008-10-27 07:23 stop-readahead*
-rwxr-xr-x 1 root root  3582 2009-01-23 12:48 sysklogd*
-rwxr-xr-x 1 root root  2704 2009-04-09 22:05 system-tools-backends*
-rwxr-xr-x 1 root root  2410 2009-02-11 11:50 timidity*
-rwxr-xr-x 1 root root  3421 2009-05-14 04:26 udev*
-rwxr-xr-x 1 root root  2064 2009-04-03 10:52 ufw*
-rwxr-xr-x 1 root root  3627 2008-10-14 08:02 umountfs*
-rwxr-xr-x 1 root root  1456 2008-10-14 08:02 umountroot*
-rwxr-xr-x 1 root root  1815 2008-10-14 08:02 urandom*
-rwxr-xr-x 1 root root  2327 2009-04-08 20:47 wpa-ifupdown*
-rwxr-xr-x 1 root root  1777 2008-10-23 08:40 x11-common*

/etc/kernel/header_postinst.d:
-rwxr-xr-x 1 root root 185 2008-07-08 10:19 dkms*
-rwxr-xr-x 1 root root 462 2008-10-06 08:17 nvidia-common*

/etc/kernel/postinst.d:
-rwxr-xr-x 1 root root 185 2008-07-08 10:19 dkms*
-rwxr-xr-x 1 root root 462 2008-10-06 08:17 nvidia-common*

/etc/kernel/prerm.d:
-rwxr-xr-x 1 root root 615 2009-01-22 15:16 dkms*
-rwxr-xr-x 1 root root 146 2009-04-08 20:21 last-good-boot*

/etc/mysql:
-rwxr-xr-x 1 root root 1198 2008-03-28 00:11 debian-start*
-rw------- 1 root root  312 2008-04-28 20:49 debian.cnf

/etc/network/if-down.d:
-rwxr-xr-x 1 root root 979 2008-03-21 05:56 avahi-autoipd*
-rwxr-xr-x 1 root root 803 2008-04-18 11:50 postfix*

/etc/network/if-post-down.d:
-rwxr-xr-x 1 root root 997 2007-12-21 09:02 wireless-tools*

/etc/network/if-pre-up.d:
-rwxr-xr-x 1 root root 1235 2009-06-24 12:57 dhclient3-apparmor*
-rwxr-xr-x 1 root root 2280 2008-11-14 15:21 wireless-tools*

/etc/network/if-up.d:
-rwxr-xr-x 1 root root  886 2008-03-21 05:56 avahi-autoipd*
-rwxr-xr-x 1 root root  504 2008-03-21 05:56 avahi-daemon*
-rwxr-xr-x 1 root root 4297 2008-10-14 08:02 mountnfs*
-rwxr-xr-x 1 root root 1171 2009-05-13 16:09 ntpdate*
-rwxr-xr-x 1 root root 1120 2008-04-18 11:50 postfix*

/etc/pm/sleep.d:
-rwxr-xr-x 1 root root 366 2009-03-30 03:37 99laptop-mode*

/etc/postfix:
-rwxr-xr-x 1 root root 22774 2008-04-18 11:50 post-install*
-rwxr-xr-x 1 root root  7421 2008-04-18 11:50 postfix-script*
-rw------- 1 root root   117 2008-07-13 19:14 sasl_passwd
-rw------- 1 root root 12288 2008-07-13 19:20 sasl_passwd.db
-rw------- 1 root root    59 2008-05-09 20:15 sasl_passwd.ori

/etc/postfix/ssl:
-rw------- 1 root root  963 2008-04-29 08:22 smtpd.key.~1~

/etc/power/event.d:
-rwxr-xr-x 1 root root 811 2007-12-11 17:00 laptop-mode*

/etc/power/scripts.d:
-rwxr-xr-x 1 root root 874 2009-03-30 03:37 laptop-mode*

/etc/ppp:
-rw------- 1 root root    80 2008-04-22 13:19 chap-secrets
-rwxr-xr-x 1 root root  1754 2007-10-04 15:48 ip-down*
-rwxr-xr-x 1 root root  1892 2007-10-04 15:48 ip-up*
-rwxr-xr-x 1 root root   784 2007-10-04 15:48 ipv6-down*
-rwxr-xr-x 1 root root   922 2007-10-04 15:48 ipv6-up*
-rw------- 1 root root  1628 2008-04-22 13:19 pap-secrets
drwxr-s--- 2 root dip   4096 2009-07-24 23:21 peers/
-rwxr-xr-x 1 root root   137 2007-10-04 15:48 pppoe_on_boot*

/etc/ppp/ip-down.d:
-rwxr-xr-x 1 root root  559 2007-10-04 15:48 0000usepeerdns*
-rwxr-xr-x 1 root root 2204 2007-06-21 23:55 0dns-down*
-rwxr-xr-x 1 root root  803 2008-04-18 11:50 postfix*

/etc/ppp/ip-up.d:
-rwxr-xr-x 1 root root  891 2007-10-04 15:48 0000usepeerdns*
-rwxr-xr-x 1 root root 4024 2007-06-21 23:55 0dns-up*
-rwxr-xr-x 1 root root 1120 2008-04-18 11:50 postfix*

/etc/ppp/peers:
-rw-r----- 1 root dip  1093 2008-04-22 13:19 provider

/etc/resolvconf/update-libc.d:
-rwxr-xr-x 1 root root 249 2008-03-21 05:56 avahi-daemon*
-rwxr-xr-x 1 root root 221 2008-04-18 11:50 postfix*

/etc/security:
-rwxr-xr-x 1 root root 1003 2009-03-25 06:25 namespace.init*
-rw------- 1 root root    0 2008-04-22 13:03 opasswd

/etc/smartmontools/run.d:
-rwxr-xr-x 1 root root 146 2007-12-06 08:58 10mail*

/etc/ssl:
drwx--x--- 2 root ssl-cert  4096 2008-04-27 16:55 private/

/etc/ssl/private:
-rw-r----- 1 root ssl-cert 887 2008-04-27 16:55 ssl-cert-snakeoil.key

```

HTH

"Should any member of your I.M. force be caught or killed, the Secretary will disavow any knowledge of your actions. Good luck, Jim."

---

### Post by Spencer Caplan on 2009-10-04
I sympathize with your mistake. Last week I was experimenting with some different things trying to learn more and I ended up doing the same thing to my permissions. Here is what I ended up doing to remedy my situation, (I realize it is not the most desirable solution.) I booted from the LiveCD, gathered all of the data which I needed to save and put it on a flash drive. I then reinstalled Ubuntu and put my needed data back on my harddrive from the flash drive.

---

### Post by fela on 2009-10-04
I was going to say what barthel said.

Just remember to be careful with recursive permissions in the future, and especially when they're coupled with root privileges.

---

