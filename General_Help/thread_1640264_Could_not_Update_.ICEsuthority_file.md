---
title: "Could not Update .ICEsuthority file"
date: 2010-12-07
forum: General Help
---

### Post by Jonny87 on 2010-12-07
I'm getting an error on boot that says 
> Could not Update .ICEauthority file
/var/lib/gdm/.ICEauthority 

It then goes to the login screen but no users show up and I can't do anything from there. If I drop it to te comand line with Ctrl + Alt + F1 I can login to the users as normal and run commands.

I've done some searching but haven't found any solutions as such. I've checked the permissions of the file and the seem to correct. 

Please is there a way to fix this? I don't want to do a full re-install as I have a lot to reconfigure.

---

### Post by Jonny87 on 2010-12-07
I've recently found that by creating or deleting a user at the command line I get temporary success in the graphical environment. The users show up in the login screen and I can login but on the next reboot its back to the way it was in the above message.

Not sure if this means anything to any one.

---

### Post by WorMzy on 2010-12-07
After logging in at a tty, can you run
```
sudo ls -la /var/lib/gdm/
```
and post the output here.

---

### Post by Jonny87 on 2010-12-08
> **WorMzy said:**
> After logging in at a tty, can you run
```
sudo ls -la /var/lib/gdm/
```and post the output here.

```

drw-xr-x 3 hplip gdm 4096 2010-10-17 21:33 .cache
drw----- 4 hplip gdm 4096 2010-10-17 21:33 .config
drw----- 3 hplip gdm 4096 2010-10-08 18:36 .dbus
-rw----- 1 hplip gdm 16 2010-10-08 18:36 .esd_auth
drw-xr-x 2 hplip gdm 4096 2010-10-08 18:36 .fontconfig
drw----- 4 hplip gdm 4096 2010-11-24 11:17 .gconf
drw----- 2 hplip gdm 4096 2010-11-24 11:18 .gconfd
drwxr-xr-x  2 hplip  gdm  4096 2010-11-24 11:17 .gconf.defaults
drwxr-xr-x  2 hplip  gdm  4096 2010-10-17 20:50 .gconf.mandatory
-rw-r--r--  1 hplip  gdm   389 2010-09-14 01:48 .gconf.path
-rw-------  1 hplip  gdm  31188 2010-11-24 11:17 .ICEauthority
drwx------  3 hplip  gdm  4096 2010-10-14 19:11 .kde
drwx------  2 hplip  gdm  4096 2010-11-24 19:17 .pulse
-rw-------  1 hplip  gdm   256 2010-10-08 18:36 .pulse-cookie


```

---

### Post by Jonny87 on 2010-12-08
Ok after looking at the above results and comparing it with my laptop I changed the ownership from hplip to gdm and it booted fine but I still have no users showing up on the login screen but I can still login fine via the command line.

Any ideas any one?

---

### Post by WorMzy on 2010-12-09
Did you ```
chown -R gdm /var/lib/gdm/
``` or just ```
chown gdm /var/lib/gdm/
```?

Using the -R flag will change the subfolder's content ownership to gdm, and not just the top level folder's content. Don't use this on lower level folders though, unless you know what you're doing.

I fear the problem may run a bit deeper than that though. Can you run

```
ls -la /var/lib
```
```
ls -la /var
```
```
ls -la /
```

You don't need to post the output here, you already seem to know what you're looking for. I'm just wondering how far down the folder hierarchy hplip has taken ownership.

Here's mine for contrast:
/var/lib:
```
drwxr-xr-x 26 root   root   4096 Dec  8 09:33 .
drwxr-xr-x 13 root   root   4096 Nov 18 19:15 ..
drwxr-xr-x  2 root   root   4096 Nov 18 20:59 alsa
drwxr-xr-x  2 root   root   4096 Oct 19 14:02 arpd
drwxr-xr-x  4 root   root   4096 Nov 25 13:45 bluetooth
drwxr-xr-x  2 clamav clamav 4096 Dec  9 09:45 clamav
drwxr-xr-x  2 root   root   4096 Jun 13 08:39 dbus
drwxr-xr-x  2 root   root   4096 Jun 21 23:32 dhcpcd
drwxrwxrwt  2 root   root   4096 Mar  7  2010 ex
drwxrwx--T 16 gdm    gdm    4096 Dec  9 09:45 gdm
drwxr-xr-x  2 root   root   4096 Jun 13 10:17 hwclock
drwxr-x---  2 root   locate 4096 Oct 26 02:54 locate
-rw-r--r--  1 root   root    810 Dec  8 19:23 logrotate.status
drwxr-xr-x  2 root   root   4096 Jun 13 10:20 misc
drwxr-x---  2 root   locate 4096 Dec  8 19:23 mlocate
drwxr-xr-x  5 mpd    mpd    4096 Dec  3 11:00 mpd
drwx------  7 mysql  mysql  4096 Dec  9 09:45 mysql
drwxr-xr-x  2 root   root   4096 Dec  8 20:01 ntp
drwxr-xr-x  4 root   root   4096 Dec  9 09:55 pacman
drwx------  3 root   root   4096 Dec  7 08:44 polkit-1
drwxr-xr-x  2 root   root   4096 Sep 12  2008 rarian
drwx------  3 root   root   4096 Nov 18 17:25 sudo
drwxr-xr-x  2 root   root   4096 Jun 13 10:20 syslog-ng
drwx------  2 root   root   4096 Dec  9 09:46 udisks
drwxr-xr-x  2 root   root   4096 Nov 28 17:48 upower
drwxr-xr-x  3 root   root   4096 Nov 18 18:07 wicd
drwxr-xr-x  2 root   root   4096 Dec  9 09:45 xkb
```
/var:
```
drwxr-xr-x 13 root root  4096 Nov 18 19:15 .
drwxr-xr-x 22 root root  4096 Nov 25 14:58 ..
drwxr-xr-x  9 root root  4096 Jun 19 11:29 cache
drwxr-xr-x  2 root root  4096 Oct 24 10:56 empty
drwxrwxr-x  2 root games 4096 Oct 24 10:56 games
drwxr-xr-x 26 root root  4096 Dec  8 09:33 lib
drwxr-xr-x  2 root root  4096 Oct 24 10:56 local
drwxrwxrwt  3 root root  4096 Dec  3 23:17 lock
drwxr-xr-x  9 root root  4096 Dec  9 09:45 log
lrwxrwxrwx  1 root root    10 Oct 24 10:56 mail -> spool/mail
drwxr-xr-x  2 root root  4096 Oct 24 10:56 opt
drwxr-xr-x 19 root root  4096 Dec  9 09:45 run
drwxr-xr-x  5 root root  4096 Nov 18 17:18 spool
drwxrwxrwt  3 root root  4096 Dec  9 10:12 tmp
```
/:
```
drwxr-xr-x  21 root root  4096 Dec  9 10:15 .
drwxr-xr-x  21 root root  4096 Dec  9 10:15 ..
drwxr-xr-x   2 root root  4096 Nov 23 12:45 bin
drwxr-xr-x   2 root root  4096 Nov 26 00:50 boot
drwxr-xr-x  17 root root  6080 Dec  9 09:45 dev
drwxr-xr-x  69 root root  4096 Dec  9 09:55 etc
drwxr-xr-x   3 root root  4096 Jun 19 11:31 home
drwxr-xr-x   9 root root  4096 Dec  8 09:33 lib
drwxr-xr-x   2 root root  4096 Oct 26 00:28 lib64
drwx------   2 root root 16384 Jun 13 08:21 lost+found
drwxr-xr-x   4 root root  4096 Dec  9 09:46 media
drwxr-xr-x   2 root root  4096 Oct 24 10:56 mnt
drwxr-xr-x   3 root root  4096 Nov 20 17:15 opt
dr-xr-xr-x 171 root root     0 Dec  9 09:45 proc
drwxr-x---  19 root root  4096 Dec  8 22:15 root
drwxr-xr-x   2 root root  4096 Dec  8 09:33 sbin
drwxr-xr-x   5 root root  4096 Nov 18 17:19 srv
drwxr-xr-x  13 root root     0 Dec  9 09:45 sys
drwxrwxrwt  10 root root  4096 Dec  9 10:13 tmp
drwxr-xr-x  11 root root  4096 Nov 26 00:50 usr
drwxr-xr-x  13 root root  4096 Nov 18 19:15 var
```

---

