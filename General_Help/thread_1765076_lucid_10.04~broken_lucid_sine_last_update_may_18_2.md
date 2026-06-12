---
title: "lucid 10.04~broken lucid sine last update may 18 2011!"
date: 2011-05-22
forum: General Help
---

### Post by KEE on 2011-05-22
hello, 
ever since last update everything went wrong. heres some pics of codes that dont work and some pics of what i thought was cause of my drive was full but threres something deeper.... the two bottom pics I have no idea whats up with the hieroglyphics around recovery  ```
**@**:~$ sudo aptitude safe-upgrade
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: The list of sources could not be read.
Segmentation fault
**@**:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
**@**:~$ sudo aptitude update
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: The list of sources could not be read.
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: The list of sources could not be read.
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
E: Couldn't read list of package sources
```
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-13.png[/IMG]
[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Image0097.jpg[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Image0096.jpg[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Image0095.jpg[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Image0094.jpg[/IMG][IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Image0093.jpg[/IMG]

---

### Post by kostkon on 2011-05-22
Yes, it could be a hardware problem.

But, could you paste here the output of some of your logs? give the following commands, one line at a time:
```
gedit /etc/apt/sources.list
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
gedit /var/log/dpkg.log
gedit /var/log/syslog
```
also, do a
```
sudo apt-get update
```
and paste its output here, as always.

Also, could you give some more info. You posted some images without explaining your problem in detail.

---

### Post by KEE on 2011-05-22
ok 
```
gedit /etc/apt/sources.list
``````
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by KEE on 2011-05-22
```
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``````
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
n
```

---

### Post by KEE on 2011-05-22
```
gedit /var/log/dpkg.log
``````
2011-05-01 09:56:13 startup packages purge
2011-05-01 09:56:13 status installed wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 remove wine1.2-gecko 1.0.0-0ubuntu4 1.0.0-0ubuntu4
2011-05-01 09:56:20 status half-configured wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 status half-installed wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 status config-files wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 status config-files wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 status config-files wine1.2-gecko 1.0.0-0ubuntu4
2011-05-01 09:56:20 status not-installed wine1.2-gecko <none>
2011-05-01 14:37:48 startup packages remove
2011-05-01 14:37:48 status installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:53 remove wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:53 status half-configured wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:53 status half-installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:54 status config-files wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:54 status config-files wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:54 status config-files wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:54 status not-installed wine1.3-dev <none>
2011-05-01 14:37:55 startup packages purge
2011-05-01 14:37:55 status installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:55 remove wine1.3 1.3.17-0ubuntu1~lucid1~ppa1 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:55 status half-configured wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:56 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:58 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-01 14:37:58 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:58 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:37:58 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:58 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:37:58 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:37:58 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-01 14:37:58 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:00 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-05-01 14:38:00 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:00 purge wine1.3 1.3.17-0ubuntu1~lucid1~ppa1 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:00 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:00 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:00 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:01 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:01 status config-files wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:38:01 status not-installed wine1.3 <none>
2011-05-01 14:38:01 status installed wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 remove wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status half-configured wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status half-installed wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status config-files wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status config-files wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status config-files wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:38:01 status not-installed wine1.3-gecko <none>
2011-05-01 14:38:01 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-01 14:38:01 status half-configured man-db 2.5.7-2ubuntu1
2011-05-01 14:38:03 status installed man-db 2.5.7-2ubuntu1
2011-05-01 14:38:03 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-01 14:38:03 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:38:03 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:38:03 status triggers-pending python-support 1.0.4ubuntu1
2011-05-01 14:38:03 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-01 14:38:03 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:38:03 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:38:03 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-01 14:38:03 status half-configured hicolor-icon-theme 0.11-1
2011-05-01 14:38:09 status installed hicolor-icon-theme 0.11-1
2011-05-01 14:38:09 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-05-01 14:38:09 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-05-01 14:38:10 status installed libc-bin 2.11.1-0ubuntu7.8
2011-05-01 14:38:10 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-01 14:38:10 status half-configured python-support 1.0.4ubuntu1
2011-05-01 14:38:18 status installed python-support 1.0.4ubuntu1
2011-05-01 14:38:18 startup packages remove
2011-05-01 14:38:18 status installed wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 remove wisotool 0.0+20110312-0ubuntu1~ppa1 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status half-configured wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status half-installed wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status config-files wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status config-files wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status config-files wisotool 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:19 status not-installed wisotool <none>
2011-05-01 14:38:20 startup packages purge
2011-05-01 14:38:20 status installed winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 remove winetricks 0.0+20110312-0ubuntu1~ppa1 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status half-configured winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status half-installed winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:38:20 status half-installed winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:38:20 status half-installed winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-01 14:38:20 status half-installed winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status config-files winetricks 0.0+20110312-0ubuntu1~ppa1
2011-05-01 14:38:20 status not-installed winetricks <none>
2011-05-01 14:38:20 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-01 14:38:20 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:38:21 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:38:21 status triggers-pending python-support 1.0.4ubuntu1
2011-05-01 14:38:21 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-01 14:38:21 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:38:21 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:38:21 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-01 14:38:21 status half-configured hicolor-icon-theme 0.11-1
2011-05-01 14:38:21 status installed hicolor-icon-theme 0.11-1
2011-05-01 14:38:21 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-01 14:38:21 status half-configured python-support 1.0.4ubuntu1
2011-05-01 14:38:22 status installed python-support 1.0.4ubuntu1
2011-05-01 14:39:04 startup archives unpack
2011-05-01 14:39:04 install wine1.3 <none> 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:04 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:05 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-01 14:39:05 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:05 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:39:05 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:05 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:39:05 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:05 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-01 14:39:05 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:15 status unpacked wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:15 status unpacked wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:15 install wine1.3-dev <none> 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:15 status half-installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:18 status unpacked wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:18 status unpacked wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:18 install wine1.3-gecko <none> 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:18 status half-installed wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:20 status unpacked wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:20 status unpacked wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:20 install winetricks <none> 0.0+20110417~ppa1
2011-05-01 14:39:20 status half-installed winetricks 0.0+20110417~ppa1
2011-05-01 14:39:20 status half-installed winetricks 0.0+20110417~ppa1
2011-05-01 14:39:20 status half-installed winetricks 0.0+20110417~ppa1
2011-05-01 14:39:20 status half-installed winetricks 0.0+20110417~ppa1
2011-05-01 14:39:21 status unpacked winetricks 0.0+20110417~ppa1
2011-05-01 14:39:21 status unpacked winetricks 0.0+20110417~ppa1
2011-05-01 14:39:21 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-01 14:39:21 status half-configured hicolor-icon-theme 0.11-1
2011-05-01 14:39:21 status installed hicolor-icon-theme 0.11-1
2011-05-01 14:39:21 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-01 14:39:21 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:39:21 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-01 14:39:21 status triggers-pending python-support 1.0.4ubuntu1
2011-05-01 14:39:21 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-01 14:39:21 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:39:22 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-01 14:39:22 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-01 14:39:22 status half-configured man-db 2.5.7-2ubuntu1
2011-05-01 14:39:22 status installed man-db 2.5.7-2ubuntu1
2011-05-01 14:39:22 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-01 14:39:22 status half-configured python-support 1.0.4ubuntu1
2011-05-01 14:39:23 status installed python-support 1.0.4ubuntu1
2011-05-01 14:39:24 startup packages configure
2011-05-01 14:39:24 configure wine1.3 1.3.17-0ubuntu1~lucid1~ppa1 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:24 status unpacked wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:24 status unpacked wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:24 status half-configured wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 status installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-05-01 14:39:25 configure wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 status unpacked wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 status half-configured wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 status installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-01 14:39:25 configure wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:25 status unpacked wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:25 status half-configured wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:25 status installed wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1
2011-05-01 14:39:25 configure winetricks 0.0+20110417~ppa1 0.0+20110417~ppa1
2011-05-01 14:39:25 status unpacked winetricks 0.0+20110417~ppa1
2011-05-01 14:39:25 status half-configured winetricks 0.0+20110417~ppa1
2011-05-01 14:39:25 status installed winetricks 0.0+20110417~ppa1
2011-05-01 14:39:25 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-05-01 14:39:25 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-05-01 14:39:25 status installed libc-bin 2.11.1-0ubuntu7.8
2011-05-01 19:55:13 startup archives unpack
2011-05-01 19:55:20 upgrade google-chrome-stable 10.0.648.205-r81283 11.0.696.57-r82915
2011-05-01 19:55:20 status half-configured google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:20 status unpacked google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:20 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:21 status triggers-pending menu 2.1.43ubuntu1
2011-05-01 19:55:21 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:21 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-01 19:55:21 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:21 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:55:21 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:21 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:55:21 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:28 status half-installed google-chrome-stable 10.0.648.205-r81283
2011-05-01 19:55:28 status unpacked google-chrome-stable 11.0.696.57-r82915
2011-05-01 19:55:28 status unpacked google-chrome-stable 11.0.696.57-r82915
2011-05-01 19:55:28 upgrade tzdata-java 2011e-0ubuntu0.10.04 2011g-0ubuntu0.10.04
2011-05-01 19:55:28 status half-configured tzdata-java 2011e-0ubuntu0.10.04
2011-05-01 19:55:28 status unpacked tzdata-java 2011e-0ubuntu0.10.04
2011-05-01 19:55:28 status half-installed tzdata-java 2011e-0ubuntu0.10.04
2011-05-01 19:55:32 status half-installed tzdata-java 2011e-0ubuntu0.10.04
2011-05-01 19:55:33 status unpacked tzdata-java 2011g-0ubuntu0.10.04
2011-05-01 19:55:33 status unpacked tzdata-java 2011g-0ubuntu0.10.04
2011-05-01 19:55:33 upgrade tzdata 2011e-0ubuntu0.10.04 2011g-0ubuntu0.10.04
2011-05-01 19:55:33 status half-configured tzdata 2011e-0ubuntu0.10.04
2011-05-01 19:55:33 status unpacked tzdata 2011e-0ubuntu0.10.04
2011-05-01 19:55:33 status half-installed tzdata 2011e-0ubuntu0.10.04
2011-05-01 19:55:37 status half-installed tzdata 2011e-0ubuntu0.10.04
2011-05-01 19:55:37 status unpacked tzdata 2011g-0ubuntu0.10.04
2011-05-01 19:55:38 status unpacked tzdata 2011g-0ubuntu0.10.04
2011-05-01 19:55:38 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-01 19:55:38 status half-configured menu 2.1.43ubuntu1
2011-05-01 19:55:39 status installed menu 2.1.43ubuntu1
2011-05-01 19:55:39 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-01 19:55:39 status half-configured man-db 2.5.7-2ubuntu1
2011-05-01 19:55:41 status installed man-db 2.5.7-2ubuntu1
2011-05-01 19:55:41 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-01 19:55:41 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:55:42 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:55:42 status triggers-pending python-support 1.0.4ubuntu1
2011-05-01 19:55:42 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-01 19:55:42 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:55:42 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:55:42 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-01 19:55:42 status half-configured python-support 1.0.4ubuntu1
2011-05-01 19:55:48 status installed python-support 1.0.4ubuntu1
2011-05-01 19:55:48 startup packages configure
2011-05-01 19:55:48 configure tzdata 2011g-0ubuntu0.10.04 2011g-0ubuntu0.10.04
2011-05-01 19:55:48 status unpacked tzdata 2011g-0ubuntu0.10.04
2011-05-01 19:55:48 status half-configured tzdata 2011g-0ubuntu0.10.04
2011-05-01 19:55:49 status installed tzdata 2011g-0ubuntu0.10.04
2011-05-01 19:55:49 startup archives unpack
2011-05-01 19:55:50 upgrade ntpdate 1:4.2.4p8+dfsg-1ubuntu2 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:55:50 status half-configured ntpdate 1:4.2.4p8+dfsg-1ubuntu2
2011-05-01 19:55:50 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2
2011-05-01 19:55:50 status half-installed ntpdate 1:4.2.4p8+dfsg-1ubuntu2
2011-05-01 19:55:51 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-01 19:55:51 status half-installed ntpdate 1:4.2.4p8+dfsg-1ubuntu2
2011-05-01 19:55:53 status half-installed ntpdate 1:4.2.4p8+dfsg-1ubuntu2
2011-05-01 19:55:53 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:55:53 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:55:53 upgrade firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:53 status half-configured firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:53 status unpacked firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:53 status half-installed firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status half-installed firefox-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status unpacked firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status unpacked firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 upgrade firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status half-configured firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status unpacked firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status half-installed firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:55:54 status half-installed firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:54 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:55:54 status half-installed firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status half-installed firefox-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status unpacked firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status unpacked firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 upgrade firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status half-configured firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status unpacked firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:55 status half-installed firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:56 status triggers-pending menu 2.1.43ubuntu1
2011-05-01 19:55:57 status half-installed firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:58 status half-installed firefox 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 upgrade firefox-3.0 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status half-configured firefox-3.0 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status unpacked firefox-3.0 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status half-installed firefox-3.0 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status half-installed firefox-3.0 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:55:59 status unpacked firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 upgrade firefox-3.0-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-configured firefox-3.0-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.0-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-installed firefox-3.0-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-installed firefox-3.0-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 upgrade firefox-3.5 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-configured firefox-3.5 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.5 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-installed firefox-3.5 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status half-installed firefox-3.5 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:00 status unpacked firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 upgrade firefox-3.5-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-configured firefox-3.5-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-installed firefox-3.5-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-installed firefox-3.5-branding 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 upgrade firefox-3.5-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-configured firefox-3.5-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-installed firefox-3.5-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status half-installed firefox-3.5-gnome-support 3.6.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 status unpacked firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:01 upgrade libapache2-mod-php5 5.3.2-1ubuntu4.7 5.3.2-1ubuntu4.8
2011-05-01 19:56:01 status half-configured libapache2-mod-php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:01 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:01 status half-installed libapache2-mod-php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:02 status half-installed libapache2-mod-php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:02 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:02 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:02 upgrade php5-common 5.3.2-1ubuntu4.7 5.3.2-1ubuntu4.8
2011-05-01 19:56:02 status half-configured php5-common 5.3.2-1ubuntu4.7
2011-05-01 19:56:02 status unpacked php5-common 5.3.2-1ubuntu4.7
2011-05-01 19:56:02 status half-installed php5-common 5.3.2-1ubuntu4.7
2011-05-01 19:56:03 status half-installed php5-common 5.3.2-1ubuntu4.7
2011-05-01 19:56:03 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:03 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:03 upgrade libnautilus-extension1 1:2.30.1-0ubuntu1.1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:03 status half-configured libnautilus-extension1 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:03 status unpacked libnautilus-extension1 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:03 status half-installed libnautilus-extension1 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:03 status half-installed libnautilus-extension1 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:03 status unpacked libnautilus-extension1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:03 status unpacked libnautilus-extension1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:04 upgrade libpcsclite1 1.5.3-1ubuntu4.1 1.5.3-1ubuntu4.2
2011-05-01 19:56:04 status half-configured libpcsclite1 1.5.3-1ubuntu4.1
2011-05-01 19:56:04 status unpacked libpcsclite1 1.5.3-1ubuntu4.1
2011-05-01 19:56:04 status half-installed libpcsclite1 1.5.3-1ubuntu4.1
2011-05-01 19:56:04 status half-installed libpcsclite1 1.5.3-1ubuntu4.1
2011-05-01 19:56:04 status unpacked libpcsclite1 1.5.3-1ubuntu4.2
2011-05-01 19:56:04 status unpacked libpcsclite1 1.5.3-1ubuntu4.2
2011-05-01 19:56:04 upgrade libpq5 8.4.7-0ubuntu0.10.04 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:04 status half-configured libpq5 8.4.7-0ubuntu0.10.04
2011-05-01 19:56:04 status unpacked libpq5 8.4.7-0ubuntu0.10.04
2011-05-01 19:56:04 status half-installed libpq5 8.4.7-0ubuntu0.10.04
2011-05-01 19:56:04 status half-installed libpq5 8.4.7-0ubuntu0.10.04
2011-05-01 19:56:04 status unpacked libpq5 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:04 status unpacked libpq5 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:04 upgrade nautilus-data 1:2.30.1-0ubuntu1.1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:04 status half-configured nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:06 status unpacked nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:06 status half-installed nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:06 status triggers-pending shared-mime-info 0.71-1ubuntu2
2011-05-01 19:56:06 status half-installed nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:06 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-01 19:56:06 status half-installed nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:07 status half-installed nautilus-data 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status unpacked nautilus-data 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:08 status unpacked nautilus-data 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:08 upgrade nautilus 1:2.30.1-0ubuntu1.1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:08 status half-configured nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status unpacked nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:08 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:10 status half-installed nautilus 1:2.30.1-0ubuntu1.1
2011-05-01 19:56:10 status triggers-awaited menu 2.1.43ubuntu1
2011-05-01 19:56:10 status unpacked nautilus 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:10 status unpacked nautilus 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:10 upgrade php5 5.3.2-1ubuntu4.7 5.3.2-1ubuntu4.8
2011-05-01 19:56:10 status half-configured php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:10 status unpacked php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:10 status half-installed php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:10 status half-installed php5 5.3.2-1ubuntu4.7
2011-05-01 19:56:10 status unpacked php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:10 status unpacked php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:10 upgrade rsync 3.0.7-1ubuntu1 3.0.7-1ubuntu1.1
2011-05-01 19:56:10 status half-configured rsync 3.0.7-1ubuntu1
2011-05-01 19:56:10 status unpacked rsync 3.0.7-1ubuntu1
2011-05-01 19:56:10 status half-installed rsync 3.0.7-1ubuntu1
2011-05-01 19:56:10 status half-installed rsync 3.0.7-1ubuntu1
2011-05-01 19:56:11 status triggers-pending ureadahead 0.100.0-4.1.3
2011-05-01 19:56:11 status half-installed rsync 3.0.7-1ubuntu1
2011-05-01 19:56:11 status half-installed rsync 3.0.7-1ubuntu1
2011-05-01 19:56:11 status unpacked rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:11 status unpacked rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:11 upgrade xserver-common 2:1.7.6-2ubuntu7.5 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:11 status half-configured xserver-common 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:11 status unpacked xserver-common 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:11 status half-installed xserver-common 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:11 status half-installed xserver-common 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:12 status half-installed xserver-common 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:12 status unpacked xserver-common 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:12 status unpacked xserver-common 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:12 upgrade xserver-xorg-core 2:1.7.6-2ubuntu7.5 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:12 status half-configured xserver-xorg-core 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:12 status unpacked xserver-xorg-core 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:12 status half-installed xserver-xorg-core 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:12 status half-installed xserver-xorg-core 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:14 status half-installed xserver-xorg-core 2:1.7.6-2ubuntu7.5
2011-05-01 19:56:14 status unpacked xserver-xorg-core 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:14 status unpacked xserver-xorg-core 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:14 upgrade xulrunner-1.9 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:14 status half-configured xulrunner-1.9 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:14 status unpacked xulrunner-1.9 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:14 status half-installed xulrunner-1.9 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:15 status half-installed xulrunner-1.9 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:15 status unpacked xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:15 status unpacked xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:15 upgrade xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:15 status half-configured xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:17 update-alternatives: run with --remove xulrunner /usr/bin/xulrunner-1.9.2
2011-05-01 19:56:17 update-alternatives: link group xulrunner fully removed
2011-05-01 19:56:17 status unpacked xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:17 status half-installed xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:18 status half-installed xulrunner-1.9.2 1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:19 status unpacked xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:19 status unpacked xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:19 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-01 19:56:19 status half-configured man-db 2.5.7-2ubuntu1
2011-05-01 19:56:20 status installed man-db 2.5.7-2ubuntu1
2011-05-01 19:56:20 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-01 19:56:20 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:56:20 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-01 19:56:20 status triggers-pending python-support 1.0.4ubuntu1
2011-05-01 19:56:20 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-01 19:56:20 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:56:20 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-01 19:56:20 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-01 19:56:20 status half-configured menu 2.1.43ubuntu1
2011-05-01 19:56:20 status installed menu 2.1.43ubuntu1
2011-05-01 19:56:20 trigproc shared-mime-info 0.71-1ubuntu2 0.71-1ubuntu2
2011-05-01 19:56:20 status half-configured shared-mime-info 0.71-1ubuntu2
2011-05-01 19:56:21 status installed shared-mime-info 0.71-1ubuntu2
2011-05-01 19:56:22 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-01 19:56:22 status half-configured hicolor-icon-theme 0.11-1
2011-05-01 19:56:28 status installed hicolor-icon-theme 0.11-1
2011-05-01 19:56:28 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2011-05-01 19:56:28 status half-configured ureadahead 0.100.0-4.1.3
2011-05-01 19:56:28 status installed ureadahead 0.100.0-4.1.3
2011-05-01 19:56:28 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-01 19:56:28 status half-configured python-support 1.0.4ubuntu1
2011-05-01 19:56:29 status installed python-support 1.0.4ubuntu1
2011-05-01 19:56:29 startup packages configure
2011-05-01 19:56:29 configure google-chrome-stable 11.0.696.57-r82915 11.0.696.57-r82915
2011-05-01 19:56:29 status unpacked google-chrome-stable 11.0.696.57-r82915
2011-05-01 19:56:30 status half-configured google-chrome-stable 11.0.696.57-r82915
2011-05-01 19:56:34 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/google-chrome 200
2011-05-01 19:56:34 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/google-chrome 200
2011-05-01 19:56:34 status installed google-chrome-stable 11.0.696.57-r82915
2011-05-01 19:56:35 status triggers-pending menu 2.1.43ubuntu1
2011-05-01 19:56:35 status triggers-awaited menu 2.1.43ubuntu1
2011-05-01 19:56:35 configure tzdata-java 2011g-0ubuntu0.10.04 2011g-0ubuntu0.10.04
2011-05-01 19:56:35 status unpacked tzdata-java 2011g-0ubuntu0.10.04
2011-05-01 19:56:35 status half-configured tzdata-java 2011g-0ubuntu0.10.04
2011-05-01 19:56:35 status installed tzdata-java 2011g-0ubuntu0.10.04
2011-05-01 19:56:35 configure ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status unpacked ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status half-configured ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 status installed ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
2011-05-01 19:56:35 configure php5-common 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status half-configured php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status installed php5-common 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 configure libapache2-mod-php5 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:35 status half-configured libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:36 status installed libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:36 configure libnautilus-extension1 1:2.30.1-0ubuntu1.2 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status unpacked libnautilus-extension1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status half-configured libnautilus-extension1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status installed libnautilus-extension1 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-05-01 19:56:36 configure libpcsclite1 1.5.3-1ubuntu4.2 1.5.3-1ubuntu4.2
2011-05-01 19:56:36 status unpacked libpcsclite1 1.5.3-1ubuntu4.2
2011-05-01 19:56:36 status half-configured libpcsclite1 1.5.3-1ubuntu4.2
2011-05-01 19:56:36 status installed libpcsclite1 1.5.3-1ubuntu4.2
2011-05-01 19:56:36 configure libpq5 8.4.8-0ubuntu0.10.04 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:36 status unpacked libpq5 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:36 status half-configured libpq5 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:36 status installed libpq5 8.4.8-0ubuntu0.10.04
2011-05-01 19:56:36 configure nautilus-data 1:2.30.1-0ubuntu1.2 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status unpacked nautilus-data 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:36 status half-configured nautilus-data 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 status installed nautilus-data 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 configure nautilus 1:2.30.1-0ubuntu1.2 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 status unpacked nautilus 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 status half-configured nautilus 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 status installed nautilus 1:2.30.1-0ubuntu1.2
2011-05-01 19:56:37 configure php5 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.8
2011-05-01 19:56:37 status unpacked php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:37 status half-configured php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:37 status installed php5 5.3.2-1ubuntu4.8
2011-05-01 19:56:37 configure rsync 3.0.7-1ubuntu1.1 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 status unpacked rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 status unpacked rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 status unpacked rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 status half-configured rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 status installed rsync 3.0.7-1ubuntu1.1
2011-05-01 19:56:37 configure xserver-common 2:1.7.6-2ubuntu7.6 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status unpacked xserver-common 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status half-configured xserver-common 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status installed xserver-common 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 configure xserver-xorg-core 2:1.7.6-2ubuntu7.6 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status unpacked xserver-xorg-core 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status half-configured xserver-xorg-core 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 status installed xserver-xorg-core 2:1.7.6-2ubuntu7.6
2011-05-01 19:56:37 configure xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status unpacked xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status half-configured xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status installed xulrunner-1.9 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 configure xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status unpacked xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status unpacked xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status unpacked xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 status half-configured xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:37 update-alternatives: run with --install /usr/bin/xulrunner xulrunner /usr/bin/xulrunner-1.9.2 50
2011-05-01 19:56:37 update-alternatives: link group xulrunner updated to point to /usr/bin/xulrunner-1.9.2
2011-05-01 19:56:37 status installed xulrunner-1.9.2 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox 40
2011-05-01 19:56:38 status installed firefox 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/firefox 40
2011-05-01 19:56:38 status installed firefox-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-3.0 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-3.0-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-3.5 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-3.5-branding 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 configure firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status unpacked firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status half-configured firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 status installed firefox-3.5-gnome-support 3.6.17+build3+nobinonly-0ubuntu0.10.04.1
2011-05-01 19:56:38 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-01 19:56:38 status half-configured menu 2.1.43ubuntu1
2011-05-01 19:56:38 status installed menu 2.1.43ubuntu1
2011-05-01 19:56:38 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-05-01 19:56:38 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-05-01 19:56:39 status installed libc-bin 2.11.1-0ubuntu7.8
2011-05-02 06:09:12 startup archives unpack
2011-05-02 06:09:18 install nvclock <none> 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:18 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-02 06:09:18 status half-installed nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:18 status unpacked nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:18 status unpacked nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:18 install nvclock-gtk <none> 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:18 status triggers-pending menu 2.1.43ubuntu1
2011-05-02 06:09:18 status half-installed nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:18 status unpacked nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:18 status unpacked nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:18 install nvclock-qt <none> 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:18 status half-installed nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:19 status unpacked nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:19 status unpacked nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:19 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-02 06:09:19 status half-configured man-db 2.5.7-2ubuntu1
2011-05-02 06:09:20 status installed man-db 2.5.7-2ubuntu1
2011-05-02 06:09:20 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-02 06:09:20 status half-configured menu 2.1.43ubuntu1
2011-05-02 06:09:21 status installed menu 2.1.43ubuntu1
2011-05-02 06:09:22 startup packages configure
2011-05-02 06:09:22 configure nvclock 0.8b4-1ubuntu3 0.8b4-1ubuntu3
2011-05-02 06:09:22 status unpacked nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:22 status half-configured nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:22 status installed nvclock 0.8b4-1ubuntu3
2011-05-02 06:09:22 configure nvclock-gtk 0.8b4-1ubuntu3 0.8b4-1ubuntu3
2011-05-02 06:09:22 status unpacked nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:22 status half-configured nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:22 status installed nvclock-gtk 0.8b4-1ubuntu3
2011-05-02 06:09:22 status triggers-pending menu 2.1.43ubuntu1
2011-05-02 06:09:22 status triggers-awaited menu 2.1.43ubuntu1
2011-05-02 06:09:22 configure nvclock-qt 0.8b4-1ubuntu3 0.8b4-1ubuntu3
2011-05-02 06:09:22 status unpacked nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:22 status half-configured nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:22 status installed nvclock-qt 0.8b4-1ubuntu3
2011-05-02 06:09:22 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-02 06:09:22 status half-configured menu 2.1.43ubuntu1
2011-05-02 06:09:22 status installed menu 2.1.43ubuntu1
2011-05-09 14:28:21 startup archives unpack
2011-05-09 14:28:28 upgrade perl-modules 5.10.1-8ubuntu2 5.10.1-8ubuntu2.1
2011-05-09 14:28:28 status half-configured perl-modules 5.10.1-8ubuntu2
2011-05-09 14:28:28 status unpacked perl-modules 5.10.1-8ubuntu2
2011-05-09 14:28:28 status half-installed perl-modules 5.10.1-8ubuntu2
2011-05-09 14:28:34 status half-installed perl-modules 5.10.1-8ubuntu2
2011-05-09 14:28:35 status unpacked perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:28:35 status unpacked perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:28:36 upgrade perl 5.10.1-8ubuntu2 5.10.1-8ubuntu2.1
2011-05-09 14:28:36 status half-configured perl 5.10.1-8ubuntu2
2011-05-09 14:28:36 status unpacked perl 5.10.1-8ubuntu2
2011-05-09 14:28:36 status half-installed perl 5.10.1-8ubuntu2
2011-05-09 14:28:36 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-09 14:28:36 status half-installed perl 5.10.1-8ubuntu2
2011-05-09 14:28:44 status half-installed perl 5.10.1-8ubuntu2
2011-05-09 14:28:44 status unpacked perl 5.10.1-8ubuntu2.1
2011-05-09 14:28:45 status unpacked perl 5.10.1-8ubuntu2.1
2011-05-09 14:28:45 upgrade libperl5.10 5.10.1-8ubuntu2 5.10.1-8ubuntu2.1
2011-05-09 14:28:45 status half-configured libperl5.10 5.10.1-8ubuntu2
2011-05-09 14:28:45 status unpacked libperl5.10 5.10.1-8ubuntu2
2011-05-09 14:28:45 status half-installed libperl5.10 5.10.1-8ubuntu2
2011-05-09 14:28:46 status half-installed libperl5.10 5.10.1-8ubuntu2
2011-05-09 14:28:46 status unpacked libperl5.10 5.10.1-8ubuntu2.1
2011-05-09 14:28:47 status unpacked libperl5.10 5.10.1-8ubuntu2.1
2011-05-09 14:28:47 upgrade perl-base 5.10.1-8ubuntu2 5.10.1-8ubuntu2.1
2011-05-09 14:28:47 status half-configured perl-base 5.10.1-8ubuntu2
2011-05-09 14:28:47 status unpacked perl-base 5.10.1-8ubuntu2
2011-05-09 14:28:47 status half-installed perl-base 5.10.1-8ubuntu2
2011-05-09 14:28:47 status half-installed perl-base 5.10.1-8ubuntu2
2011-05-09 14:28:49 status half-installed perl-base 5.10.1-8ubuntu2
2011-05-09 14:28:49 status unpacked perl-base 5.10.1-8ubuntu2.1
2011-05-09 14:28:49 status unpacked perl-base 5.10.1-8ubuntu2.1
2011-05-09 14:28:49 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-09 14:28:49 status half-configured man-db 2.5.7-2ubuntu1
2011-05-09 14:28:52 status installed man-db 2.5.7-2ubuntu1
2011-05-09 14:28:54 startup packages configure
2011-05-09 14:28:54 configure perl-base 5.10.1-8ubuntu2.1 5.10.1-8ubuntu2.1
2011-05-09 14:28:54 status unpacked perl-base 5.10.1-8ubuntu2.1
2011-05-09 14:28:54 status half-configured perl-base 5.10.1-8ubuntu2.1
2011-05-09 14:28:54 status installed perl-base 5.10.1-8ubuntu2.1
2011-05-09 14:28:55 startup archives unpack
2011-05-09 14:29:00 upgrade xdg-utils 1.0.2-6.1ubuntu3 1.0.2-6.1ubuntu3.1
2011-05-09 14:29:00 status half-configured xdg-utils 1.0.2-6.1ubuntu3
2011-05-09 14:29:01 status unpacked xdg-utils 1.0.2-6.1ubuntu3
2011-05-09 14:29:01 status half-installed xdg-utils 1.0.2-6.1ubuntu3
2011-05-09 14:29:01 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-09 14:29:01 status half-installed xdg-utils 1.0.2-6.1ubuntu3
2011-05-09 14:29:02 status half-installed xdg-utils 1.0.2-6.1ubuntu3
2011-05-09 14:29:02 status unpacked xdg-utils 1.0.2-6.1ubuntu3.1
2011-05-09 14:29:02 status unpacked xdg-utils 1.0.2-6.1ubuntu3.1
2011-05-09 14:29:02 upgrade google-chrome-stable 11.0.696.57-r82915 11.0.696.65-r84435
2011-05-09 14:29:02 status half-configured google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:02 status unpacked google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:02 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:05 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:05 status triggers-pending menu 2.1.43ubuntu1
2011-05-09 14:29:05 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:05 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:29:05 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:05 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:29:05 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:14 status half-installed google-chrome-stable 11.0.696.57-r82915
2011-05-09 14:29:14 status unpacked google-chrome-stable 11.0.696.65-r84435
2011-05-09 14:29:15 status unpacked google-chrome-stable 11.0.696.65-r84435
2011-05-09 14:29:16 upgrade ttf-symbol-replacement-wine1.3 1.3.17-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status half-configured ttf-symbol-replacement-wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status unpacked ttf-symbol-replacement-wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status half-installed ttf-symbol-replacement-wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status half-installed ttf-symbol-replacement-wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status unpacked ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status unpacked ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 upgrade wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status half-configured wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status unpacked wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:16 status half-installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:21 status half-installed wine1.3-dev 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:21 status unpacked wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:22 status unpacked wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:22 upgrade wine1.3 1.3.17-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:22 status half-configured wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:22 status unpacked wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:22 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:30 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:39 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-09 14:29:39 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:39 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:39 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:42 status half-installed wine1.3 1.3.17-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:45 status unpacked wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:56 status unpacked wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:29:56 upgrade winetricks 0.0+20110417~ppa1 0.0+20110429~ppa1
2011-05-09 14:29:56 status half-configured winetricks 0.0+20110417~ppa1
2011-05-09 14:29:56 status unpacked winetricks 0.0+20110417~ppa1
2011-05-09 14:29:56 status half-installed winetricks 0.0+20110417~ppa1
2011-05-09 14:29:56 status half-installed winetricks 0.0+20110417~ppa1
2011-05-09 14:29:56 status half-installed winetricks 0.0+20110417~ppa1
2011-05-09 14:29:56 status half-installed winetricks 0.0+20110417~ppa1
2011-05-09 14:29:57 status half-installed winetricks 0.0+20110417~ppa1
2011-05-09 14:29:57 status unpacked winetricks 0.0+20110429~ppa1
2011-05-09 14:29:57 status unpacked winetricks 0.0+20110429~ppa1
2011-05-09 14:29:58 upgrade apt 0.7.25.3ubuntu9.3 0.7.25.3ubuntu9.4
2011-05-09 14:29:58 status half-configured apt 0.7.25.3ubuntu9.3
2011-05-09 14:29:58 status unpacked apt 0.7.25.3ubuntu9.3
2011-05-09 14:29:58 status half-installed apt 0.7.25.3ubuntu9.3
2011-05-09 14:30:00 status half-installed apt 0.7.25.3ubuntu9.3
2011-05-09 14:30:04 status half-installed apt 0.7.25.3ubuntu9.3
2011-05-09 14:30:04 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:05 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:05 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-09 14:30:05 status half-configured man-db 2.5.7-2ubuntu1
2011-05-09 14:30:08 status installed man-db 2.5.7-2ubuntu1
2011-05-09 14:30:08 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-09 14:30:08 status half-configured menu 2.1.43ubuntu1
2011-05-09 14:30:10 status installed menu 2.1.43ubuntu1
2011-05-09 14:30:10 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-09 14:30:10 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:30:15 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:30:15 status triggers-pending python-support 1.0.4ubuntu1
2011-05-09 14:30:15 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-09 14:30:15 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:30:15 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:30:15 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-09 14:30:15 status half-configured hicolor-icon-theme 0.11-1
2011-05-09 14:30:25 status installed hicolor-icon-theme 0.11-1
2011-05-09 14:30:25 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-09 14:30:25 status half-configured python-support 1.0.4ubuntu1
2011-05-09 14:30:34 status installed python-support 1.0.4ubuntu1
2011-05-09 14:30:36 startup packages configure
2011-05-09 14:30:36 configure apt 0.7.25.3ubuntu9.4 0.7.25.3ubuntu9.4
2011-05-09 14:30:36 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status unpacked apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status half-configured apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status installed apt 0.7.25.3ubuntu9.4
2011-05-09 14:30:38 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:30:38 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-05-09 14:30:38 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:30:41 status installed libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:30:43 startup archives unpack
2011-05-09 14:30:49 upgrade apt-utils 0.7.25.3ubuntu9.3 0.7.25.3ubuntu9.4
2011-05-09 14:30:49 status half-configured apt-utils 0.7.25.3ubuntu9.3
2011-05-09 14:30:49 status unpacked apt-utils 0.7.25.3ubuntu9.3
2011-05-09 14:30:49 status half-installed apt-utils 0.7.25.3ubuntu9.3
2011-05-09 14:30:49 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-09 14:30:49 status half-installed apt-utils 0.7.25.3ubuntu9.3
2011-05-09 14:30:50 status half-installed apt-utils 0.7.25.3ubuntu9.3
2011-05-09 14:30:50 status unpacked apt-utils 0.7.25.3ubuntu9.4
2011-05-09 14:30:50 status unpacked apt-utils 0.7.25.3ubuntu9.4
2011-05-09 14:30:50 upgrade apt-transport-https 0.7.25.3ubuntu9.3 0.7.25.3ubuntu9.4
2011-05-09 14:30:50 status half-configured apt-transport-https 0.7.25.3ubuntu9.3
2011-05-09 14:30:50 status unpacked apt-transport-https 0.7.25.3ubuntu9.3
2011-05-09 14:30:50 status half-installed apt-transport-https 0.7.25.3ubuntu9.3
2011-05-09 14:30:51 status half-installed apt-transport-https 0.7.25.3ubuntu9.3
2011-05-09 14:30:51 status unpacked apt-transport-https 0.7.25.3ubuntu9.4
2011-05-09 14:30:51 status unpacked apt-transport-https 0.7.25.3ubuntu9.4
2011-05-09 14:30:51 upgrade gdm 2.30.2.is.2.30.0-0ubuntu5.1 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:30:51 status half-configured gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:54 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:54 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:54 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-09 14:30:54 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:54 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:30:54 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:54 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:30:54 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:55 status triggers-pending ureadahead 0.100.0-4.1.3
2011-05-09 14:30:56 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:57 status triggers-pending ureadahead 0.100.0-4.1.3
2011-05-09 14:30:59 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu5.1
2011-05-09 14:30:59 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:30:59 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:30:59 upgrade libapache2-mod-php5 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.9
2011-05-09 14:30:59 status half-configured libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-09 14:30:59 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-09 14:30:59 status half-installed libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:03 status half-installed libapache2-mod-php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:03 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:03 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:03 upgrade php5-common 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.9
2011-05-09 14:31:03 status half-configured php5-common 5.3.2-1ubuntu4.8
2011-05-09 14:31:03 status unpacked php5-common 5.3.2-1ubuntu4.8
2011-05-09 14:31:03 status half-installed php5-common 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status half-installed php5-common 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status unpacked php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:04 status unpacked php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:04 upgrade php5 5.3.2-1ubuntu4.8 5.3.2-1ubuntu4.9
2011-05-09 14:31:04 status half-configured php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status unpacked php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status half-installed php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status half-installed php5 5.3.2-1ubuntu4.8
2011-05-09 14:31:04 status unpacked php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:04 status unpacked php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:05 upgrade thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status half-configured thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status unpacked thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status half-installed thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status half-installed thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status half-installed thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:05 status half-installed thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:08 status half-installed thunderbird 3.1.8+build3+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:09 status unpacked thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:09 status unpacked thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:09 upgrade usb-creator 0.2.22.1 0.2.22.3
2011-05-09 14:31:09 status half-configured usb-creator 0.2.22.1
2011-05-09 14:31:09 status unpacked usb-creator 0.2.22.1
2011-05-09 14:31:09 status half-installed usb-creator 0.2.22.1
2011-05-09 14:31:10 status half-installed usb-creator 0.2.22.1
2011-05-09 14:31:10 status unpacked usb-creator 0.2.22.3
2011-05-09 14:31:10 status unpacked usb-creator 0.2.22.3
2011-05-09 14:31:10 upgrade usb-creator-gtk 0.2.22.1 0.2.22.3
2011-05-09 14:31:10 status half-configured usb-creator-gtk 0.2.22.1
2011-05-09 14:31:11 status unpacked usb-creator-gtk 0.2.22.1
2011-05-09 14:31:11 status half-installed usb-creator-gtk 0.2.22.1
2011-05-09 14:31:11 status half-installed usb-creator-gtk 0.2.22.1
2011-05-09 14:31:11 status half-installed usb-creator-gtk 0.2.22.1
2011-05-09 14:31:11 status half-installed usb-creator-gtk 0.2.22.1
2011-05-09 14:31:12 status half-installed usb-creator-gtk 0.2.22.1
2011-05-09 14:31:12 status unpacked usb-creator-gtk 0.2.22.3
2011-05-09 14:31:12 status unpacked usb-creator-gtk 0.2.22.3
2011-05-09 14:31:12 upgrade usb-creator-common 0.2.22.1 0.2.22.3
2011-05-09 14:31:12 status half-configured usb-creator-common 0.2.22.1
2011-05-09 14:31:13 status unpacked usb-creator-common 0.2.22.1
2011-05-09 14:31:13 status half-installed usb-creator-common 0.2.22.1
2011-05-09 14:31:14 status half-installed usb-creator-common 0.2.22.1
2011-05-09 14:31:14 status unpacked usb-creator-common 0.2.22.3
2011-05-09 14:31:14 status unpacked usb-creator-common 0.2.22.3
2011-05-09 14:31:14 upgrade vino 2.28.2-0ubuntu2 2.28.2-0ubuntu2.1
2011-05-09 14:31:14 status half-configured vino 2.28.2-0ubuntu2
2011-05-09 14:31:16 status unpacked vino 2.28.2-0ubuntu2
2011-05-09 14:31:16 status half-installed vino 2.28.2-0ubuntu2
2011-05-09 14:31:16 status half-installed vino 2.28.2-0ubuntu2
2011-05-09 14:31:16 status half-installed vino 2.28.2-0ubuntu2
2011-05-09 14:31:16 status half-installed vino 2.28.2-0ubuntu2
2011-05-09 14:31:17 status unpacked vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:17 status unpacked vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:17 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-09 14:31:17 status half-configured man-db 2.5.7-2ubuntu1
2011-05-09 14:31:19 status installed man-db 2.5.7-2ubuntu1
2011-05-09 14:31:19 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-09 14:31:19 status half-configured hicolor-icon-theme 0.11-1
2011-05-09 14:31:20 status installed hicolor-icon-theme 0.11-1
2011-05-09 14:31:20 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-09 14:31:20 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:31:21 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-09 14:31:21 status triggers-pending python-support 1.0.4ubuntu1
2011-05-09 14:31:21 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-09 14:31:21 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:31:21 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-09 14:31:21 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2011-05-09 14:31:21 status half-configured ureadahead 0.100.0-4.1.3
2011-05-09 14:31:21 status installed ureadahead 0.100.0-4.1.3
2011-05-09 14:31:21 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-09 14:31:21 status half-configured python-support 1.0.4ubuntu1
2011-05-09 14:31:23 status installed python-support 1.0.4ubuntu1
2011-05-09 14:31:24 startup packages configure
2011-05-09 14:31:24 configure libperl5.10 5.10.1-8ubuntu2.1 5.10.1-8ubuntu2.1
2011-05-09 14:31:24 status unpacked libperl5.10 5.10.1-8ubuntu2.1
2011-05-09 14:31:24 status half-configured libperl5.10 5.10.1-8ubuntu2.1
2011-05-09 14:31:24 status installed libperl5.10 5.10.1-8ubuntu2.1
2011-05-09 14:31:24 status triggers-pending libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:31:24 configure xdg-utils 1.0.2-6.1ubuntu3.1 1.0.2-6.1ubuntu3.1
2011-05-09 14:31:24 status unpacked xdg-utils 1.0.2-6.1ubuntu3.1
2011-05-09 14:31:24 status half-configured xdg-utils 1.0.2-6.1ubuntu3.1
2011-05-09 14:31:24 status installed xdg-utils 1.0.2-6.1ubuntu3.1
2011-05-09 14:31:24 configure google-chrome-stable 11.0.696.65-r84435 11.0.696.65-r84435
2011-05-09 14:31:24 status unpacked google-chrome-stable 11.0.696.65-r84435
2011-05-09 14:31:24 status half-configured google-chrome-stable 11.0.696.65-r84435
2011-05-09 14:31:37 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/google-chrome 200
2011-05-09 14:31:37 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/google-chrome 200
2011-05-09 14:31:37 status installed google-chrome-stable 11.0.696.65-r84435
2011-05-09 14:31:37 status triggers-pending menu 2.1.43ubuntu1
2011-05-09 14:31:37 status triggers-awaited menu 2.1.43ubuntu1
2011-05-09 14:31:37 configure ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:37 status unpacked ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:37 status half-configured ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:37 status installed ttf-symbol-replacement-wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:37 configure wine1.3 1.3.19-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:37 status unpacked wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:38 status unpacked wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:38 status half-configured wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 status installed wine1.3 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 configure wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 status unpacked wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 status half-configured wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 status installed wine1.3-dev 1.3.19-0ubuntu1~lucid1~ppa1
2011-05-09 14:31:39 configure winetricks 0.0+20110429~ppa1 0.0+20110429~ppa1
2011-05-09 14:31:39 status unpacked winetricks 0.0+20110429~ppa1
2011-05-09 14:31:39 status half-configured winetricks 0.0+20110429~ppa1
2011-05-09 14:31:39 status installed winetricks 0.0+20110429~ppa1
2011-05-09 14:31:39 configure apt-utils 0.7.25.3ubuntu9.4 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status unpacked apt-utils 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status half-configured apt-utils 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status installed apt-utils 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 configure apt-transport-https 0.7.25.3ubuntu9.4 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status unpacked apt-transport-https 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status half-configured apt-transport-https 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 status installed apt-transport-https 0.7.25.3ubuntu9.4
2011-05-09 14:31:39 configure gdm 2.30.2.is.2.30.0-0ubuntu5.2 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:39 status half-configured gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:41 status installed gdm 2.30.2.is.2.30.0-0ubuntu5.2
2011-05-09 14:31:41 configure php5-common 5.3.2-1ubuntu4.9 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status half-configured php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status installed php5-common 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 configure libapache2-mod-php5 5.3.2-1ubuntu4.9 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status unpacked libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:41 status half-configured libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:44 status installed libapache2-mod-php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:45 configure php5 5.3.2-1ubuntu4.9 5.3.2-1ubuntu4.9
2011-05-09 14:31:45 status unpacked php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:45 status half-configured php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:45 status installed php5 5.3.2-1ubuntu4.9
2011-05-09 14:31:45 configure thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:45 status unpacked thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:45 status unpacked thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:45 status half-configured thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:45 status installed thunderbird 3.1.10+build1+nobinonly-0ubuntu0.10.04.1
2011-05-09 14:31:45 configure usb-creator-common 0.2.22.3 0.2.22.3
2011-05-09 14:31:45 status unpacked usb-creator-common 0.2.22.3
2011-05-09 14:31:45 status unpacked usb-creator-common 0.2.22.3
2011-05-09 14:31:45 status half-configured usb-creator-common 0.2.22.3
2011-05-09 14:31:45 status installed usb-creator-common 0.2.22.3
2011-05-09 14:31:46 status triggers-pending python-central 0.6.15ubuntu1
2011-05-09 14:31:46 status triggers-awaited usb-creator-common 0.2.22.3
2011-05-09 14:31:46 configure vino 2.28.2-0ubuntu2.1 2.28.2-0ubuntu2.1
2011-05-09 14:31:46 status unpacked vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:46 status unpacked vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:46 status half-configured vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:46 status installed vino 2.28.2-0ubuntu2.1
2011-05-09 14:31:46 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2011-05-09 14:31:46 status half-configured python-central 0.6.15ubuntu1
2011-05-09 14:31:46 status installed usb-creator-common 0.2.22.3
2011-05-09 14:31:47 status installed python-central 0.6.15ubuntu1
2011-05-09 14:31:49 configure usb-creator-gtk 0.2.22.3 0.2.22.3
2011-05-09 14:31:49 status unpacked usb-creator-gtk 0.2.22.3
2011-05-09 14:31:49 status half-configured usb-creator-gtk 0.2.22.3
2011-05-09 14:31:49 status installed usb-creator-gtk 0.2.22.3
2011-05-09 14:31:49 status triggers-pending python-central 0.6.15ubuntu1
2011-05-09 14:31:49 status triggers-awaited usb-creator-gtk 0.2.22.3
2011-05-09 14:31:49 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2011-05-09 14:31:49 status half-configured python-central 0.6.15ubuntu1
2011-05-09 14:31:49 status installed usb-creator-gtk 0.2.22.3
2011-05-09 14:31:49 status installed python-central 0.6.15ubuntu1
2011-05-09 14:31:49 configure usb-creator 0.2.22.3 0.2.22.3
2011-05-09 14:31:49 status unpacked usb-creator 0.2.22.3
2011-05-09 14:31:49 status half-configured usb-creator 0.2.22.3
2011-05-09 14:31:49 status installed usb-creator 0.2.22.3
2011-05-09 14:31:49 configure perl-modules 5.10.1-8ubuntu2.1 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status unpacked perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status unpacked perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status half-configured perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status installed perl-modules 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 configure perl 5.10.1-8ubuntu2.1 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status unpacked perl 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 status half-configured perl 5.10.1-8ubuntu2.1
2011-05-09 14:31:49 update-alternatives: run with --install /usr/bin/rename rename /usr/bin/prename 60 --slave /usr/share/man/man1/rename.1.gz rename.1.gz /usr/share/man/man1/prename.1.gz
2011-05-09 14:31:50 status installed perl 5.10.1-8ubuntu2.1
2011-05-09 14:31:50 trigproc libc-bin 2.11.1-0ubuntu7.8 2.11.1-0ubuntu7.8
2011-05-09 14:31:50 status half-configured libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:31:50 status installed libc-bin 2.11.1-0ubuntu7.8
2011-05-09 14:31:50 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-09 14:31:50 status half-configured menu 2.1.43ubuntu1
2011-05-09 14:31:50 status installed menu 2.1.43ubuntu1
2011-05-17 05:05:40 startup archives unpack
2011-05-17 05:05:48 upgrade google-chrome-stable 11.0.696.65-r84435 11.0.696.68-r84545
2011-05-17 05:05:48 status half-configured google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:48 status unpacked google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:48 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:50 status triggers-pending menu 2.1.43ubuntu1
2011-05-17 05:05:50 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:50 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-17 05:05:50 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:50 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2011-05-17 05:05:50 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:50 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2011-05-17 05:05:50 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:58 status half-installed google-chrome-stable 11.0.696.65-r84435
2011-05-17 05:05:58 status unpacked google-chrome-stable 11.0.696.68-r84545
2011-05-17 05:05:59 status unpacked google-chrome-stable 11.0.696.68-r84545
2011-05-17 05:05:59 upgrade adobe-flashplugin 10.2.159.1-0lucid1 10.3.181.14-0lucid1
2011-05-17 05:05:59 status half-configured adobe-flashplugin 10.2.159.1-0lucid1
2011-05-17 05:06:01 update-alternatives: run with --remove iceape-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:01 update-alternatives: link group iceape-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:01 update-alternatives: run with --remove iceweasel-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:01 update-alternatives: link group iceweasel-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:01 update-alternatives: run with --remove mozilla-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:01 update-alternatives: link group mozilla-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:01 update-alternatives: run with --remove firefox-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:01 update-alternatives: link group firefox-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:01 update-alternatives: run with --remove xulrunner-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:01 update-alternatives: link group xulrunner-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:02 update-alternatives: run with --remove midbrowser-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:02 update-alternatives: link group midbrowser-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:02 update-alternatives: run with --remove xulrunner-addons-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:02 update-alternatives: link group xulrunner-addons-flashplugin updated to point to /usr/lib/gnash/libgnashplugin.so
2011-05-17 05:06:02 status unpacked adobe-flashplugin 10.2.159.1-0lucid1
2011-05-17 05:06:02 status half-installed adobe-flashplugin 10.2.159.1-0lucid1
2011-05-17 05:06:02 status triggers-pending hicolor-icon-theme 0.11-1
2011-05-17 05:06:02 status half-installed adobe-flashplugin 10.2.159.1-0lucid1
2011-05-17 05:06:04 status half-installed adobe-flashplugin 10.2.159.1-0lucid1
2011-05-17 05:06:04 status unpacked adobe-flashplugin 10.3.181.14-0lucid1
2011-05-17 05:06:04 status unpacked adobe-flashplugin 10.3.181.14-0lucid1
2011-05-17 05:06:04 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-17 05:06:04 status half-configured menu 2.1.43ubuntu1
2011-05-17 05:06:05 status installed menu 2.1.43ubuntu1
2011-05-17 05:06:05 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-17 05:06:05 status half-configured man-db 2.5.7-2ubuntu1
2011-05-17 05:06:07 status installed man-db 2.5.7-2ubuntu1
2011-05-17 05:06:07 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2011-05-17 05:06:07 status half-configured python-gmenu 2.30.0-0ubuntu4
2011-05-17 05:06:11 status installed python-gmenu 2.30.0-0ubuntu4
2011-05-17 05:06:11 status triggers-pending python-support 1.0.4ubuntu1
2011-05-17 05:06:11 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2011-05-17 05:06:11 status half-configured desktop-file-utils 0.16-0ubuntu2
2011-05-17 05:06:11 status installed desktop-file-utils 0.16-0ubuntu2
2011-05-17 05:06:11 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-05-17 05:06:11 status half-configured hicolor-icon-theme 0.11-1
2011-05-17 05:06:19 status installed hicolor-icon-theme 0.11-1
2011-05-17 05:06:19 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2011-05-17 05:06:19 status half-configured python-support 1.0.4ubuntu1
2011-05-17 05:06:26 status installed python-support 1.0.4ubuntu1
2011-05-17 05:06:27 startup packages configure
2011-05-17 05:06:27 configure google-chrome-stable 11.0.696.68-r84545 11.0.696.68-r84545
2011-05-17 05:06:27 status unpacked google-chrome-stable 11.0.696.68-r84545
2011-05-17 05:06:27 status half-configured google-chrome-stable 11.0.696.68-r84545
2011-05-17 05:06:33 update-alternatives: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/google-chrome 200
2011-05-17 05:06:33 update-alternatives: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/google-chrome 200
2011-05-17 05:06:33 status installed google-chrome-stable 11.0.696.68-r84545
2011-05-17 05:06:34 status triggers-pending menu 2.1.43ubuntu1
2011-05-17 05:06:34 status triggers-awaited menu 2.1.43ubuntu1
2011-05-17 05:06:35 configure adobe-flashplugin 10.3.181.14-0lucid1 10.3.181.14-0lucid1
2011-05-17 05:06:35 status unpacked adobe-flashplugin 10.3.181.14-0lucid1
2011-05-17 05:06:36 status half-configured adobe-flashplugin 10.3.181.14-0lucid1
2011-05-17 05:06:36 update-alternatives: run with --install /usr/lib/iceape/plugins/flashplugin-alternative.so iceape-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:36 update-alternatives: link group iceape-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:36 update-alternatives: run with --install /usr/lib/iceweasel/plugins/flashplugin-alternative.so iceweasel-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:36 update-alternatives: link group iceweasel-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:36 update-alternatives: run with --install /usr/lib/mozilla/plugins/flashplugin-alternative.so mozilla-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:36 update-alternatives: link group mozilla-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:36 update-alternatives: run with --install /usr/lib/firefox/plugins/flashplugin-alternative.so firefox-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:36 update-alternatives: link group firefox-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:36 update-alternatives: run with --install /usr/lib/xulrunner/plugins/flashplugin-alternative.so xulrunner-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:36 update-alternatives: link group xulrunner-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:37 update-alternatives: run with --install /usr/lib/midbrowser/plugins/flashplugin-alternative.so midbrowser-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:37 update-alternatives: link group midbrowser-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:37 update-alternatives: run with --install /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so xulrunner-addons-flashplugin /usr/lib/adobe-flashplugin/libflashplayer.so 50
2011-05-17 05:06:37 update-alternatives: link group xulrunner-addons-flashplugin updated to point to /usr/lib/adobe-flashplugin/libflashplayer.so
2011-05-17 05:06:37 status installed adobe-flashplugin 10.3.181.14-0lucid1
2011-05-17 05:06:37 trigproc menu 2.1.43ubuntu1 2.1.43ubuntu1
2011-05-17 05:06:37 status half-configured menu 2.1.43ubuntu1
2011-05-17 05:06:37 status installed menu 2.1.43ubuntu1
2011-05-18 07:08:31 startup archives unpack
2011-05-18 07:08:40 upgrade apturl 0.4.1ubuntu4 0.4.1ubuntu4.1
2011-05-18 07:08:40 status half-configured apturl 0.4.1ubuntu4
2011-05-18 07:08:43 status unpacked apturl 0.4.1ubuntu4
2011-05-18 07:08:44 status half-installed apturl 0.4.1ubuntu4
2011-05-18 07:08:44 status triggers-pending man-db 2.5.7-2ubuntu1
2011-05-18 07:08:44 status half-installed apturl 0.4.1ubuntu4
2011-05-18 07:08:46 status half-installed apturl 0.4.1ubuntu4
2011-05-18 07:08:46 status unpacked apturl 0.4.1ubuntu4.1
2011-05-18 07:08:47 status unpacked apturl 0.4.1ubuntu4.1
2011-05-18 07:08:47 upgrade apturl-common 0.4.1ubuntu4 0.4.1ubuntu4.1
2011-05-18 07:08:47 status half-configured apturl-common 0.4.1ubuntu4
2011-05-18 07:08:47 status unpacked apturl-common 0.4.1ubuntu4
2011-05-18 07:08:47 status half-installed apturl-common 0.4.1ubuntu4
2011-05-18 07:08:48 status half-installed apturl-common 0.4.1ubuntu4
2011-05-18 07:08:49 status half-installed apturl-common 0.4.1ubuntu4
2011-05-18 07:08:50 status unpacked apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:50 status unpacked apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:50 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2011-05-18 07:08:50 status half-configured man-db 2.5.7-2ubuntu1
2011-05-18 07:08:52 status installed man-db 2.5.7-2ubuntu1
2011-05-18 07:08:54 startup packages configure
2011-05-18 07:08:54 configure apturl-common 0.4.1ubuntu4.1 0.4.1ubuntu4.1
2011-05-18 07:08:54 status unpacked apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:54 status unpacked apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:54 status half-configured apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:54 status installed apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:54 status triggers-pending python-central 0.6.15ubuntu1
2011-05-18 07:08:54 status triggers-awaited apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:54 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2011-05-18 07:08:54 status half-configured python-central 0.6.15ubuntu1
2011-05-18 07:08:54 status installed apturl-common 0.4.1ubuntu4.1
2011-05-18 07:08:55 status installed python-central 0.6.15ubuntu1
2011-05-18 07:08:55 configure apturl 0.4.1ubuntu4.1 0.4.1ubuntu4.1
2011-05-18 07:08:55 status unpacked apturl 0.4.1ubuntu4.1
2011-05-18 07:08:55 status half-configured apturl 0.4.1ubuntu4.1
2011-05-18 07:08:55 status installed apturl 0.4.1ubuntu4.1
2011-05-18 07:08:55 status triggers-pending python-central 0.6.15ubuntu1
2011-05-18 07:08:55 status triggers-awaited apturl 0.4.1ubuntu4.1
2011-05-18 07:08:55 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2011-05-18 07:08:55 status half-configured python-central 0.6.15ubuntu1
2011-05-18 07:08:55 status installed apturl 0.4.1ubuntu4.1
2011-05-18 07:08:56 status installed python-central 0.6.15ubuntu1
2011-05-19 07:39:46 startup packages configure
2011-05-21 08:12:29 startup packages configure
2011-05-21 08:12:42 startup packages configure
```

---

### Post by KEE on 2011-05-22
```
gedit /var/log/syslog
``` ```
May 22 00:55:46 spaceops rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="838" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 22 00:55:48 spaceops rsyslogd: last message repeated 2 times
May 22 00:55:48 spaceops kernel: [  359.073235] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28290 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=75.54.205.17 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=39721 LEN=75 ] 
May 22 00:56:04 spaceops kernel: [  375.324824] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28291 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=188.123.226.8 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=42643 LEN=75 ] 
May 22 00:56:11 spaceops kernel: [  382.655465] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28292 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=124.37.212.127 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=22960 LEN=75 ] 
May 22 00:56:41 spaceops kernel: [  412.697451] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28293 PROTO=ICMP
 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28293 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=82.196.174.87 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=44279 LEN=75 ] 
May 22 00:56:49 spaceops kernel: [  420.421468] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28294 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=190.213.195.112 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=30994 LEN=75 ] 
May 22 00:57:07 spaceops kernel: [  438.177562] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28295 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=124.115.12.153 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=2063 LEN=75 ] 
May 22 00:57:19 spaceops kernel: [  450.896111] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28296 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=68.40.181.175 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=22222 LEN=75 ] 
May 22 00:57:20 spaceops anacron[1185]: Job `cron.daily' terminated (mailing output)
May 22 00:57:20 spaceops anacron[1185]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
May 22 00:57:20 spaceops anacron[1185]: Normal exit (1 job run)
May 22 00:57:37 spaceops kernel: [  468.816166] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28297 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=205.250.150.127 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=40849 LEN=75 ] 
May 22 00:57:49 spaceops kernel: [  480.566530] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28298 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=89.238.170.10 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=6881 LEN=75 ] 
May 22 00:57:58 spaceops kernel: [  489.740655] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28299 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=99.125.170.68 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=30127 LEN=75 ] 
May 22 00:58:15 spaceops kernel: [  506.616328] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28300 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=213.66.56.36 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=16336 LEN=75 ] 
May 22 00:58:42 spaceops kernel: [  533.635041] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28301 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.23.233.34 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=8890 LEN=75 ] 
May 22 00:59:12 spaceops kernel: [  563.290542] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28302 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=84.244.8.102 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=18664 LEN=75 ] 
May 22 00:59:24 spaceops kernel: [  575.244083] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28303 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.85.196.164 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=33855 LEN=75 ] 
May 22 00:59:35 spaceops kernel: [  586.283699] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28304 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=70.112.69.186 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=28404 LEN=75 ] 
May 22 01:00:01 spaceops CRON[3115]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p
daemon.info)
May 22 01:00:01 spaceops debarchiver: Error: No mail command has been found.
May 22 01:00:01 spaceops debarchiver: EXIT: 2
May 22 01:00:02 spaceops kernel: [  613.953646] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28305 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=75.129.55.186 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=27474 LEN=75 ] 
May 22 01:00:11 spaceops kernel: [  622.816030] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28306 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=210.143.48.241 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=60467 LEN=75 ] 
May 22 01:00:40 spaceops kernel: [  651.673579] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28307 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=75.37.71.128 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=51533 LEN=75 ] 
May 22 01:00:53 spaceops kernel: [  664.409977] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28308 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=80.186.206.13 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=44160 LEN=75 ] 
May 22 01:01:10 spaceops kernel: [  681.132347] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28309 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=67.170.123.206 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=28747 LEN=75 ] 
May 22 01:01:18 spaceops kernel: [  689.552709] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1
DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28310 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=89.162.45.100 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=34551 LEN=75 ] 
May 22 01:01:38 spaceops kernel: [  709.820751] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28311 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=118.160.194.208 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=26128 LEN=75 ] 
May 22 01:01:51 spaceops kernel: [  722.673746] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28312 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=67.172.183.7 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=43641 LEN=75 ] 
May 22 01:02:03 spaceops kernel: [  734.147181] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28313 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=71.17.72.209 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=51413 LEN=75 ] 
May 22 01:02:13 spaceops kernel: [  744.317364] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28314 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=97.93.34.214 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=26055 LEN=75 ] 
May 22 01:02:20 spaceops kernel: [  751.426863] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28315 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.122.161.183 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=36240 LEN=75 ]
 May 22 01:02:40 spaceops kernel: [  771.253714] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28316 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=24.27.122.49 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=27260 LEN=75 ] 
May 22 01:02:47 spaceops kernel: [  778.533287] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28317 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=194.219.108.76 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=49160 LEN=75 ] 
May 22 01:02:50 spaceops AptDaemon: INFO: Initializing daemon
May 22 01:02:56 spaceops kernel: [  787.673548] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28318 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=87.69.114.206 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=46077 LEN=75 ] 
May 22 01:03:07 spaceops kernel: [  798.519006] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28319 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=89.215.189.25 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=56140 LEN=75 ] 
May 22 01:03:25 spaceops kernel: [  816.873329] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28320 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.198.255.19 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=47602 LEN=75 ] 
 May 22 01:03:35 spaceops kernel: [  826.153208] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28321 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.177.237.104 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=17753 LEN=75 ] 
May 22 01:03:49 spaceops kernel: [  840.525888] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28322 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.188.103.236 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=23576 LEN=75 ] 
May 22 01:04:00 spaceops kernel: [  851.758265] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28323 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=99.126.209.210 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=33501 LEN=75 ] 
May 22 01:04:21 spaceops kernel: [  872.358659] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28324 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=92.237.196.123 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=43480 LEN=75 ] 
May 22 01:04:32 spaceops kernel: [  883.758334] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28325 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=77.66.235.252 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=23572 LEN=75 ] 
May 22 01:04:47 spaceops kernel: [  898.921573] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28326 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=83.152.76.152 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=33144 LEN=75 ] 
May 22 01:05:01 spaceops CRON[3678]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:05:01 spaceops debarchiver: Error: No mail command has been found.
May 22 01:05:01 spaceops debarchiver: EXIT: 2
May 22 01:05:02 spaceops kernel: [  913.726093] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28327 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=95.158.244.242 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=43737 LEN=75 ] 
May 22 01:05:13 spaceops kernel: [  924.962894] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28328 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=87.121.152.157 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=16638 LEN=75 ] 
May 22 01:05:30 spaceops kernel: [  941.452964] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28329 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=84.212.219.213 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=51625 LEN=75 ] 
May 22 01:05:47 spaceops kernel: [  958.150253] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28330 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=60.48.51.248 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=20528 LEN=75 ] 
May 22 01:06:21 spaceops kernel: [  992.834200] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28331 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=24.113.89.85 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=57285 LEN=75 ] 
May 22 01:06:33 spaceops kernel: [ 1004.706095] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28332 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=98.178.166.116 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=60946 LEN=75 ] 
May 22 01:06:49 spaceops kernel: [ 1021.022738] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28333 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=84.215.157.172 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=59980 LEN=75 ] 
May 22 01:07:10 spaceops kernel: [ 1041.976911] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28334 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=77.225.131.128 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=13750 LEN=75 ] 
May 22 01:07:19 spaceops kernel: [ 1050.611385] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28335 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=82.243.181.182 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=39656 LEN=75 ] 
May 22 01:07:39 spaceops kernel: [ 1070.327583] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28336 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=205.206.20.43 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=53770 LEN=75 ] 
May 22 01:07:51 spaceops AptDaemon: INFO: Quiting due to inactivity
May 22 01:07:51 spaceops AptDaemon: INFO: Shutdown was requested
May 22 01:07:51 spaceops AptDaemon: INFO: Initializing daemon
May 22 01:07:58 spaceops kernel: [ 1089.890023] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28337 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=92.125.249.191 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=54169 LEN=75 ] 
May 22 01:08:18 spaceops kernel: [ 1109.674205] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28338 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=91.117.129.181 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=28176 LEN=75 ] 
May 22 01:08:28 spaceops kernel: [ 1120.042892] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28339 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=68.47.124.212 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=10470 LEN=75 ] 
May 22 01:08:49 spaceops kernel: [ 1140.865715] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28340 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=190.213.73.85 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=63331 LEN=75 ] 
May 22 01:09:01 spaceops CRON[4696]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 01:09:11 spaceops kernel: [ 1162.337212] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28341 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=122.151.243.38 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=36656 LEN=75 ] 
May 22 01:09:31 spaceops kernel: [ 1183.035517] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28342 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=67.165.96.78 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=18331 LEN=75 ] 
May 22 01:09:42 spaceops kernel: [ 1193.382007] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28343 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.20.76.129 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=11877 LEN=75 ] 
May 22 01:10:01 spaceops CRON[4724]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:10:01 spaceops debarchiver: Error: No mail command has been found.
May 22 01:10:01 spaceops debarchiver: EXIT: 2
May 22 01:10:02 spaceops kernel: [ 1213.903336] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28344 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=99.236.18.118 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=61588 LEN=75 ] 
May 22 01:10:22 spaceops kernel: [ 1234.012072] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28345 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=114.69.124.84 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=13526 LEN=75 ] 
May 22 01:10:31 spaceops kernel: [ 1242.900767] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28346 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=86.166.228.57 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=50899 LEN=75 ] 
May 22 01:10:45 spaceops kernel: [ 1257.039181] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28347 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=76.105.234.61 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=40453 LEN=75 ] 
May 22 01:10:59 spaceops kernel: [ 1270.971338] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28348 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=186.204.157.174 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=17434 LEN=75 ] 
May 22 01:11:15 spaceops kernel: [ 1286.357150] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28349 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=89.82.134.145 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=49408 LEN=75 ] 
May 22 01:11:24 spaceops kernel: [ 1295.269691] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28350 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=188.61.66.9 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=6881 LEN=75 ] 
May 22 01:11:56 spaceops kernel: [ 1327.723233] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28351 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=123.240.22.1 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=24461 LEN=75 ] 
May 22 01:12:11 spaceops kernel: [ 1342.838543] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28352 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=203.133.229.112 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=10946 LEN=75 ] 
May 22 01:12:22 spaceops kernel: [ 1353.434605] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28353 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=65.190.81.73 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=52452 LEN=75 ] 
May 22 01:12:40 spaceops kernel: [ 1371.629653] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28354 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=90.177.133.240 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=16881 LEN=75 ] 
May 22 01:12:52 spaceops AptDaemon: INFO: Quiting due to inactivity
May 22 01:12:52 spaceops AptDaemon: INFO: Shutdown was requested
May 22 01:12:57 spaceops kernel: [ 1388.773824] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28355 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=149.159.2.128 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=23563 LEN=75 ] 
May 22 01:13:09 spaceops kernel: [ 1400.297912] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28356 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=86.140.7.187 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=57739 LEN=75 ] 
May 22 01:13:18 spaceops kernel: [ 1409.658560] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28357 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=89.156.126.101 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=27886 LEN=75 ] 
May 22 01:13:38 spaceops kernel: [ 1429.921896] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28358 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=212.251.242.109 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=18303 LEN=75 ] 
May 22 01:13:55 spaceops kernel: [ 1446.625696] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28359 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=173.70.84.104 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=47900 LEN=75 ] 
May 22 01:14:15 spaceops kernel: [ 1466.237975] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28360 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=114.45.99.94 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=14170 LEN=75 ] 
May 22 01:14:24 spaceops kernel: [ 1475.561392] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28361 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=174.59.119.23 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=31983 LEN=75 ] 
May 22 01:14:51 spaceops kernel: [ 1502.941181] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28362 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=80.66.255.197 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=11821 LEN=75 ] 
May 22 01:15:02 spaceops CRON[4775]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:15:03 spaceops debarchiver: Error: No mail command has been found.
May 22 01:15:03 spaceops debarchiver: EXIT: 2
May 22 01:15:04 spaceops kernel: [ 1515.093771] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28363 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=119.238.243.129 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=17082 LEN=75 ] 
May 22 01:15:33 spaceops kernel: [ 1544.341757] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28364 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=118.160.193.94 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=18657 LEN=75 ] 
May 22 01:15:54 spaceops kernel: [ 1565.925183] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28365 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=66.240.20.11 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=61043 LEN=75 ] 
May 22 01:16:18 spaceops kernel: [ 1589.716479] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28366 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=77.78.173.157 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=26333 LEN=75 ] 
May 22 01:16:39 spaceops kernel: [ 1610.281817] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28367 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=67.175.50.131 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=11520 LEN=75 ] 
May 22 01:16:47 spaceops kernel: [ 1618.119101] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28368 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=83.113.94.172 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=42514 LEN=75 ] 
May 22 01:17:01 spaceops CRON[4779]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 01:17:01 spaceops kernel: [ 1632.806156] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28369 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=24.193.229.80 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=6881 LEN=75 ] 
May 22 01:17:21 spaceops kernel: [ 1652.943796] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28370 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=220.135.222.210 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=8297 LEN=75 ] 
May 22 01:17:38 spaceops kernel: [ 1669.537570] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:1c:f0:46:33:14:08:00 SRC=192.168.0.1 DST=192.168.0.106 LEN=123 TOS=0x00 PREC=0xC0 TTL=64 ID=28371 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.0.106 DST=83.228.218.169 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51413 DPT=58688 LEN=75 ] 
May 22 01:18:38 spaceops transmission-daemon: DHT Attempting bootstrap from dht.transmissionbt.com (tr-dht.c:234)
May 22 01:18:38 spaceops transmission-daemon: DHT dht.transmissionbt.com:6881: No address associated with hostname (tr-dht.c:118)
May 22 01:20:01 spaceops CRON[4784]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:20:01 spaceops debarchiver: Error: No mail command has been found.
May 22 01:20:01 spaceops debarchiver: EXIT: 2
May 22 01:25:02 spaceops CRON[4796]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:25:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:25:02 spaceops debarchiver: EXIT: 2
May 22 01:26:43 spaceops kernel: [ 2214.342468] lo: Disabled Privacy Extensions
May 22 01:28:11 spaceops kernel: [ 2302.896052] No probe response from AP 00:1c:f0:46:33:14 after 500ms, disconnecting.
May 22 01:28:11 spaceops wpa_supplicant[918]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May 22 01:28:11 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
May 22 01:28:11 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 22 01:28:13 spaceops wpa_supplicant[918]: Trying to associate with 00:1c:f0:46:33:14 (SSID='dlink' freq=2437 MHz)
May 22 01:28:13 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 22 01:28:13 spaceops wpa_supplicant[918]: Association request to the driver failed
May 22 01:28:13 spaceops kernel: [ 2304.265435] wlan0: direct probe to AP 00:1c:f0:46:33:14 (try 1)
May 22 01:28:13 spaceops kernel: [ 2304.464055] wlan0: direct probe to AP 00:1c:f0:46:33:14 (try 2)
May 22 01:28:13 spaceops kernel: [ 2304.468212] wlan0: direct probe responded
May 22 01:28:13 spaceops kernel: [ 2304.468215] wlan0: authenticate with AP 00:1c:f0:46:33:14 (try 1)
May 22 01:28:13 spaceops kernel: [ 2304.473224] wlan0: authenticated
May 22 01:28:13 spaceops kernel: [ 2304.473263] wlan0: associate with AP 00:1c:f0:46:33:14 (try 1)
May 22 01:28:13 spaceops kernel: [ 2304.672042] wlan0: associate with AP 00:1c:f0:46:33:14 (try 2)
May 22 01:28:13 spaceops kernel: [ 2304.872043] wlan0: associate with AP 00:1c:f0:46:33:14 (try 3)
May 22 01:28:14 spaceops kernel: [ 2305.072043] wlan0: association with AP 00:1c:f0:46:33:14 timed out
May 22 01:28:14 spaceops NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 0)
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2249
May 22 01:28:14 spaceops NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
May 22 01:28:14 spaceops avahi-daemon[860]: Withdrawing address record for 192.168.0.106 on wlan0.
May 22 01:28:14 spaceops avahi-daemon[860]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.106.
May 22 01:28:14 spaceops avahi-daemon[860]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) starting
connection 'Auto mickey31'
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto mickey31' has security, but secrets are required.
May 22 01:28:14 spaceops NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May 22 01:28:14 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 01:28:16 spaceops nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 22 01:28:18 spaceops wpa_supplicant[918]: Authentication with 00:00:00:00:00:00 timed out.
May 22 01:30:01 spaceops CRON[5243]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:30:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:30:02 spaceops debarchiver: EXIT: 2
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 01:31:18 spaceops NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 01:31:18 spaceops NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto mickey31' has security, and secrets exist.  No new secrets needed.
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'ssid' value 'mickey31'
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
May 22 01:31:18 spaceops NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
May 22 01:31:18 spaceops NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 22 01:31:18 spaceops NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 22 01:31:18 spaceops NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 01:31:18 spaceops NetworkManager: <info>  Config: set interface ap_scan to 1
May 22 01:31:18 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 22 01:31:19 spaceops wpa_supplicant[918]: Trying to associate with 00:13:a3:1a:ff:67 (SSID='mickey31' freq=2462 MHz)
May 22 01:31:19 spaceops kernel: [ 2490.688802] ath9k: Two wiphys trying to scan at the same time
May 22 01:31:19 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 22 01:31:19 spaceops kernel: [ 2490.889279] wlan0: direct probe to AP 00:13:a3:1a:ff:67 (try 1)
May 22 01:31:19 spaceops kernel: [ 2490.891812] wlan0: direct probe responded
May 22 01:31:19 spaceops kernel: [ 2490.891816] wlan0: authenticate with AP 00:13:a3:1a:ff:67 (try 1)
May 22 01:31:19 spaceops kernel: [ 2490.893917] wlan0: authenticated
May 22 01:31:19 spaceops kernel: [ 2490.893943] wlan0: associate with AP 00:13:a3:1a:ff:67 (try 1)
May 22 01:31:19 spaceops kernel: [ 2490.895977] wlan0: RX AssocResp from 00:13:a3:1a:ff:67 (capab=0x451 status=0 aid=2)
May 22 01:31:19 spaceops kernel: [ 2490.895981] wlan0: associated
May 22 01:31:19 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
May 22 01:31:19 spaceops wpa_supplicant[918]: Associated with 00:13:a3:1a:ff:67
May 22 01:31:19 spaceops wpa_supplicant[918]: CTRL-EVENT-CONNECTED - Connection to 00:13:a3:1a:ff:67 completed (reauth) [id=0 id_str=]
May 22 01:31:19 spaceops NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
May 22 01:31:19 spaceops NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mickey31'.
May 22 01:31:19 spaceops NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May 22 01:31:19 spaceops NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May 22 01:31:19 spaceops NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
May 22 01:31:19 spaceops NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
May 22 01:31:20 spaceops NetworkManager: <info>  dhclient started with pid 5261
May 22 01:31:20 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May 22 01:31:20 spaceops NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 22 01:31:20 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
May 22 01:31:20 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
May 22 01:31:20 spaceops dhclient: Internet Systems Consortium DHCP Client V3.1.3
May 22 01:31:20 spaceops dhclient: Copyright 2004-2009 Internet Systems Consortium.
May 22 01:31:20 spaceops dhclient: All rights reserved.
May 22 01:31:20 spaceops dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 22 01:31:20 spaceops dhclient: 
May 22 01:31:20 spaceops NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
May 22 01:31:20 spaceops dhclient: Listening on LPF/wlan0/00:25:d3:01:0c:4d
May 22 01:31:20 spaceops dhclient: Sending on   LPF/wlan0/00:25:d3:01:0c:4d
May 22 01:31:20 spaceops dhclient: Sending on   Socket/fallback
May 22 01:31:20 spaceops dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May 22 01:31:21 spaceops dhclient: DHCPOFFER of 192.168.2.10 from 192.168.2.1
May 22 01:31:21 spaceops dhclient: DHCPREQUEST of 192.168.2.10 on wlan0 to 255.255.255.255 port 67
May 22 01:31:21 spaceops dhclient: DHCPACK of 192.168.2.10 from 192.168.2.1
May 22 01:31:21 spaceops NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
May 22 01:31:21 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May 22 01:31:21 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
May 22 01:31:21 spaceops NetworkManager: <info>    address 192.168.2.10
May 22 01:31:21 spaceops NetworkManager: <info>    prefix 24 (255.255.255.0)
May 22 01:31:21 spaceops NetworkManager: <info>    gateway 192.168.2.1
May 22 01:31:21 spaceops NetworkManager: <info>    hostname 'spaceopsR0P1A5Y'
May 22 01:31:21 spaceops dhclient: bound to 192.168.2.10 -- renewal in 104866 seconds.
May 22 01:31:21 spaceops NetworkManager: <info>    nameserver '192.168.2.1'
May 22 01:31:21 spaceops NetworkManager: nm_ip4_config_add_nameserver: assertion `nameserver != s' failed
May 22 01:31:21 spaceops NetworkManager: <info>    nameserver '192.168.2.1'
May 22 01:31:21 spaceops NetworkManager: <info>    domain name 'no-domain-set.aliant'
May 22 01:31:21 spaceops NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 22 01:31:21 spaceops NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
May 22 01:31:21 spaceops NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May 22 01:31:21 spaceops avahi-daemon[860]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.10.
May 22 01:31:21 spaceops avahi-daemon[860]: New relevant interface wlan0.IPv4 for mDNS.
May 22 01:31:21 spaceops avahi-daemon[860]: Registering new address record for 192.168.2.10 on wlan0.IPv4.
May 22 01:31:22 spaceops NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
May 22 01:31:22 spaceops NetworkManager: <info>  Policy set 'Auto mickey31' (wlan0) as default for routing and DNS.
May 22 01:31:22 spaceops NetworkManager: <info>  Activation (wlan0) successful, device activated.
May 22 01:31:22 spaceops NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May 22 01:31:25 spaceops iplist[1982]: info: User defined signal 1 signal caught
May 22 01:31:43 spaceops ntpdate[5583]: step time server 91.189.94.4 offset 14.394367 sec
May 22 01:32:27 spaceops kernel: [ 2544.420393] lo: Disabled Privacy Extensions
May 22 01:35:01 spaceops CRON[5859]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:35:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:35:02 spaceops debarchiver: EXIT: 2
May 22 01:39:01 spaceops CRON[5931]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 01:40:01 spaceops CRON[5988]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:40:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:40:02 spaceops debarchiver: EXIT: 2
May 22 01:45:01 spaceops CRON[6035]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:45:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:45:02 spaceops debarchiver: EXIT: 2
May 22 01:50:02 spaceops CRON[6113]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:50:04 spaceops debarchiver: Error: No mail command has been found.
May 22 01:50:04 spaceops debarchiver: EXIT: 2
May 22 01:55:01 spaceops CRON[6119]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 01:55:02 spaceops debarchiver: Error: No mail command has been found.
May 22 01:55:02 spaceops debarchiver: EXIT: 2
May 22 02:00:02 spaceops CRON[6298]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:00:04 spaceops debarchiver: Error: No mail command has been found.
May 22 02:00:04 spaceops debarchiver: EXIT: 2
May 22 02:05:01 spaceops CRON[7020]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:05:02 spaceops debarchiver: Error: No mail command has been found.
May 22 02:05:02 spaceops debarchiver: EXIT: 2
May 22 02:09:01 spaceops CRON[8499]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 02:10:01 spaceops CRON[8506]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:10:01 spaceops debarchiver: Error: No mail command has been found.
May 22 02:10:01 spaceops debarchiver: EXIT: 2
May 22 02:15:01 spaceops CRON[8521]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:15:02 spaceops debarchiver: Error: No mail command has been found.
May 22 02:15:02 spaceops debarchiver: EXIT: 2
May 22 02:17:01 spaceops CRON[8526]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 02:20:02 spaceops CRON[9249]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:20:04 spaceops debarchiver: Error: No mail command has been found.
May 22 02:20:04 spaceops debarchiver: EXIT: 2
May 22 02:25:02 spaceops CRON[10997]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:25:04 spaceops debarchiver: Error: No mail command has been found.
May 22 02:25:04 spaceops debarchiver: EXIT: 2
May 22 02:30:02 spaceops CRON[11002]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:30:02 spaceops debarchiver: Error: No mail command has been found.
May 22 02:30:02 spaceops debarchiver: EXIT: 2
May 22 02:35:01 spaceops CRON[11007]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:35:03 spaceops debarchiver: Error: No mail command has been found.
May 22 02:35:03 spaceops debarchiver: EXIT: 2
May 22 02:39:02 spaceops CRON[11013]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 02:40:01 spaceops CRON[11020]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:40:03 spaceops debarchiver: Error: No mail command has been found.
May 22 02:40:03 spaceops debarchiver: EXIT: 2
May 22 02:45:02 spaceops CRON[11025]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:45:05 spaceops debarchiver: Error: No mail command has been found.
May 22 02:45:05 spaceops debarchiver: EXIT: 2
May 22 02:50:01 spaceops CRON[11237]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:50:02 spaceops debarchiver: Error: No mail command has been found.
May 22 02:50:02 spaceops debarchiver: EXIT: 2
May 22 02:50:59 spaceops kernel: [ 7255.724604] kjournald starting.  Commit interval 5 seconds
May 22 02:50:59 spaceops kernel: [ 7255.725168] EXT3 FS on sda1, internal journal
May 22 02:50:59 spaceops kernel: [ 7255.725173] EXT3-fs: recovery complete.
May 22 02:50:59 spaceops kernel: [ 7255.725700] EXT3-fs: mounted filesystem with ordered data mode.
May 22 02:50:59 spaceops init: ureadahead-other main process (11261) terminated with status 4
May 22 02:55:01 spaceops CRON[11276]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 02:55:04 spaceops debarchiver: Error: No mail command has been found.
May 22 02:55:04 spaceops debarchiver: EXIT: 2
May 22 03:00:01 spaceops CRON[11295]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:00:01 spaceops debarchiver: Error: No mail command has been found.
May 22 03:00:01 spaceops debarchiver: EXIT: 2
May 22 03:05:02 spaceops CRON[11300]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:05:02 spaceops debarchiver: Error: No mail command has been found.
May 22 03:05:02 spaceops debarchiver: EXIT: 2
May 22 03:09:01 spaceops CRON[11331]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 03:10:02 spaceops CRON[11340]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:10:03 spaceops debarchiver: Error: No mail command has been found.
May 22 03:10:03 spaceops debarchiver: EXIT: 2
May 22 03:15:01 spaceops CRON[11345]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:15:02 spaceops debarchiver: Error: No mail command has been found.
May 22 03:15:02 spaceops debarchiver: EXIT: 2
May 22 03:17:01 spaceops CRON[12423]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 03:20:02 spaceops CRON[12427]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:20:03 spaceops debarchiver: Error: No mail command has been found.
May 22 03:20:03 spaceops debarchiver: EXIT: 2
May 22 03:25:01 spaceops CRON[12498]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:25:02 spaceops debarchiver: Error: No mail command has been found.
May 22 03:25:02 spaceops debarchiver: EXIT: 2
May 22 03:30:01 spaceops CRON[12503]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:30:02 spaceops debarchiver: Error: No mail command has been found.
May 22 03:30:02 spaceops debarchiver: EXIT: 2
May 22 03:35:02 spaceops CRON[12508]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:35:03 spaceops debarchiver: Error: No mail command has been found.
May 22 03:35:03 spaceops debarchiver: EXIT: 2
May 22 03:39:01 spaceops CRON[12514]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 03:40:01 spaceops CRON[12523]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:40:01 spaceops debarchiver: Error: No mail command has been found.
May 22 03:40:01 spaceops debarchiver: EXIT: 2
May 22 03:45:01 spaceops CRON[12883]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:45:02 spaceops debarchiver: Error: No mail command has been found.
May 22 03:45:02 spaceops debarchiver: EXIT: 2
May 22 03:50:02 spaceops CRON[13445]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:50:06 spaceops debarchiver: Error: No mail command has been found.
May 22 03:50:06 spaceops debarchiver: EXIT: 2
May 22 03:55:01 spaceops CRON[13451]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 03:55:04 spaceops debarchiver: Error: No mail command has been found.
May 22 03:55:04 spaceops debarchiver: EXIT: 2
May 22 04:00:01 spaceops CRON[13456]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:00:04 spaceops debarchiver: Error: No mail command has been found.
May 22 04:00:04 spaceops debarchiver: EXIT: 2
May 22 04:05:02 spaceops CRON[13461]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:05:04 spaceops debarchiver: Error: No mail command has been found.
May 22 04:05:04 spaceops debarchiver: EXIT: 2
May 22 04:09:01 spaceops CRON[13467]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 04:10:01 spaceops CRON[13474]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:10:01 spaceops debarchiver: Error: No mail command has been found.
May 22 04:10:01 spaceops debarchiver: EXIT: 2
May 22 04:15:02 spaceops CRON[13478]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:15:03 spaceops debarchiver: Error: No mail command has been found.
May 22 04:15:03 spaceops debarchiver: EXIT: 2
May 22 04:17:01 spaceops CRON[13484]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 04:20:01 spaceops CRON[13488]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:20:02 spaceops debarchiver: Error: No mail command has been found.
May 22 04:20:02 spaceops debarchiver: EXIT: 2
May 22 04:25:02 spaceops CRON[13494]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:25:02 spaceops debarchiver: Error: No mail command has been found.
May 22 04:25:02 spaceops debarchiver: EXIT: 2
May 22 04:30:02 spaceops CRON[13499]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:30:03 spaceops debarchiver: Error: No mail command has been found.
May 22 04:30:03 spaceops debarchiver: EXIT: 2
May 22 04:35:01 spaceops CRON[13504]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:35:02 spaceops debarchiver: Error: No mail command has been found.
May 22 04:35:02 spaceops debarchiver: EXIT: 2
May 22 04:39:01 spaceops CRON[13510]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 04:40:01 spaceops CRON[13517]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:40:03 spaceops debarchiver: Error: No mail command has been found.
May 22 04:40:03 spaceops debarchiver: EXIT: 2
May 22 04:45:02 spaceops CRON[13522]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:45:02 spaceops debarchiver: Error: No mail command has been found.
May 22 04:45:02 spaceops debarchiver: EXIT: 2
May 22 04:50:02 spaceops CRON[13527]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:50:03 spaceops debarchiver: Error: No mail command has been found.
May 22 04:50:03 spaceops debarchiver: EXIT: 2
May 22 04:55:01 spaceops CRON[13533]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 04:55:02 spaceops debarchiver: Error: No mail command has been found.
May 22 04:55:02 spaceops debarchiver: EXIT: 2
May 22 05:00:01 spaceops CRON[13538]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:00:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:00:02 spaceops debarchiver: EXIT: 2
May 22 05:05:02 spaceops CRON[13543]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:05:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:05:02 spaceops debarchiver: EXIT: 2
May 22 05:09:02 spaceops CRON[13549]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 05:10:01 spaceops CRON[13556]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:10:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:10:02 spaceops debarchiver: EXIT: 2
May 22 05:15:01 spaceops CRON[13561]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:15:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:15:02 spaceops debarchiver: EXIT: 2
May 22 05:17:01 spaceops CRON[13566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 05:20:02 spaceops CRON[13570]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:20:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:20:02 spaceops debarchiver: EXIT: 2
May 22 05:25:02 spaceops CRON[13576]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:25:03 spaceops debarchiver: Error: No mail command has been found.
May 22 05:25:03 spaceops debarchiver: EXIT: 2
May 22 05:30:01 spaceops CRON[13581]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:30:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:30:02 spaceops debarchiver: EXIT: 2
May 22 05:35:02 spaceops CRON[13586]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:35:04 spaceops debarchiver: Error: No mail command has been found.
May 22 05:35:04 spaceops debarchiver: EXIT: 2
May 22 05:39:02 spaceops CRON[13592]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 05:40:01 spaceops CRON[13599]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:40:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:40:02 spaceops debarchiver: EXIT: 2
May 22 05:45:02 spaceops CRON[13604]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:45:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:45:02 spaceops debarchiver: EXIT: 2
May 22 05:50:02 spaceops CRON[13609]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:50:02 spaceops debarchiver: Error: No mail command has been found.
May 22 05:50:02 spaceops debarchiver: EXIT: 2
May 22 05:55:02 spaceops CRON[13615]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 05:55:03 spaceops debarchiver: Error: No mail command has been found.
May 22 05:55:03 spaceops debarchiver: EXIT: 2
May 22 06:00:01 spaceops CRON[13620]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:00:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:00:02 spaceops debarchiver: EXIT: 2
May 22 06:05:01 spaceops CRON[13625]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:05:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:05:02 spaceops debarchiver: EXIT: 2
May 22 06:09:02 spaceops CRON[13631]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 06:10:01 spaceops CRON[13638]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:10:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:10:02 spaceops debarchiver: EXIT: 2
May 22 06:15:02 spaceops CRON[13643]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:15:04 spaceops debarchiver: Error: No mail command has been found.
May 22 06:15:04 spaceops debarchiver: EXIT: 2
May 22 06:17:01 spaceops CRON[13648]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 06:20:01 spaceops CRON[13652]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:20:03 spaceops debarchiver: Error: No mail command has been found.
May 22 06:20:03 spaceops debarchiver: EXIT: 2
May 22 06:25:01 spaceops CRON[13659]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
May 22 06:25:01 spaceops CRON[13660]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:25:01 spaceops debarchiver: Error: No mail command has been found.
May 22 06:25:01 spaceops debarchiver: EXIT: 2
May 22 06:30:01 spaceops CRON[13665]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:30:01 spaceops debarchiver: Error: No mail command has been found.
May 22 06:30:01 spaceops debarchiver: EXIT: 2
May 22 06:35:02 spaceops CRON[13670]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:35:03 spaceops debarchiver: Error: No mail command has been found.
May 22 06:35:03 spaceops debarchiver: EXIT: 2
May 22 06:35:48 spaceops kernel: [20744.708544] CE: hpet increasing min_delta_ns to 15000 nsec
May 22 06:39:02 spaceops CRON[13676]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 06:40:01 spaceops CRON[13683]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:40:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:40:02 spaceops debarchiver: EXIT: 2
May 22 06:45:02 spaceops CRON[13688]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:45:04 spaceops debarchiver: Error: No mail command has been found.
May 22 06:45:04 spaceops debarchiver: EXIT: 2
May 22 06:47:02 spaceops CRON[13693]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
May 22 06:50:01 spaceops CRON[13696]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:50:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:50:02 spaceops debarchiver: EXIT: 2
May 22 06:55:01 spaceops CRON[13702]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 06:55:02 spaceops debarchiver: Error: No mail command has been found.
May 22 06:55:02 spaceops debarchiver: EXIT: 2
May 22 07:00:02 spaceops CRON[13707]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:00:02 spaceops debarchiver: Error: No mail command has been found.
May 22 07:00:02 spaceops debarchiver: EXIT: 2
May 22 07:05:02 spaceops CRON[13712]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:05:04 spaceops debarchiver: Error: No mail command has been found.
May 22 07:05:04 spaceops debarchiver: EXIT: 2
May 22 07:09:02 spaceops CRON[13725]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 07:10:01 spaceops CRON[13732]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:10:03 spaceops debarchiver: Error: No mail command has been found.
May 22 07:10:03 spaceops debarchiver: EXIT: 2
May 22 07:15:01 spaceops CRON[13737]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:15:04 spaceops debarchiver: Error: No mail command has been found.
May 22 07:15:04 spaceops debarchiver: EXIT: 2
May 22 07:17:01 spaceops CRON[13742]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 07:20:01 spaceops CRON[13746]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:20:02 spaceops debarchiver: Error: No mail command has been found.
May 22 07:20:02 spaceops debarchiver: EXIT: 2
May 22 07:25:01 spaceops CRON[13752]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:25:02 spaceops debarchiver: Error: No mail command has been found.
May 22 07:25:02 spaceops debarchiver: EXIT: 2
May 22 07:30:02 spaceops CRON[13758]: (root) CMD (start -q anacron || :)
May 22 07:30:02 spaceops CRON[13759]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:30:03 spaceops anacron[13764]: Anacron 2.3 started on 2011-05-22
May 22 07:30:03 spaceops anacron[13764]: Normal exit (0 jobs run)
May 22 07:30:05 spaceops debarchiver: Error: No mail command has been found.
May 22 07:30:05 spaceops debarchiver: EXIT: 2
May 22 07:35:01 spaceops CRON[13767]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:35:04 spaceops debarchiver: Error: No mail command has been found.
May 22 07:35:04 spaceops debarchiver: EXIT: 2
May 22 07:39:02 spaceops CRON[13773]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 07:40:01 spaceops CRON[13780]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:40:03 spaceops debarchiver: Error: No mail command has been found.
May 22 07:40:03 spaceops debarchiver: EXIT: 2
May 22 07:45:01 spaceops CRON[13785]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:45:03 spaceops debarchiver: Error: No mail command has been found.
May 22 07:45:03 spaceops debarchiver: EXIT: 2
May 22 07:50:01 spaceops CRON[13790]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:50:04 spaceops debarchiver: Error: No mail command has been found.
May 22 07:50:04 spaceops debarchiver: EXIT: 2
May 22 07:55:01 spaceops CRON[13796]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 07:55:03 spaceops debarchiver: Error: No mail command has been found.
May 22 07:55:03 spaceops debarchiver: EXIT: 2
May 22 08:00:01 spaceops CRON[13801]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:00:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:00:02 spaceops debarchiver: EXIT: 2
May 22 08:05:01 spaceops CRON[13806]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:05:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:05:02 spaceops debarchiver: EXIT: 2
May 22 08:09:02 spaceops CRON[13812]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 22 08:10:01 spaceops CRON[13819]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:10:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:10:02 spaceops debarchiver: EXIT: 2
May 22 08:15:02 spaceops CRON[13824]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:15:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:15:02 spaceops debarchiver: EXIT: 2
May 22 08:17:02 spaceops CRON[13829]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 08:20:01 spaceops CRON[13833]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:20:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:20:02 spaceops debarchiver: EXIT: 2
May 22 08:25:01 spaceops CRON[13839]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:25:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:25:02 spaceops debarchiver: EXIT: 2
May 22 08:30:02 spaceops CRON[13898]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:30:02 spaceops debarchiver: Error: No mail command has been found.
May 22 08:30:02 spaceops debarchiver: EXIT: 2
May 22 08:35:02 spaceops CRON[13902]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
May 22 08:35:03 spaceops debarchiver: Error: No mail command has been found.
May 22 08:35:03 spaceops debarchiver: EXIT: 2
May 22 08:35:44 spaceops kernel: [27941.375273] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:44 spaceops kernel: [27941.580064] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:48 spaceops kernel: [27944.682613] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:48 spaceops kernel: [27944.789058] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:48 spaceops kernel: [27945.079217] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:49 spaceops kernel: [27945.883005] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:53 spaceops kernel: [27950.415739] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:53 spaceops kernel: [27950.620875] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:54 spaceops kernel: [27951.235343] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:35:55 spaceops kernel: [27951.965954] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:06 spaceops kernel: [27962.708635] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:06 spaceops kernel: [27962.913672] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:06 spaceops kernel: [27963.323317] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:07 spaceops kernel: [27963.937711] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:17 spaceops kernel: [27974.563653] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:20 spaceops kernel: [27977.560136] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:21 spaceops kernel: [27978.484228] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:26 spaceops kernel: [27983.605931] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:27 spaceops kernel: [27984.425388] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:30 spaceops kernel: [27987.429978] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:31 spaceops kernel: [27988.318171] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:39 spaceops kernel: [27995.898037] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:36:39 spaceops kernel: [27996.512881] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:00 spaceops kernel: [28017.411643] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:00 spaceops kernel: [28017.411670] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:00 spaceops kernel: [28017.508551] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:01 spaceops kernel: [28018.640052] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:03 spaceops kernel: [28020.483927] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:04 spaceops kernel: [28020.688762] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:06 spaceops kernel: [28023.557501] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:07 spaceops kernel: [28024.582167] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:09 spaceops kernel: [28026.426554] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:09 spaceops kernel: [28026.426584] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:11 spaceops kernel: [28027.750671] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:11 spaceops kernel: [28028.557905] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:11 spaceops kernel: [28028.559065] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:11 spaceops kernel: [28028.581305] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:14 spaceops kernel: [28031.280399] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:14 spaceops kernel: [28031.343102] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:14 spaceops kernel: [28031.343130] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:15 spaceops kernel: [28031.775512] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:15 spaceops kernel: [28032.162760] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:16 spaceops kernel: [28032.981747] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:17 spaceops kernel: [28033.801322] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:18 spaceops kernel: [28035.645788] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:18 spaceops kernel: [28035.645818] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39758 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:19 spaceops kernel: [28036.464868] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39757 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:19 spaceops kernel: [28036.508959] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:20 spaceops kernel: [28037.497434] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:20 spaceops kernel: [28037.520482] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:21 spaceops kernel: [28037.898775] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:21 spaceops kernel: [28038.040449] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:21 spaceops kernel: [28038.078860] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:21 spaceops kernel: [28038.106219] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:21 spaceops kernel: [28038.150503] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:22 spaceops kernel: [28038.932470] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:26 spaceops kernel: [28043.483751] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:27 spaceops kernel: [28044.149961] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:29 spaceops kernel: [28045.891108] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:29 spaceops kernel: [28046.583325] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:30 spaceops kernel: [28047.299304] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:32 spaceops kernel: [28049.379448] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:32 spaceops kernel: [28049.379477] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:32 spaceops kernel: [28049.393809] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:32 spaceops kernel: [28049.494230] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:33 spaceops kernel: [28049.797586] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:33 spaceops kernel: [28049.989364] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:33 spaceops kernel: [28050.102036] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:34 spaceops kernel: [28050.907967] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:36 spaceops kernel: [28052.746029] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:36 spaceops kernel: [28053.299929] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:39 spaceops kernel: [28055.931905] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:39 spaceops kernel: [28056.340927] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:43 spaceops kernel: [28059.824050] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:43 spaceops kernel: [28060.507880] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:44 spaceops kernel: [28061.463192] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:47 spaceops kernel: [28064.436654] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:48 spaceops kernel: [28065.560817] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:51 spaceops kernel: [28068.022006] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:52 spaceops kernel: [28069.044614] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.120.161 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=39796 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:53 spaceops kernel: [28070.071407] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46339 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:56 spaceops kernel: [28073.407791] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46377 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:56 spaceops kernel: [28073.446586] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49029 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:56 spaceops kernel: [28073.469210] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49030 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:57 spaceops kernel: [28073.757017] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46378 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:57 spaceops kernel: [28073.962403] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48997 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:57 spaceops kernel: [28074.408449] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48999 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:58 spaceops kernel: [28074.781607] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46378 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:58 spaceops kernel: [28074.786876] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46377 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:58 spaceops kernel: [28075.396188] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=48998 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:59 spaceops kernel: [28076.358310] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46377 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:59 spaceops kernel: [28076.358340] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49029 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:37:59 spaceops kernel: [28076.358365] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49030 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:00 spaceops kernel: [28076.830665] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46378 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:00 spaceops kernel: [28076.830693] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49030 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:00 spaceops kernel: [28076.875073] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49029 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:03 spaceops kernel: [28080.519405] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46340 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:04 spaceops kernel: [28080.929253] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46377 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:04 spaceops kernel: [28080.929280] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46378 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:05 spaceops kernel: [28082.330441] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46377 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:05 spaceops kernel: [28082.345707] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49029 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:05 spaceops kernel: [28082.393010] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49030 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:06 spaceops kernel: [28082.777253] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=184.84.79.139 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=46378 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:06 spaceops kernel: [28082.780603] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49030 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:06 spaceops kernel: [28082.782770] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49044 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:06 spaceops kernel: [28082.874662] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49029 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:10 spaceops kernel: [28086.692394] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49044 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:12 spaceops kernel: [28089.343594] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49045 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:13 spaceops kernel: [28089.741301] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49023 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:14 spaceops kernel: [28091.598230] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49044 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:15 spaceops kernel: [28092.074180] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49025 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:16 spaceops kernel: [28092.825972] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:00 SRC=50.18.119.38 DST=192.168.2.10 LEN=44 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=TCP SPT=80 DPT=49044 WINDOW=5840 RES=0x00 ACK SYN URGP=0 
May 22 08:38:17 spaceops kernel: [28093.674088] Inbound IN=wlan0 OUT= MAC=00:25:d3:01:0c:4d:00:13:a3:1a:ff:61:08:
```

---

### Post by linuxinstalledfromhdd on 2011-05-22
I have never seen anything quite like that before.  I would recommend you try to do a data migration of important data (to have a backup at least) that you wish to keep and perhaps reinstall with a more recent version of Ubuntu, and wait and see if this problem reoccurs. It could be hardware related.  Hard to be sure at this point.

---

### Post by KEE on 2011-05-22
> **linuxinstalledfromhdd said:**
> I have never seen anything quite like that before.  I would recommend you try to do a data migration of important data (to have a backup at least) that you wish to keep and perhaps reinstall with a more recent version of Ubuntu, and wait and see if this problem reoccurs. It could be hardware related.  Hard to be sure at this point.if its hard ware then why is vista working fine? I am not really done with the last part ```
gedit /var/log/syslog
``` im only on 01:28:14. theres still alot more information after that point. is more information needed?

---

### Post by linuxinstalledfromhdd on 2011-05-22
Keep doing what you are doing.  I just hope you made good backups.

---

### Post by KEE on 2011-05-22
> **linuxinstalledfromhdd said:**
> Keep doing what you are doing.  I just hope you made good backups.

well it works right now, its just I cant update anything and source frigged up aswell. Also, i cant put more infor. i had it at 11:00:00 saved then it timeoout when i tried to put more it screwed its at 8:00 something now. is that because ubuntu not wanting to put toomuch information on here? heres a pic of how updates dont work [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-1-10.png[/IMG]

---

### Post by KEE on 2011-05-23
> **kostkon said:**
> Yes, it could be a hardware problem.

But, could you paste here the output of some of your logs? give the following commands, one line at a time:
```
gedit /etc/apt/sources.list
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
gedit /var/log/dpkg.log
gedit /var/log/syslog
```
also, do a
```
sudo apt-get update
```
and paste its output here, as always.

Also, could you give some more info. You posted some images without explaining your problem in detail.
i cant update at all and i cant run recovery

---

### Post by linuxinstalledfromhdd on 2011-05-23
I would do a complete backup of any important data at this time, and reinstall 10.10. It sounds pretty bad at this point.

---

### Post by plucky on 2011-05-23
> **KEE said:**
> ```
gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``````
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
n
```


To fix that error,remove the "n" from the file as it shouldn't be there and is causing the error message ```
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

Then run ```
sudo apt-get update
``` to see if you get the same error.

Good Luck

p.s Please post thumbnails instead of large images as it is difficult to read sideways.

---

### Post by KEE on 2011-05-23
> **plucky said:**
> To fix that error,remove the "n" from the file as it shouldn't be there and is causing the error message ```
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

Then run ```
sudo apt-get update
``` to see if you get the same error.

Good Luck

p.s Please post thumbnails instead of large images as it is difficult to read sideways.
i cant it has permission now heres a pic...update i did found the files and did update heres what I got ```
bash: /usr/share/GNUstep/Makefiles/filesystem.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
bash: /usr/share/GNUstep/Makefiles/print_unique_pathlist.sh: No such file or directory
spaceops@spaceops:~$ gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
spaceops@spaceops:~$ gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
spaceops@spaceops:~$ sudo chmod 777 /etc/apt/sources.list.d/ubuntu-wine-pp-lucid.list.save 
[sudo] password for spaceops: 
spaceops@spaceops:~$ sudo chown spaceops /etc/apt/sources.list.d/ubuntu-wine-pp-lucid.list.save 
spaceops@spaceops:~$ gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.listspaceops@spaceops:~$ sudo chown spaceops /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list 
spaceops@spaceops:~$ sudo chmod 700 /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list 
spaceops@spaceops:~$ sudo chmod 700 /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save 
spaceops@spaceops:~$ sudo chown spaceops /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save 
spaceops@spaceops:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA       
Get:2 http://dl.google.com stable Release [1,351B]                             
Get:3 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ssakar/ppa/ubuntu/ lucid/main Translation-en_CA   
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main Translation-en_CA
Get:5 http://ppa.launchpad.net lucid Release.gpg [316B]              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_CA
Hit http://ppa.launchpad.net lucid Release                           
Get:6 http://dl.google.com stable/main Packages [1,230B]                       
Get:7 http://ppa.launchpad.net lucid Release [14.0kB]                          
Hit http://ppa.launchpad.net lucid Release                                  
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                      
Get:8 http://ppa.launchpad.net lucid/main Packages [4,783B]                    
Get:9 http://archive.canonical.com lucid Release.gpg [198B]                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_CA       
Get:10 http://archive.ubuntu.com lucid Release.gpg [189B]                      
Get:11 http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA [10.3kB] 
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:12 http://archive.canonical.com lucid Release [8,215B]                     
Get:13 http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA [425B]
Get:14 http://archive.canonical.com lucid/partner Packages [13.2kB]            
Get:15 http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA [663B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA       
Get:16 http://archive.ubuntu.com lucid-updates Release.gpg [198B]              
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA
Get:17 http://archive.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Hit http://archive.ubuntu.com lucid Release                                    
Get:18 http://archive.ubuntu.com lucid-updates Release [44.7kB]                
Get:19 http://archive.ubuntu.com lucid-security Release [44.7kB]               
Hit http://archive.ubuntu.com lucid/main Packages                              
Hit http://archive.ubuntu.com lucid/restricted Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://archive.ubuntu.com lucid/universe Packages                          
Hit http://archive.ubuntu.com lucid/universe Sources                           
Hit http://archive.ubuntu.com lucid/multiverse Packages                        
Hit http://archive.ubuntu.com lucid/multiverse Sources                         
Get:20 http://archive.ubuntu.com lucid-updates/main Packages [495kB]           
Get:21 http://archive.ubuntu.com lucid-updates/restricted Packages [3,240B]    
Get:22 http://archive.ubuntu.com lucid-updates/main Sources [191kB]            
Get:23 http://archive.ubuntu.com lucid-updates/restricted Sources [1,443B]     
Get:24 http://archive.ubuntu.com lucid-updates/universe Packages [200kB]       
Get:25 http://archive.ubuntu.com lucid-updates/universe Sources [74.1kB]       
Get:26 http://archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]    
Get:27 http://archive.ubuntu.com lucid-updates/multiverse Sources [5,061B]     
Get:28 http://archive.ubuntu.com lucid-security/main Packages [185kB]          
Get:29 http://archive.ubuntu.com lucid-security/restricted Packages [14B]      
Get:30 http://archive.ubuntu.com lucid-security/main Sources [55.5kB]
Get:31 http://archive.ubuntu.com lucid-security/restricted Sources [14B]       
Get:32 http://archive.ubuntu.com lucid-security/universe Packages [68.6kB]     
Get:33 http://archive.ubuntu.com lucid-security/universe Sources [20.9kB]      
Get:34 http://archive.ubuntu.com lucid-security/multiverse Packages [4,557B]   
Get:35 http://archive.ubuntu.com lucid-security/multiverse Sources [1,758B]    
Fetched 1,462kB in 2min 58s (8,208B/s)                                         
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
spaceops@spaceops:~$ 

```[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-4-4.png[/IMG]

---

### Post by KEE on 2011-05-23
i think its fixed thanks. im updating now we'll let ya know if turns out ok...its 3 hours though

---

### Post by KEE on 2011-05-23
k not sure whats happening here...not running any other programs..```
spaceops@spaceops:~$ sudo aptitude safe-upgrade
[sudo] password for spaceops: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by linuxinstalledfromhdd on 2011-05-23
Keep trying, but as long as you have your stuff backed up, you would save yourself a considerable amount of effort and time just reinstalling from a live usb or disc.. It should take what, 20 minutes tops?

---

### Post by KEE on 2011-05-23
k fixed thanks ```
spaceops@spaceops:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```[IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-6-4.png[/IMG]

---

