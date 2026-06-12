---
title: "Wife clicked update today, reboot to nothing"
date: 2010-09-29
forum: General Help
---

### Post by skogs on 2010-09-29
I had previously told her that updates were really easy and not to worry about them.  I guess 1 hiccup every few years is ok.  The machine updated today, 29 Sep 2010, and then reboots to odd stuff...or just a black screen with a little cursor in the top left home position.

What got updated this morning, unfortunately just about everything that could cause a boot problem:  
```
2010-09-29 08:01:06 startup archives unpack
2010-09-29 08:01:14 upgrade coreutils 7.4-2ubuntu2 7.4-2ubuntu3
2010-09-29 08:01:14 status half-configured coreutils 7.4-2ubuntu2
2010-09-29 08:01:14 status unpacked coreutils 7.4-2ubuntu2
2010-09-29 08:01:14 status half-installed coreutils 7.4-2ubuntu2
2010-09-29 08:01:14 status triggers-pending install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:01:14 status half-installed coreutils 7.4-2ubuntu2
2010-09-29 08:01:15 status triggers-pending man-db 2.5.7-2
2010-09-29 08:01:15 status half-installed coreutils 7.4-2ubuntu2
2010-09-29 08:01:18 status half-installed coreutils 7.4-2ubuntu2
2010-09-29 08:01:18 status unpacked coreutils 7.4-2ubuntu3
2010-09-29 08:01:18 status unpacked coreutils 7.4-2ubuntu3
2010-09-29 08:01:18 trigproc install-info 4.13a.dfsg.1-5ubuntu1 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:01:18 status half-configured install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:01:19 status installed install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:01:19 trigproc man-db 2.5.7-2 2.5.7-2
2010-09-29 08:01:19 status half-configured man-db 2.5.7-2
2010-09-29 08:01:21 status installed man-db 2.5.7-2
2010-09-29 08:01:22 startup packages configure
2010-09-29 08:01:22 configure coreutils 7.4-2ubuntu3 7.4-2ubuntu3
2010-09-29 08:01:22 status unpacked coreutils 7.4-2ubuntu3
2010-09-29 08:01:22 status half-configured coreutils 7.4-2ubuntu3
2010-09-29 08:01:22 status installed coreutils 7.4-2ubuntu3
2010-09-29 08:01:22 startup archives unpack
2010-09-29 08:01:23 upgrade libssl-dev 0.9.8k-7ubuntu8.1 0.9.8k-7ubuntu8.2
2010-09-29 08:01:23 status half-configured libssl-dev 0.9.8k-7ubuntu8.1
2010-09-29 08:01:23 status unpacked libssl-dev 0.9.8k-7ubuntu8.1
2010-09-29 08:01:23 status half-installed libssl-dev 0.9.8k-7ubuntu8.1
2010-09-29 08:01:23 status triggers-pending man-db 2.5.7-2
2010-09-29 08:01:24 status half-installed libssl-dev 0.9.8k-7ubuntu8.1
2010-09-29 08:01:26 status half-installed libssl-dev 0.9.8k-7ubuntu8.1
2010-09-29 08:01:27 status unpacked libssl-dev 0.9.8k-7ubuntu8.2
2010-09-29 08:01:27 status unpacked libssl-dev 0.9.8k-7ubuntu8.2
2010-09-29 08:01:27 upgrade libssl0.9.8 0.9.8k-7ubuntu8.1 0.9.8k-7ubuntu8.2
2010-09-29 08:01:27 status half-configured libssl0.9.8 0.9.8k-7ubuntu8.1
2010-09-29 08:01:27 status unpacked libssl0.9.8 0.9.8k-7ubuntu8.1
2010-09-29 08:01:27 status half-installed libssl0.9.8 0.9.8k-7ubuntu8.1
2010-09-29 08:01:28 status half-installed libssl0.9.8 0.9.8k-7ubuntu8.1
2010-09-29 08:01:28 status unpacked libssl0.9.8 0.9.8k-7ubuntu8.2
2010-09-29 08:01:29 status unpacked libssl0.9.8 0.9.8k-7ubuntu8.2
2010-09-29 08:01:29 trigproc man-db 2.5.7-2 2.5.7-2
2010-09-29 08:01:29 status half-configured man-db 2.5.7-2
2010-09-29 08:01:31 status installed man-db 2.5.7-2
2010-09-29 08:01:32 startup packages configure
2010-09-29 08:01:32 configure libssl0.9.8 0.9.8k-7ubuntu8.2 0.9.8k-7ubuntu8.2
2010-09-29 08:01:32 status unpacked libssl0.9.8 0.9.8k-7ubuntu8.2
2010-09-29 08:01:32 status half-configured libssl0.9.8 0.9.8k-7ubuntu8.2
2010-09-29 08:01:33 status installed libssl0.9.8 0.9.8k-7ubuntu8.2
2010-09-29 08:01:33 status triggers-pending libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:01:33 trigproc libc-bin 2.11.1-0ubuntu7.3 2.11.1-0ubuntu7.3
2010-09-29 08:01:33 status half-configured libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:01:33 status installed libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:01:34 startup archives unpack
2010-09-29 08:01:34 upgrade openssl 0.9.8k-7ubuntu8.1 0.9.8k-7ubuntu8.2
2010-09-29 08:01:34 status half-configured openssl 0.9.8k-7ubuntu8.1
2010-09-29 08:01:34 status unpacked openssl 0.9.8k-7ubuntu8.1
2010-09-29 08:01:34 status half-installed openssl 0.9.8k-7ubuntu8.1
2010-09-29 08:01:34 status triggers-pending man-db 2.5.7-2
2010-09-29 08:01:34 status half-installed openssl 0.9.8k-7ubuntu8.1
2010-09-29 08:01:37 status half-installed openssl 0.9.8k-7ubuntu8.1
2010-09-29 08:01:37 status unpacked openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:01:37 status unpacked openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:01:37 upgrade python-desktopcouch 0.6.4-0ubuntu3 0.6.4-0ubuntu3.1
2010-09-29 08:01:37 status half-configured python-desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:37 status unpacked python-desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:37 status half-installed python-desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:38 status half-installed python-desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:38 status unpacked python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:01:38 status unpacked python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:01:39 upgrade python-desktopcouch-records 0.6.4-0ubuntu3 0.6.4-0ubuntu3.1
2010-09-29 08:01:39 status half-configured python-desktopcouch-records 0.6.4-0ubuntu3
2010-09-29 08:01:39 status unpacked python-desktopcouch-records 0.6.4-0ubuntu3
2010-09-29 08:01:39 status half-installed python-desktopcouch-records 0.6.4-0ubuntu3
2010-09-29 08:01:40 status half-installed python-desktopcouch-records 0.6.4-0ubuntu3
2010-09-29 08:01:40 status unpacked python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:01:40 status unpacked python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:01:40 upgrade desktopcouch 0.6.4-0ubuntu3 0.6.4-0ubuntu3.1
2010-09-29 08:01:40 status half-configured desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:40 status unpacked desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:40 status half-installed desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:40 status half-installed desktopcouch 0.6.4-0ubuntu3
2010-09-29 08:01:41 status unpacked desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:01:41 status unpacked desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:01:41 upgrade gdm 2.30.2.is.2.30.0-0ubuntu3 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:01:41 status half-configured gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:46 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:46 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:47 status triggers-pending hicolor-icon-theme 0.11-1
2010-09-29 08:01:47 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:47 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:01:47 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:47 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2010-09-29 08:01:47 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:47 status triggers-pending ureadahead 0.100.0-4.1.3
2010-09-29 08:01:47 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:47 status triggers-pending ureadahead 0.100.0-4.1.3
2010-09-29 08:01:49 status half-installed gdm 2.30.2.is.2.30.0-0ubuntu3
2010-09-29 08:01:49 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:01:49 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:01:49 upgrade grub-pc 1.98-1ubuntu7 1.98-1ubuntu8
2010-09-29 08:01:49 status half-configured grub-pc 1.98-1ubuntu7
2010-09-29 08:01:49 status unpacked grub-pc 1.98-1ubuntu7
2010-09-29 08:01:49 status half-installed grub-pc 1.98-1ubuntu7
2010-09-29 08:01:50 status half-installed grub-pc 1.98-1ubuntu7
2010-09-29 08:01:51 status half-installed grub-pc 1.98-1ubuntu7
2010-09-29 08:01:51 status unpacked grub-pc 1.98-1ubuntu8
2010-09-29 08:01:52 status unpacked grub-pc 1.98-1ubuntu8
2010-09-29 08:01:52 upgrade grub-common 1.98-1ubuntu7 1.98-1ubuntu8
2010-09-29 08:01:52 status half-configured grub-common 1.98-1ubuntu7
2010-09-29 08:01:52 status unpacked grub-common 1.98-1ubuntu7
2010-09-29 08:01:52 status half-installed grub-common 1.98-1ubuntu7
2010-09-29 08:01:52 status half-installed grub-common 1.98-1ubuntu7
2010-09-29 08:01:52 status triggers-pending install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:01:52 status half-installed grub-common 1.98-1ubuntu7
2010-09-29 08:01:52 status half-installed grub-common 1.98-1ubuntu7
2010-09-29 08:01:53 status half-installed grub-common 1.98-1ubuntu7
2010-09-29 08:01:53 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:01:53 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:01:54 upgrade libgksu2-0 2.0.13~pre1-1ubuntu4 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:01:54 status half-configured libgksu2-0 2.0.13~pre1-1ubuntu4
2010-09-29 08:01:59 status unpacked libgksu2-0 2.0.13~pre1-1ubuntu4
2010-09-29 08:01:59 status half-installed libgksu2-0 2.0.13~pre1-1ubuntu4
2010-09-29 08:01:59 status half-installed libgksu2-0 2.0.13~pre1-1ubuntu4
2010-09-29 08:01:59 status half-installed libgksu2-0 2.0.13~pre1-1ubuntu4
2010-09-29 08:02:00 status unpacked libgksu2-0 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:02:00 status unpacked libgksu2-0 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:02:00 upgrade python-imaging 1.1.7-1 1.1.7-1ubuntu0.1
2010-09-29 08:02:00 status half-configured python-imaging 1.1.7-1
2010-09-29 08:02:00 status unpacked python-imaging 1.1.7-1
2010-09-29 08:02:00 status half-installed python-imaging 1.1.7-1
2010-09-29 08:02:01 status half-installed python-imaging 1.1.7-1
2010-09-29 08:02:01 status unpacked python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:02:01 status unpacked python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:02:01 upgrade fglrx 2:8.771-0ubuntu0sarvatt~lucid 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:01 status half-configured fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:11 status unpacked fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:12 status half-installed fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:12 status half-installed fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:12 status half-installed fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:15 status half-installed fglrx 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:16 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:16 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:16 upgrade fglrx-modaliases 2:8.771-0ubuntu0sarvatt~lucid 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:16 status half-configured fglrx-modaliases 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:16 status unpacked fglrx-modaliases 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:16 status half-installed fglrx-modaliases 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:17 status half-installed fglrx-modaliases 2:8.771-0ubuntu0sarvatt~lucid
2010-09-29 08:02:17 status unpacked fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:17 status unpacked fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:02:17 upgrade liblircclient0 0.8.6-0ubuntu4.1 0.8.6-0ubuntu4.2
2010-09-29 08:02:17 status half-configured liblircclient0 0.8.6-0ubuntu4.1
2010-09-29 08:02:17 status unpacked liblircclient0 0.8.6-0ubuntu4.1
2010-09-29 08:02:17 status half-installed liblircclient0 0.8.6-0ubuntu4.1
2010-09-29 08:02:18 status half-installed liblircclient0 0.8.6-0ubuntu4.1
2010-09-29 08:02:18 status unpacked liblircclient0 0.8.6-0ubuntu4.2
2010-09-29 08:02:18 status unpacked liblircclient0 0.8.6-0ubuntu4.2
2010-09-29 08:02:18 upgrade mplayer 2:1.0~rc3+svn20090426-1ubuntu16 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:02:18 status half-configured mplayer 2:1.0~rc3+svn20090426-1ubuntu16
2010-09-29 08:02:18 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16
2010-09-29 08:02:18 status half-installed mplayer 2:1.0~rc3+svn20090426-1ubuntu16
2010-09-29 08:02:18 status half-installed mplayer 2:1.0~rc3+svn20090426-1ubuntu16
2010-09-29 08:02:19 status half-installed mplayer 2:1.0~rc3+svn20090426-1ubuntu16
2010-09-29 08:02:20 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:02:20 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:02:20 upgrade nspluginwrapper 1.2.2-0ubuntu6 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:02:20 status half-configured nspluginwrapper 1.2.2-0ubuntu6
2010-09-29 08:02:20 status unpacked nspluginwrapper 1.2.2-0ubuntu6
2010-09-29 08:02:20 status half-installed nspluginwrapper 1.2.2-0ubuntu6
2010-09-29 08:02:20 status half-installed nspluginwrapper 1.2.2-0ubuntu6
2010-09-29 08:02:21 status half-installed nspluginwrapper 1.2.2-0ubuntu6
2010-09-29 08:02:21 status unpacked nspluginwrapper 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:02:21 status unpacked nspluginwrapper 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:02:21 trigproc man-db 2.5.7-2 2.5.7-2
2010-09-29 08:02:21 status half-configured man-db 2.5.7-2
2010-09-29 08:02:24 status installed man-db 2.5.7-2
2010-09-29 08:02:24 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-09-29 08:02:24 status half-configured hicolor-icon-theme 0.11-1
2010-09-29 08:02:31 status installed hicolor-icon-theme 0.11-1
2010-09-29 08:02:31 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2010-09-29 08:02:31 status half-configured python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:02:33 status installed python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:02:33 status triggers-pending python-support 1.0.4ubuntu1
2010-09-29 08:02:33 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2010-09-29 08:02:33 status half-configured desktop-file-utils 0.16-0ubuntu2
2010-09-29 08:02:33 status installed desktop-file-utils 0.16-0ubuntu2
2010-09-29 08:02:33 trigproc ureadahead 0.100.0-4.1.3 0.100.0-4.1.3
2010-09-29 08:02:33 status half-configured ureadahead 0.100.0-4.1.3
2010-09-29 08:02:33 status installed ureadahead 0.100.0-4.1.3
2010-09-29 08:02:33 trigproc install-info 4.13a.dfsg.1-5ubuntu1 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:02:33 status half-configured install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:02:34 status installed install-info 4.13a.dfsg.1-5ubuntu1
2010-09-29 08:02:34 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2010-09-29 08:02:34 status half-configured python-support 1.0.4ubuntu1
2010-09-29 08:02:37 status installed python-support 1.0.4ubuntu1
2010-09-29 08:02:38 startup packages configure
2010-09-29 08:02:38 configure libssl-dev 0.9.8k-7ubuntu8.2 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status unpacked libssl-dev 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status half-configured libssl-dev 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status installed libssl-dev 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 configure openssl 0.9.8k-7ubuntu8.2 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status unpacked openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status unpacked openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status half-configured openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 status installed openssl 0.9.8k-7ubuntu8.2
2010-09-29 08:02:38 configure gdm 2.30.2.is.2.30.0-0ubuntu4 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:38 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:38 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status unpacked gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:39 status half-configured gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:40 status installed gdm 2.30.2.is.2.30.0-0ubuntu4
2010-09-29 08:02:40 configure grub-common 1.98-1ubuntu8 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:40 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:41 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:41 status unpacked grub-common 1.98-1ubuntu8
2010-09-29 08:02:41 status half-configured grub-common 1.98-1ubuntu8
2010-09-29 08:02:41 status installed grub-common 1.98-1ubuntu8
2010-09-29 08:02:41 configure grub-pc 1.98-1ubuntu8 1.98-1ubuntu8
2010-09-29 08:02:41 status unpacked grub-pc 1.98-1ubuntu8
2010-09-29 08:02:41 status unpacked grub-pc 1.98-1ubuntu8
2010-09-29 08:02:41 status half-configured grub-pc 1.98-1ubuntu8
2010-09-29 08:06:10 status installed grub-pc 1.98-1ubuntu8
2010-09-29 08:06:10 configure libgksu2-0 2.0.13~pre1-1ubuntu4.1 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:06:10 status unpacked libgksu2-0 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:06:10 status half-configured libgksu2-0 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:06:11 update-alternatives: run with --install /usr/share/gconf/defaults/10_libgksu libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo 30
2010-09-29 08:06:11 update-alternatives: run with --install /usr/share/gconf/defaults/10_libgksu libgksu-gconf-defaults /usr/share/libgksu/debian/gconf-defaults.libgksu-su 20
2010-09-29 08:06:12 status installed libgksu2-0 2.0.13~pre1-1ubuntu4.1
2010-09-29 08:06:12 status triggers-pending libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:06:12 configure python-imaging 1.1.7-1ubuntu0.1 1.1.7-1ubuntu0.1
2010-09-29 08:06:12 status unpacked python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:06:12 status half-configured python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:06:12 status installed python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:06:12 status triggers-pending python-central 0.6.15ubuntu1
2010-09-29 08:06:12 status triggers-awaited python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:06:12 configure fglrx 2:8.780-0ubuntu2~xup1~lucid 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:12 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 status unpacked fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 status half-configured fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:13 update-alternatives: run with --force --install /etc/ld.so.conf.d/GL.conf gl_conf /usr/lib/fglrx/ld.so.conf 1000 --slave /usr/bin/aticonfig aticonfig /usr/lib/fglrx/bin/aticonfig --slave /usr/bin/atiode atiode /usr/lib/fglrx/bin/atiode --slave /usr/bin/amdnotifyui amdnotifyui /usr/lib/fglrx/bin/amdnotifyui --slave /usr/bin/amdcccle amdcccle /usr/lib/fglrx/bin/amdcccle --slave /usr/bin/amdxdg-su amdxdg_su /usr/lib/fglrx/bin/amdxdg-su --slave /usr/share/applications/ubuntu-amdcccle.desktop amdcccle_desktop /usr/share/fglrx/amdcccle.desktop --slave /usr/share/applications/ubuntu-amdccclesu.desktop amdccclesu_desktop /usr/share/fglrx/amdccclesu.desktop --slave /usr/bin/fgl_glxgears fgl_glxgears /usr/lib/fglrx/bin/fgl_glxgears --slave /usr/bin/fglrxinfo fglrxinfo /usr/lib/fglrx/bin/fglrxinfo --slave /usr/bin/atiodcli atiodcli /usr/lib/fglrx/bin/atiodcli --slave /usr/bin/atieventsd atieventsd /usr/lib/fglrx/bin/atieventsd --slave /usr/lib/xorg/modules/drivers/fglrx_drv.so fglrx_drv /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so --slave /usr/lib/dri/fglrx_dri.so fglrx_dri /usr/lib/fglrx/dri/fglrx_dri.so --slave /usr/lib/libAMDXvBA.cap libAMDXvBA_cap /usr/lib/fglrx/libAMDXvBA.cap --slave /etc/modprobe.d/fglrx.conf fglrx_modconf /lib/fglrx/modprobe.conf --slave /etc/X11/Xsession.d/10fglrx 10fglrx /usr/lib/fglrx/10fglrx --slave /etc/ati ati_conf /usr/lib/fglrx/etc/ati --slave /usr/lib/xorg/extra-modules xorg_extra_modules /usr/lib/fglrx/xorg --slave /usr/lib/libaticalcl.so libaticalcl.so /usr/lib/fglrx/libaticalcl.so --slave /usr/lib32/libaticalcl.so libaticalcl.so_lib32 /usr/lib32/fglrx/libaticalcl.so --slave /usr/lib/libaticalrt.so libaticalrt.so /usr/lib/fglrx/libaticalrt.so --slave /usr/lib32/libaticalrt.so libaticalrt.so_lib32 /usr/lib32/fglrx/libaticalrt.so
2010-09-29 08:06:13 update-alternatives: auto-repair link group gl_conf
2010-09-29 08:06:32 status installed fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:06:33 status triggers-awaited fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 status triggers-pending initramfs-tools 0.92bubuntu78
2010-09-29 08:06:33 configure fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 status unpacked fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 status half-configured fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 status installed fglrx-modaliases 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:33 configure liblircclient0 0.8.6-0ubuntu4.2 0.8.6-0ubuntu4.2
2010-09-29 08:06:33 status unpacked liblircclient0 0.8.6-0ubuntu4.2
2010-09-29 08:06:33 status half-configured liblircclient0 0.8.6-0ubuntu4.2
2010-09-29 08:06:33 status installed liblircclient0 0.8.6-0ubuntu4.2
2010-09-29 08:06:33 configure mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status unpacked mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status half-configured mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 status installed mplayer 2:1.0~rc3+svn20090426-1ubuntu16.1
2010-09-29 08:06:33 configure nspluginwrapper 1.2.2-0ubuntu6.10.04.1 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:06:33 status unpacked nspluginwrapper 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:06:33 status half-configured nspluginwrapper 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:06:34 status installed nspluginwrapper 1.2.2-0ubuntu6.10.04.1
2010-09-29 08:06:34 configure desktopcouch 0.6.4-0ubuntu3.1 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status unpacked desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status unpacked desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status half-configured desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status installed desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 configure python-desktopcouch 0.6.4-0ubuntu3.1 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status unpacked python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status half-configured python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status installed python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 status triggers-awaited python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:34 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2010-09-29 08:06:34 status half-configured python-central 0.6.15ubuntu1
2010-09-29 08:06:34 status installed python-desktopcouch 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 status installed python-imaging 1.1.7-1ubuntu0.1
2010-09-29 08:06:35 status installed python-central 0.6.15ubuntu1
2010-09-29 08:06:35 configure python-desktopcouch-records 0.6.4-0ubuntu3.1 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 status unpacked python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 status half-configured python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 status installed python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 status triggers-pending python-central 0.6.15ubuntu1
2010-09-29 08:06:35 status triggers-awaited python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:06:35 trigproc libc-bin 2.11.1-0ubuntu7.3 2.11.1-0ubuntu7.3
2010-09-29 08:06:35 status half-configured libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:06:35 status installed libc-bin 2.11.1-0ubuntu7.3
2010-09-29 08:06:35 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2010-09-29 08:06:35 status half-configured python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:06:35 status installed fglrx 2:8.780-0ubuntu2~xup1~lucid
2010-09-29 08:06:36 status installed python-gmenu 2.30.0-0ubuntu4
2010-09-29 08:06:36 status triggers-pending python-support 1.0.4ubuntu1
2010-09-29 08:06:36 trigproc initramfs-tools 0.92bubuntu78 0.92bubuntu78
2010-09-29 08:06:36 status half-configured initramfs-tools 0.92bubuntu78
2010-09-29 08:06:48 status installed initramfs-tools 0.92bubuntu78
2010-09-29 08:06:48 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2010-09-29 08:06:48 status half-configured python-central 0.6.15ubuntu1
2010-09-29 08:06:49 status installed python-desktopcouch-records 0.6.4-0ubuntu3.1
2010-09-29 08:06:49 status installed python-central 0.6.15ubuntu1
2010-09-29 08:06:49 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2010-09-29 08:06:49 status half-configured python-support 1.0.4ubuntu1
2010-09-29 08:06:49 status installed python-support 1.0.4ubuntu1
```

Boot log, messages, dmesg are suprisingly useless and/or empty.

I can get the machine up in recovery  mode with reduced graphics, but if I don't do that I get odd messages about network not coming up right...with rules.d/hp-foobar-p1505.rules error in use of SYSFS instead of ATTR in udev.
I removed the offending rule, though I doubt it had any meaning as it refered to a USB connection that isn't used.

eth0 pre-start 685 terminated with state 1...

I just plain don't get it.  It looks like there are a dozen things goofed up, but none of them should be keeping me from a normal desktop login.

I am about to try re-installing gdm and kernel, will see what happens.

---

### Post by skogs on 2010-09-29
Reverting to the old kernel gets it up, minus video acceleration.  guess I should just be happy with that.

---

### Post by andrei2 on 2010-10-05
The amd video driver from xswat team ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)) seems to be the root cause:
after reverting to default video config and completely uninstalling the latest 2:8.780-0ubuntu2~xup1~lucid driver, I'm back to the default ati driver 2:8.723.1-0ubuntu5 and everything is fine so far.

Any idea what is wrong with the latest driver?

CU
Andrei

---

### Post by skogs on 2010-10-05
End result is that I began beta testing the 10.10 release candidate.  I did a fresh install with alt-install disc.  
I have no idea what boned it, though video does seem the most likely.  I would have been more upset with the outcome had it not been just about time to switch anyway.

On another note: May the fleas of a thousand camels infest the armpits of the 'team' that moved all the buttons over to the left side of the windows.  Seriously...millions of people just have to move them back to the right so they don't lose all their hair.

---

### Post by Quackers on 2010-10-05
Lol. I think I read somewhere that it's for upcoming changes of some kind.
Glad to see you're up and running again :-)

---

