---
title: "ownerships in /usr/bin"
date: 2010-09-14
forum: General Help
---

### Post by anntzer on 2010-09-14
Hi,
I accidentally (well, after trying to do some stuff...) changed the ownership of all my /usr/bin/* to root. Is there anything that shouldn't be owned by root in /usr/bin, actually?
Thanks,
Antony

---

### Post by dcstar on 2010-09-14
> **anntzer said:**
> Hi,
I accidentally (well, after trying to do some stuff...) changed the ownership of all my /usr/bin/* to root. Is there anything that shouldn't be owned by root in /usr/bin, actually?


Not on my system.

---

### Post by robsoles on 2010-09-14
Here is a dump of ls -al in /usr/bin from a machine I take care of. There are a couple of files in this list that are not solely owned by root:

```
total 173992
drwxr-xr-x  2 root   root      40960 2010-09-09 07:39 .
drwxr-xr-x 11 root   root       4096 2010-06-21 14:59 ..
-rwxr-xr-x  1 root   root      47584 2010-03-05 14:41 [
lrwxrwxrwx  1 root   root          8 2010-06-18 15:37 2to3 -> 2to3-2.6
-rwxr-xr-x  1 root   root        106 2010-04-17 00:41 2to3-2.6
-rwxr-xr-x  1 root   root         39 2009-07-09 10:30 7z
-rwxr-xr-x  1 root   root         40 2009-07-09 10:30 7za
-rwxr-xr-x  1 root   root     106272 2010-04-23 18:38 a2p
lrwxrwxrwx  1 root   root          7 2010-09-09 07:38 abrowser -> firefox
-rwxr-xr-x  1 root   root      18984 2010-03-29 10:04 aconnect
-rwxr-xr-x  1 root   root       6328 2010-04-23 23:24 acpi_fakekey
-rwxr-xr-x  1 root   root      10864 2010-04-29 16:24 acpi_listen
-rwxr-xr-x  1 root   root       1221 2010-04-15 15:02 add-apt-repository
-rwxr-xr-x  1 root   root       6288 2010-03-23 04:57 addpart
-rwxr-xr-x  1 root   root      27624 2010-06-18 21:43 addr2line
-rwxr-xr-x  1 root   root       1211 2010-03-29 21:14 alacarte
-rwxr-xr-x  1 root   root      65344 2010-03-29 10:04 alsamixer
-rwxr-xr-x  1 root   root      18984 2010-03-29 10:04 amidi
-rwxr-xr-x  1 root   root      52672 2010-03-29 10:04 amixer
-rwxr-xr-x  1 root   root       2668 2009-11-14 05:51 amuFormat.sh
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 animate
-rwxr-xr-x  1 root   root      60624 2010-03-29 10:04 aplay
-rwxr-xr-x  1 root   root      23136 2010-03-29 10:04 aplaymidi
-rwxr-xr-x  1 root   root       2184 2010-04-19 18:56 apport-bug
-rwxr-xr-x  1 root   root      14640 2010-04-19 18:56 apport-cli
lrwxrwxrwx  1 root   root         10 2010-06-18 15:37 apport-collect -> apport-bug
-rwxr-xr-x  1 root   root       1382 2010-04-19 18:56 apport-unpack
-rwxr-xr-x  1 root   root      10440 2010-03-23 07:28 appres
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 apropos -> whatis
lrwxrwxrwx  1 root   root         18 2010-06-18 15:37 apt-add-repository -> add-apt-repository
-rwxr-xr-x  1 root   root      64504 2010-07-16 18:15 apt-cache
-rwxr-xr-x  1 root   root      23136 2010-07-16 18:15 apt-cdrom
-rwxr-xr-x  1 root   root      14800 2010-07-16 18:15 apt-config
-rwxr-xr-x  1 root   root       1038 2010-04-17 16:42 aptdcon
-rwxr-xr-x  1 root   root      27352 2010-07-16 18:15 apt-extracttemplates
-rwxr-xr-x  1 root   root     180024 2010-07-16 18:15 apt-ftparchive
-rwxr-xr-x  1 root   root     122640 2010-07-16 18:15 apt-get
-rwxr-xr-x  1 root   root    2270504 2010-04-10 00:41 aptitude
-rwxr-xr-x  1 root   root       1939 2010-04-10 00:41 aptitude-create-state-bundle
-rwxr-xr-x  1 root   root       3007 2010-04-10 00:41 aptitude-run-state-bundle
-rwxr-xr-x  1 root   root       6521 2010-07-16 18:14 apt-key
-rwxr-xr-x  1 root   root       3253 2010-07-16 18:14 apt-mark
-rwxr-xr-x  1 root   root      32627 2009-06-23 00:37 apt-show-versions
-rwxr-xr-x  1 root   root      27176 2010-07-16 18:15 apt-sortpkgs
-rwxr-xr-x  1 root   root        273 2010-03-15 20:37 apturl
-rwxr-xr-x  1 root   root       1547 2010-03-20 04:51 apturl-gtk
-rwxr-xr-x  1 root   root      56168 2010-06-18 21:43 ar
-rwxr-xr-x  1 root   root      39360 2010-03-05 14:41 arch
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 arecord -> aplay
-rwxr-xr-x  1 root   root      23200 2010-03-29 10:04 arecordmidi
-rwxr-xr-x  1 root   root     335523 2009-12-18 18:18 arj
-rwxr-xr-x  1 root   root      11728 2009-12-18 18:18 arjdisp
-rwxr-xr-x  1 root   root      11456 2009-12-18 18:18 arj-register
-rwxr-xr-x  1 root   root      10432 2010-03-25 19:12 arm2hpdl
-rwsr-xr-x  1 root   root      14720 2010-03-12 22:41 arping
-rwxr-xr-x  1 root   root     319744 2010-06-18 21:43 as
-rwxr-xr-x  1 root   root      18848 2010-03-29 10:04 aseqdump
-rwxr-xr-x  1 root   root      18952 2010-03-29 10:04 aseqnet
-rwxr-xr-x  1 root   root     163416 2010-03-25 03:10 aspell
-rwxr-xr-x  1 root   root       2044 2010-03-25 03:10 aspell-import
-rwsr-sr-x  1 daemon daemon    52112 2010-03-05 13:42 at
-rwxr-xr-x  1 root   root      10456 2010-03-13 06:40 atobm
lrwxrwxrwx  1 root   root          2 2010-06-18 15:37 atq -> at
lrwxrwxrwx  1 root   root          2 2010-06-18 15:37 atrm -> at
-rwxr-xr-x  1 root   root      27208 2009-12-05 08:24 avahi-browse
lrwxrwxrwx  1 root   root         12 2010-06-18 15:37 avahi-browse-domains -> avahi-browse
-rwxr-xr-x  1 root   root      18896 2009-12-05 08:24 avahi-publish
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 avahi-publish-address -> avahi-publish
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 avahi-publish-service -> avahi-publish
-rwxr-xr-x  1 root   root      14720 2009-12-05 08:24 avahi-resolve
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 avahi-resolve-address -> avahi-resolve
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 avahi-resolve-host-name -> avahi-resolve
-rwxr-xr-x  1 root   root      14664 2009-12-05 08:24 avahi-set-host-name
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 awk -> /etc/alternatives/awk
-rwxr-xr-x  1 root   root     137008 2010-03-31 21:57 baobab
-rwxr-xr-x  1 root   root      43488 2010-03-05 14:41 base64
-rwxr-xr-x  1 root   root      35240 2010-03-05 14:41 basename
-rwxr-xr-x  1 root   root       6877 2010-04-19 12:15 bashbug
-rwxr-xr-x  1 root   root        152 2010-03-05 13:42 batch
-rwxr-xr-x  1 root   root      85112 2009-12-22 09:14 bc
-rwxr-xr-x  1 root   root      10424 2010-01-12 02:31 bdftopcf
-rwxr-xr-x  1 root   root        334 2010-07-13 03:58 bdftops
-rwxr-xr-x  1 root   root      10440 2010-01-12 02:31 bdftruncate
lrwxrwxrwx  1 root   root         28 2010-06-18 15:37 bf_compact -> /etc/alternatives/bf_compact
-rwxr-xr-x  1 root   root       2158 2010-08-28 01:11 bf_compact-bdb
lrwxrwxrwx  1 root   root         25 2010-06-18 15:37 bf_copy -> /etc/alternatives/bf_copy
-rwxr-xr-x  1 root   root       1266 2010-08-28 01:11 bf_copy-bdb
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 bf_tar -> /etc/alternatives/bf_tar
-rwxr-xr-x  1 root   root       1719 2010-08-28 01:11 bf_tar-bdb
-rwxr-xr-x  1 root   root      88768 2010-03-13 06:40 bitmap
-rwxr-xr-x  1 root   root      15032 2010-04-09 21:25 bluetooth-agent
-rwxr-xr-x  1 root   root     102944 2010-04-09 23:12 bluetooth-applet
-rwxr-xr-x  1 root   root      90816 2010-04-09 23:12 bluetooth-properties
-rwxr-xr-x  1 root   root      69712 2010-04-09 23:12 bluetooth-sendto
-rwxr-xr-x  1 root   root      86016 2010-04-09 23:12 bluetooth-wizard
-rwxr-xr-x  1 root   root      10456 2010-03-13 06:40 bmtoa
lrwxrwxrwx  1 root   root         28 2010-06-18 15:37 bogofilter -> /etc/alternatives/bogofilter
-rwxr-xr-x  1 root   root     212528 2010-08-28 01:11 bogofilter-bdb
lrwxrwxrwx  1 root   root         27 2010-06-18 15:37 bogolexer -> /etc/alternatives/bogolexer
-rwxr-xr-x  1 root   root     119704 2010-08-28 01:11 bogolexer-bdb
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 bogotune -> /etc/alternatives/bogotune
-rwxr-xr-x  1 root   root     202720 2010-08-28 01:11 bogotune-bdb
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 bogoupgrade -> /etc/alternatives/bogoupgrade
-rwxr-xr-x  1 root   root       5825 2010-08-28 01:11 bogoupgrade-bdb
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 bogoutil -> /etc/alternatives/bogoutil
-rwxr-xr-x  1 root   root      84000 2010-08-28 01:11 bogoutil-bdb
-rwxr-xr-x  1 root   root     476688 2010-06-25 23:01 brasero
-rwxr-xr-x  1 root   root      97416 2009-11-10 19:05 bsd-mailx
-rwxr-sr-x  1 root   tty       14704 2009-11-11 05:35 bsd-write
-rwxr-xr-x  1 root   root      26952 2009-12-06 09:03 btcflash
-rwxr-xr-x  1 root   root       2207 2010-04-01 07:27 byobu
-rwxr-xr-x  1 root   root      17103 2010-03-17 15:17 byobu-config
-rwxr-xr-x  1 root   root       3612 2010-03-11 11:26 byobu-export
-rwxr-xr-x  1 root   root       4974 2010-03-30 16:51 byobu-janitor
-rwxr-xr-x  1 root   root        850 2010-06-16 20:07 byobu-launch
-rwxr-xr-x  1 root   root        842 2010-03-03 18:14 byobu-launcher
-rwxr-xr-x  1 root   root       1633 2010-06-16 20:07 byobu-launcher-install
-rwxr-xr-x  1 root   root       1184 2010-06-16 20:07 byobu-launcher-uninstall
-rwxr-xr-x  1 root   root       1619 2010-03-11 11:37 byobu-reconnect-sockets
-rwxr-xr-x  1 root   root       4728 2010-03-10 10:04 byobu-select-profile
-rwxr-xr-x  1 root   root       1821 2010-04-01 07:11 byobu-select-session
-rwxr-xr-x  1 root   root       2620 2010-03-11 11:30 byobu-status
-rwxr-xr-x  1 root   root       1054 2010-03-03 18:14 byobu-status-detail
-rwxr-xr-x  1 root   root      36601 2010-04-23 18:37 c2ph
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 c89 -> /etc/alternatives/c89
-rwxr-xr-x  1 root   root        428 2009-06-13 02:05 c89-gcc
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 c99 -> /etc/alternatives/c99
-rwxr-xr-x  1 root   root        451 2009-06-13 02:05 c99-gcc
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 cal -> ncal
-rwxr-xr-x  1 root   root      27760 2009-11-11 05:35 calendar
-rwxr-xr-x  1 root   root      23848 2010-02-16 20:42 calibrate_ppa
-rwxr-xr-x  1 root   root      14664 2010-01-16 15:55 canberra-gtk-play
-rwxr-xr-x  1 root   root      14256 2010-06-19 01:19 cancel
lrwxrwxrwx  1 root   root          3 2010-06-18 15:37 captoinfo -> tic
-rwxr-xr-x  1 root   root       3396 2010-06-14 23:52 catchsegv
-rwxr-xr-x  1 root   root     167544 2010-03-02 21:31 catman
-rwxr-xr-x  1 root   root        853 2010-01-16 11:05 cautious-launcher
lrwxrwxrwx  1 root   root         20 2010-06-18 15:37 cc -> /etc/alternatives/cc
-rwxr-xr-x  1 root   root      57176 2009-12-06 09:00 cdparanoia
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 cdrecord -> wodim
-rwxr-xr-x  1 root   root      27208 2010-06-18 21:43 c++filt
-rwxr-sr-x  1 root   shadow    58984 2010-01-27 04:09 chage
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 charmap -> gucharmap
-rwxr-xr-x  1 root   root      10520 2010-04-19 14:31 chattr
-rwxr-xr-x  1 root   root      64208 2010-03-05 14:41 chcon
-rwxr-xr-x  1 root   root       3885 2010-03-20 06:46 check-bios-nx
-rwxr-xr-x  1 root   root        565 2010-04-03 04:06 checkbox-gtk
-rwxr-xr-x  1 root   root       2149 2010-06-18 20:00 check-language-support
-rwxr-xr-x  1 root   root       6280 2009-11-10 22:00 checksctp
-rwsr-xr-x  1 root   root      41864 2010-01-27 04:09 chfn
-rwxr-xr-x  1 root   root       3676 2010-03-23 04:56 chkdupexe
-rwxr-xr-x  1 root   root      10480 2010-03-23 04:57 chrt
-rwsr-xr-x  1 root   root      37128 2010-01-27 04:09 chsh
-rwxr-xr-x  1 root   root      19152 2010-04-09 21:25 ciptool
-rwxr-xr-x  1 root   root      31104 2010-03-13 05:09 cjpeg
-rwxr-xr-x  1 root   root     115811 2010-04-25 07:17 ckbcomp
-rwxr-xr-x  1 root   root      23544 2010-02-19 17:08 ck-history
-rwxr-xr-x  1 root   root      10448 2010-02-19 17:08 ck-launch-session
-rwxr-xr-x  1 root   root      10672 2010-02-19 17:08 ck-list-sessions
-rwxr-xr-x  1 root   root      39344 2010-03-05 14:41 cksum
-rwxr-xr-x  1 root   root       6264 2010-03-07 15:25 clear
-rwxr-xr-x  1 root   root      10456 2010-04-19 12:16 clear_console
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 cli -> /etc/alternatives/cli
lrwxrwxrwx  1 root   root         44 2010-06-18 15:37 cli-gacutil -> /etc/alternatives/global-assembly-cache-tool
-rwxr-xr-x  1 root   root      22968 2009-11-05 17:33 cmp
-rwxr-xr-x  1 root   root      10448 2010-03-13 01:29 codepage
-rwxr-xr-x  1 root   root      10464 2009-11-11 05:35 col
-rwxr-xr-x  1 root   root      10432 2009-11-11 05:35 colcrt
-rwxr-xr-x  1 root   root      10424 2009-11-11 05:35 colrm
-rwxr-xr-x  1 root   root      14648 2009-11-11 05:35 column
-rwxr-xr-x  1 root   root      39392 2010-03-05 14:41 comm
-rwxr-xr-x  1 root   root       6304 2009-11-27 10:20 compare
-rwxr-xr-x  1 root   root     255296 2010-04-09 20:15 compiz
-rwxr-xr-x  1 root   root       3144 2010-04-09 20:15 compiz-decorator
lrwxrwxrwx  1 root   root         11 2010-06-18 15:37 compose -> run-mailcap
-rwxr-xr-x  1 root   root       6304 2009-11-27 10:20 composite
-rwxr-xr-x  1 root   root       7243 2010-04-23 18:37 config_data
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 conjure
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 convert
-rwxr-xr-x  1 root   root       6516 2010-04-23 18:37 corelist
-rwxr-xr-x  1 root   root      10294 2010-03-11 05:21 couchdb
-rwxr-xr-x  1 root   root         63 2009-08-19 21:10 couchdb-dump
-rwxr-xr-x  1 root   root         63 2009-08-19 21:10 couchdb-load
-rwxr-xr-x  1 root   root       2513 2010-03-11 05:21 couchjs
-rwxr-xr-x  1 root   root         57 2009-08-19 21:10 couchpy
-rwxr-xr-x  1 root   root      11839 2010-04-23 18:37 cpan
-rwxr-xr-x  1 root   root      22409 2010-04-23 18:37 cpan2dist
-rwxr-xr-x  1 root   root       3398 2010-04-23 18:37 cpanp
-rwxr-xr-x  1 root   root        536 2010-04-23 18:37 cpanp-run-perl
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 cpp -> cpp-4.4
-rwxr-xr-x  1 root   root     255192 2010-03-27 11:13 cpp-4.4
-rwxr-xr-x  1 root   root      30744 2010-04-15 16:42 cpufreq-selector
-rwxr-xr-x  1 root   root       3899 2010-03-31 05:11 c_rehash
-rwxr-sr-x  1 root   crontab   36952 2010-04-15 16:51 crontab
-rwxr-xr-x  1 root   root     117488 2010-03-05 14:41 csplit
-rwxr-xr-x  1 root   root      18888 2009-11-06 02:19 csslint-0.6
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 ctstat -> lnstat
-rwxr-xr-x  1 root   root      39192 2010-02-12 22:05 cups-calibrate
-rwxr-xr-x  1 root   root      14256 2010-06-19 01:19 cupstestdsc
-rwxr-xr-x  1 root   root      59392 2010-06-19 01:19 cupstestppd
-rwxr-xr-x  1 root   root      51744 2010-03-05 14:41 cut
-rwxr-xr-x  1 root   root      14520 2010-06-16 19:39 cvt
-rwxr-xr-x  1 root   root     193448 2004-10-27 12:08 daemon
-rwxr-xr-x  1 root   root       1465 2010-03-07 04:01 dbilogstrip
-rwxr-xr-x  1 root   root       6300 2010-03-07 04:01 dbiprof
-rwxr-xr-x  1 root   root       5482 2010-03-07 04:01 dbiproxy
-rwxr-xr-x  1 root   root       8960 2010-04-14 06:20 dbmmanage
-rwxr-xr-x  1 root   root      27256 2010-03-31 05:43 dbus-launch
-rwxr-xr-x  1 root   root      14704 2010-03-31 05:43 dbus-monitor
-rwxr-xr-x  1 root   root      18912 2010-03-31 05:43 dbus-send
-rwxr-xr-x  1 root   root      43408 2009-12-22 09:14 dc
-rwxr-xr-x  1 root   root      10432 2010-03-05 14:58 dccleancrw
-rwxr-xr-x  1 root   root      14720 2010-03-05 14:58 dcfujigreen
-rwxr-xr-x  1 root   root      10392 2010-03-05 14:58 dcfujiturn
-rwxr-xr-x  1 root   root      10408 2010-03-05 14:58 dcfujiturn16
-rwxr-xr-x  1 root   root      47384 2010-03-05 14:58 dcparse
-rwxr-xr-x  1 root   root     310112 2010-03-05 14:58 dcraw
-rwxr-xr-x  1 root   root      11024 2010-03-23 04:57 ddate
-rwxr-xr-x  1 root   root      10472 2010-03-13 01:29 deallocvt
-rwxr-xr-x  1 root   root       2838 2010-04-10 00:33 debconf
-rwxr-xr-x  1 root   root      11541 2010-04-10 00:33 debconf-apt-progress
-rwxr-xr-x  1 root   root        608 2010-04-10 00:33 debconf-communicate
-rwxr-xr-x  1 root   root       1719 2010-04-10 00:33 debconf-copydb
-rwxr-xr-x  1 root   root        647 2010-04-10 00:33 debconf-escape
-rwxr-xr-x  1 root   root       2985 2010-04-10 00:33 debconf-set-selections
-rwxr-xr-x  1 root   root       1827 2010-04-10 00:33 debconf-show
-rwxr-xr-x  1 root   root       3622 2006-06-18 01:54 defoma
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 defoma-app -> defoma
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 defoma-font -> defoma
-rwxr-xr-x  1 root   root       2038 2006-06-18 01:54 defoma-hints
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 defoma-id -> defoma
-rwxr-xr-x  1 root   root      17711 2006-06-23 03:43 defoma-psfont-installer
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 defoma-subst -> defoma
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 defoma-user -> defoma
-rwxr-xr-x  1 root   root       6288 2010-03-23 04:57 delpart
-rwxr-xr-x  1 root   root      64440 2010-04-09 21:54 desktop-file-install
-rwxr-xr-x  1 root   root      56272 2010-04-09 21:54 desktop-file-validate
-rwxr-xr-x  1 root   root     159568 2010-03-20 06:50 devdump
-rwxr-xr-x  1 root   root       8501 2010-04-01 22:07 dexconf
-rwxr-xr-x  1 root   root      23232 2010-04-09 21:25 dfutool
-rwxr-xr-x  1 root   root       2527 2010-04-14 23:32 dh_bash-completion
-rwxr-xr-x  1 root   root       4108 2010-03-28 16:52 dh_dkms
-rwxr-xr-x  1 root   root       1761 2006-06-18 01:54 dh_installdefoma
-rwxr-xr-x  1 root   root       9379 2009-11-10 22:10 dh_installxmlcatalogs
-rwxr-xr-x  1 root   root      25903 2010-04-01 01:26 dh_pycentral
-rwxr-xr-x  1 root   root      11671 2009-11-19 05:15 dh_pysupport
-rwxr-xr-x  1 root   root      76552 2009-11-05 17:33 diff
-rwxr-xr-x  1 root   root      27104 2009-11-05 17:33 diff3
-rwxr-xr-x  1 root   root     132320 2010-03-23 07:00 dig
-rwxr-xr-x  1 root   root      43496 2010-03-05 14:41 dircolors
lrwxrwxrwx  1 root   root         12 2010-06-18 15:37 directomatic -> foomatic-rip
-rwxr-xr-x  1 root   root      35248 2010-03-05 14:41 dirname
-rwxr-xr-x  1 root   root      17143 2006-11-26 10:13 dirsplit
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 display
-rwxr-xr-x  1 root   root      26976 2010-03-13 05:09 djpeg
-rwxr-xr-x  1 root   root       3603 2010-06-01 20:11 do-release-upgrade
-rwxr-sr-x  1 root   mail      14848 2010-01-15 03:56 dotlockfile
-rwxr-xr-x  1 root   root     418216 2010-06-29 03:41 dpkg
-rwxr-xr-x  1 root   root     260392 2010-06-29 03:41 dpkg-deb
-rwxr-xr-x  1 root   root      12010 2010-06-29 03:40 dpkg-divert
-rwxr-xr-x  1 root   root     113688 2010-06-29 03:41 dpkg-query
-rwxr-xr-x  1 root   root      47800 2010-06-29 03:41 dpkg-split
-rwxr-xr-x  1 root   root     105408 2010-06-29 03:41 dpkg-statoverride
-rwxr-xr-x  1 root   root      97128 2010-06-29 03:41 dpkg-trigger
-rwxr-xr-x  1 root   root      24089 2010-04-23 18:37 dprofpp
-rwxr-xr-x  1 root   root     101216 2010-03-05 14:41 du
-rwxr-xr-x  1 root   root        596 2010-07-13 03:58 dumphint
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 dumpkeys -> /bin/dumpkeys
-rwxr-xr-x  1 root   root      22760 2009-12-06 09:03 dvd-ram-control
-rwxr-xr-x  1 root   root      43280 2009-12-06 09:03 dvd+rw-booktype
-rwxr-xr-x  1 root   root      47512 2009-12-06 09:03 dvd+rw-format
-rwxr-xr-x  1 root   root      55560 2009-12-06 09:03 dvd+rw-mediainfo
-rwxr-xr-x  1 root   root       1054 2010-07-13 03:58 dvipdf
-rwxr-xr-x  1 root   root      27576 2010-03-29 09:34 dwell-click-applet
lrwxrwxrwx  1 root   root         11 2010-06-18 15:37 edit -> run-mailcap
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 editor -> /etc/alternatives/editor
-rwxr-xr-x  1 root   root      58664 2010-03-23 07:28 editres
-rwxr-xr-x  1 root   root      27824 2009-11-10 19:07 eject
-rwxr-xr-x  1 root   root      39204 2010-04-23 18:37 enc2xs
-rwxr-xr-x  1 root   root      14696 2010-04-13 22:57 enchant
-rwxr-xr-x  1 root   root      10432 2010-04-13 22:57 enchant-lsmod
-rwxr-xr-x  1 root   root      35264 2010-03-05 14:41 env
-rwxr-xr-x  1 root   root      31232 2010-03-05 15:59 envsubst
-rwxr-xr-x  1 root   root     540416 2010-03-30 19:41 eog
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 epmd -> ../lib/erlang/bin/epmd
-rwxr-xr-x  1 root   root        674 2010-07-13 03:58 eps2eps
-rwxr-xr-x  1 root   root     161384 2010-02-22 21:23 eqn
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 erl -> ../lib/erlang/bin/erl
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 erlc -> ../lib/erlang/bin/erlc
lrwxrwxrwx  1 root   root         50 2010-06-18 15:37 erl_call -> ../lib/erlang/lib/erl_interface-3.6.4/bin/erl_call
-rwxr-xr-x  1 root   root      10376 2010-03-07 14:48 esc-m
lrwxrwxrwx  1 root   root         25 2010-06-18 15:37 escript -> ../lib/erlang/bin/escript
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 esd -> esdcompat
-rwxr-xr-x  1 root   root      10408 2009-12-19 07:29 esdcat
-rwxr-xr-x  1 root   root       2760 2010-03-27 14:56 esdcompat
-rwxr-xr-x  1 root   root      14640 2009-12-19 07:29 esdctl
-rwxr-xr-x  1 root   root       2050 2009-12-19 07:28 esddsp
-rwxr-xr-x  1 root   root      10416 2009-12-19 07:29 esdfilt
-rwxr-xr-x  1 root   root      10464 2009-12-19 07:29 esdloop
-rwxr-xr-x  1 root   root      10408 2009-12-19 07:29 esdmon
-rwxr-xr-x  1 root   root      10392 2009-12-19 07:29 esdplay
-rwxr-xr-x  1 root   root      10408 2009-12-19 07:29 esdrec
-rwxr-xr-x  1 root   root      10504 2009-12-19 07:29 esdsample
-rwxr-xr-x  1 root   root      19248 2010-03-25 15:47 espeak
-rwxr-xr-x  1 root   root    1423080 2010-04-10 03:36 eventlogadm
-rwxr-xr-x  1 root   root     403560 2010-07-08 00:41 evince
-rwxr-xr-x  1 root   root      47200 2010-07-08 00:41 evince-previewer
-rwxr-xr-x  1 root   root      14440 2010-07-08 00:41 evince-thumbnailer
lrwxrwxrwx  1 root   root         20 2010-06-18 15:37 ex -> /etc/alternatives/ex
-rwxr-xr-x  1 root   root       1133 2010-03-13 05:09 exifautotran
-rwxr-xr-x  1 root   root      39376 2010-03-05 14:41 expand
-rwxr-sr-x  1 root   shadow    23232 2010-01-27 04:09 expiry
-rwxr-xr-x  1 root   root     113264 2010-03-05 14:41 expr
-rwxr-xr-x  1 root   root      30976 2008-07-16 00:55 extlinux
-rwxr-xr-x  1 root   root      39360 2010-03-05 14:41 factor
-rwxr-xr-x  1 root   root      14976 2010-01-27 04:09 faillog
-rwxr-xr-x  1 root   root      18792 2010-01-08 18:32 faked-sysv
-rwxr-xr-x  1 root   root      22944 2010-01-08 18:32 faked-tcp
lrwxrwxrwx  1 root   root         26 2010-06-18 16:37 fakeroot -> /etc/alternatives/fakeroot
-rwxr-xr-x  1 root   root       3614 2010-01-08 18:32 fakeroot-sysv
-rwxr-xr-x  1 root   root       3610 2010-01-08 18:32 fakeroot-tcp
-rwxr-xr-x  1 root   root      10456 2010-03-23 04:57 fallocate
-rwxr-xr-x  1 root   root      14768 2010-01-21 02:38 fc-cache
-rwxr-xr-x  1 root   root      14672 2010-01-21 02:38 fc-cat
-rwxr-xr-x  1 root   root      10496 2010-01-21 02:38 fc-list
-rwxr-xr-x  1 root   root      10568 2010-01-21 02:38 fc-match
-rwxr-xr-x  1 root   root      10448 2010-01-21 02:38 fc-query
-rwxr-xr-x  1 root   root      10488 2010-01-21 02:38 fc-scan
-rwxr-xr-x  1 root   root      18768 2010-04-02 06:28 file
-rwxr-xr-x  1 root   root     411728 2010-04-30 01:01 file-roller
-rwxr-xr-x  1 root   root     229928 2010-03-10 00:23 find
-rwxr-xr-x  1 root   root      23599 2010-04-23 18:37 find2perl
-rwxr-xr-x  1 root   root       4603 2010-04-10 03:34 findsmb
-rwxr-xr-x  1 root   root      23552 2010-03-05 14:10 finger
lrwxrwxrwx  1 root   root         31 2010-09-09 07:38 firefox -> ../lib/firefox-3.6.9/firefox.sh
-rwxr-xr-x  1 root   root      14616 2010-03-23 04:57 flock
-rwxr-xr-x  1 root   root      43488 2010-03-05 14:41 fmt
-rwxr-xr-x  1 root   root      39392 2010-03-05 14:41 fold
-rwxr-xr-x  1 root   root        342 2010-07-13 03:58 font2c
-rwxr-xr-x  1 root   root       3244 2010-06-18 20:00 fontconfig-voodoo
-rwxr-xr-x  1 root   root      35224 2010-01-12 02:31 fonttosfnt
-rwxr-xr-x  1 root   root      75880 2010-03-25 19:12 foo2hiperc
-rwxr-xr-x  1 root   root      16926 2010-03-25 19:12 foo2hiperc-wrapper
-rwxr-xr-x  1 root   root      76096 2010-03-25 19:12 foo2hp
-rwxr-xr-x  1 root   root      18812 2010-03-25 19:12 foo2hp2600-wrapper
-rwxr-xr-x  1 root   root      76936 2010-03-25 19:12 foo2lava
-rwxr-xr-x  1 root   root      19705 2010-03-25 19:12 foo2lava-wrapper
-rwxr-xr-x  1 root   root      80064 2010-03-25 19:12 foo2oak
-rwxr-xr-x  1 root   root      17292 2010-03-25 19:12 foo2oak-wrapper
-rwxr-xr-x  1 root   root      75848 2010-03-25 19:12 foo2qpdl
-rwxr-xr-x  1 root   root      17960 2010-03-25 19:12 foo2qpdl-wrapper
-rwxr-xr-x  1 root   root      71744 2010-03-25 19:12 foo2slx
-rwxr-xr-x  1 root   root      17224 2010-03-25 19:12 foo2slx-wrapper
-rwxr-xr-x  1 root   root      71744 2010-03-25 19:12 foo2xqx
-rwxr-xr-x  1 root   root      16463 2010-03-25 19:12 foo2xqx-wrapper
-rwxr-xr-x  1 root   root      71744 2010-03-25 19:12 foo2zjs
-rwxr-xr-x  1 root   root     172200 2010-03-25 19:12 foo2zjs-icc2ps
-rwxr-xr-x  1 root   root       1689 2010-03-25 19:12 foo2zjs-pstops
-rwxr-xr-x  1 root   root      18817 2010-03-25 19:12 foo2zjs-wrapper
-rwxr-xr-x  1 root   root      43344 2010-02-16 04:42 foomatic-combo-xml
-rwxr-xr-x  1 root   root       4629 2010-02-16 04:42 foomatic-compiledb
-rwxr-xr-x  1 root   root     136795 2010-02-16 04:42 foomatic-configure
lrwxrwxrwx  1 root   root         16 2010-06-18 15:37 foomatic-datafile -> foomatic-ppdfile
-rwxr-xr-x  1 root   root      80200 2010-02-16 04:42 foomatic-perl-data
-rwxr-xr-x  1 root   root       9676 2010-02-16 04:42 foomatic-ppdfile
-rwxr-xr-x  1 root   root       4000 2010-02-16 04:42 foomatic-ppd-options
-rwxr-xr-x  1 root   root       9003 2010-02-16 04:42 foomatic-ppd-to-xml
-rwxr-xr-x  1 root   root      35088 2010-02-16 04:42 foomatic-printjob
-rwxr-xr-x  1 root   root     107272 2010-02-16 04:04 foomatic-rip
-rwxr-xr-x  1 root   root       2487 2010-02-16 04:42 foomatic-searchprinter
-rwxr-xr-x  1 root   root      10424 2009-12-17 06:34 free
-rwxr-xr-x  1 root   root      15488 2010-02-23 01:59 fribidi
-rwxr-xr-x  1 root   root      10440 2009-11-11 05:35 from
-rwxr-xr-x  1 root   root      14600 2010-03-07 20:57 fslsfonts
-rwxr-xr-x  1 root   root      14912 2010-03-07 20:57 fstobdf
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 ftp -> /etc/alternatives/ftp
-rwxr-xr-x  1 root   root      22824 2010-03-07 20:33 funzip
-rwxr-xr-x  1 root   root         78 2010-04-23 02:38 gacutil
-rwxr-xr-x  1 root   root         78 2010-04-23 02:12 gacutil2
-rwxr-xr-x  1 root   root       6280 2010-04-15 17:25 gamma4scanimage
-rwxr-xr-x  1 root   root     123536 2009-11-07 10:42 gapcmon
-rwxr-xr-x  1 root   root     356072 2009-12-11 14:45 gawk
-rwxr-xr-x  1 root   root     204856 2010-04-09 21:18 gcalctool
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 gcc -> gcc-4.4
-rwxr-xr-x  1 root   root     255192 2010-03-27 11:19 gcc-4.4
-rwxr-xr-x  1 root   root     125416 2010-03-31 05:57 gconf-editor
-rwxr-xr-x  1 root   root      52496 2010-03-31 04:17 gconf-merge-tree
lrwxrwxrwx  1 root   root         27 2010-06-18 15:37 gconftool -> /etc/alternatives/gconftool
-rwxr-xr-x  1 root   root      64736 2010-03-31 04:17 gconftool-2
-rwxr-xr-x  1 root   root       1873 2010-01-01 18:31 gcore
lrwxrwxrwx  1 root   root          8 2010-06-18 15:37 gcov -> gcov-4.4
-rwxr-xr-x  1 root   root      35312 2010-03-27 11:19 gcov-4.4
-rwxr-xr-x  1 root   root    4345264 2010-04-09 23:38 gdb
-rwxr-xr-x  1 root   root        126 2010-04-09 23:37 gdbtui
-rwxr-xr-x  1 root   root       3899 2010-04-09 19:51 gdebi
-rwxr-xr-x  1 root   root       3094 2010-04-09 19:51 gdebi-gtk
-rwxr-xr-x  1 root   root       9228 2010-03-29 22:03 gdialog
lrwxrwxrwx  1 root   root         43 2010-07-06 10:07 gdk-pixbuf-query-loaders -> ../lib/libgtk2.0-0/gdk-pixbuf-query-loaders
-rwxr-xr-x  1 root   root      19496 2010-07-22 00:14 gdmflexiserver
-rwxr-xr-x  1 root   root      14920 2010-07-22 00:14 gdm-screenshot
-rwxr-xr-x  1 root   root      69448 2010-07-22 00:14 gdmsetup
-rwxr-xr-x  1 root   root     688064 2010-06-25 06:35 gedit
-rwxr-xr-x  1 root   root      23040 2010-06-14 23:58 gencat
-rwxr-xr-x  1 root   root     605096 2010-03-20 06:50 genisoimage
lrwxrwxrwx  1 root   root          3 2010-06-18 15:37 geqn -> eqn
lrwxrwxrwx  1 root   root         11 2010-09-01 07:47 GET -> lwp-request
-rwxr-xr-x  1 root   root      22800 2010-06-14 23:58 getconf
-rwxr-xr-x  1 root   root       5832 2010-03-20 06:50 geteltorito
-rwxr-xr-x  1 root   root      23672 2010-06-14 23:58 getent
-rwxr-xr-x  1 root   root       6216 2008-07-16 00:55 gethostip
-rwxr-xr-x  1 root   root      10464 2010-03-13 01:29 getkeycodes
-rwxr-xr-x  1 root   root      15008 2010-03-23 04:57 getopt
-rwxr-xr-x  1 root   root      31208 2010-03-05 15:59 gettext
-rwxr-xr-x  1 root   root       4653 2010-03-05 15:59 gettext.sh
-rwxr-xr-x  1 root   root      12890 2010-03-25 19:12 getweb
lrwxrwxrwx  1 root   root          2 2010-07-14 07:45 ghostscript -> gs
-rwxr-xr-x  1 root   root      40512 2010-02-12 00:49 ginstall-info
-rwxr-xr-x  1 root   root      10512 2010-05-09 21:23 gio-querymodules
-rwxr-xr-x  1 root   root      58440 2010-03-25 19:12 gipddecode
-rwxr-xr-x  1 root   root      28256 2010-03-05 16:05 gksu
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 gksudo -> gksu
-rwxr-xr-x  1 root   root      14736 2010-01-08 19:48 gksu-properties
-rwxr-xr-x  1 root   root        831 2010-04-09 19:30 gmenu-simple-editor
-rwxr-xr-x  1 root   root      37070 2010-06-25 20:51 gnome-about
-rwxr-xr-x  1 root   root      83400 2010-04-29 19:09 gnome-about-me
-rwxr-xr-x  1 root   root     229752 2010-04-29 19:09 gnome-appearance-properties
-rwxr-xr-x  1 root   root       2205 2010-04-29 19:09 gnome-at-mobility
-rwxr-xr-x  1 root   root      56896 2010-04-29 19:09 gnome-at-properties
-rwxr-xr-x  1 root   root       2205 2010-04-29 19:09 gnome-at-visual
-rwxr-xr-x  1 root   root      10544 2010-03-30 10:34 gnome-audio-profiles-properties
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 gnome-calculator -> gcalctool
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 gnome-character-map -> gucharmap
-rwxr-xr-x  1 root   root        168 2010-01-21 22:11 gnome-codec-install
-rwxr-xr-x  1 root   root     128144 2010-04-29 19:09 gnome-control-center
-rwxr-xr-x  1 root   root      73752 2010-04-29 19:09 gnome-default-applications-properties
-rwxr-xr-x  1 root   root     107760 2010-07-08 01:19 gnome-desktop-item-edit
-rwxr-xr-x  1 root   root     107680 2010-03-31 21:57 gnome-dictionary
-rwxr-xr-x  1 root   root      69688 2010-04-29 19:09 gnome-display-properties
-rwxr-xr-x  1 root   root       9503 2010-04-19 16:26 gnome-doc-prepare
-rwxr-xr-x  1 root   root      20530 2010-04-19 16:26 gnome-doc-tool
-rwxr-xr-x  1 root   root      23280 2010-04-16 02:37 gnome-file-share-properties
-rwxr-xr-x  1 root   root      27752 2010-04-29 19:09 gnome-font-viewer
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 gnome-help -> yelp
-rwxr-xr-x  1 root   root      65600 2010-04-29 19:09 gnome-keybinding-properties
-rwxr-xr-x  1 root   root     107704 2010-04-29 19:09 gnome-keyboard-properties
-rwxr-xr-x  1 root   root      14968 2010-06-25 20:54 gnome-keyring
-rwxr-xr-x  1 root   root     857616 2010-06-25 20:54 gnome-keyring-daemon
-rwxr-xr-x  1 root   root        871 2010-06-18 20:00 gnome-language-selector
-rwxr-xr-x  1 root   root      73840 2010-04-29 19:09 gnome-mouse-properties
-rwxr-xr-x  1 root   root     115376 2010-04-02 06:46 gnome-nettool
-rwxr-xr-x  1 root   root      77976 2010-04-29 19:09 gnome-network-properties
-rwxr-xr-x  1 root   root      10440 2010-03-31 09:02 gnome-open
-rwxr-xr-x  1 root   root     616096 2010-07-08 01:19 gnome-panel
lrwxrwxrwx  1 root   root         16 2010-06-18 15:37 gnome-panel-screenshot -> gnome-screenshot
-rwxr-xr-x  1 root   root     201600 2010-03-29 23:48 gnome-power-manager
-rwxr-xr-x  1 root   root      44184 2010-03-29 23:48 gnome-power-preferences
-rwxr-xr-x  1 root   root      77640 2010-03-29 23:48 gnome-power-statistics
-rwxr-xr-x  1 root   root      66064 2010-03-31 21:57 gnome-screenshot
-rwxr-xr-x  1 root   root     176600 2010-03-31 21:57 gnome-search-tool
-rwxr-xr-x  1 root   root     227504 2010-03-31 02:24 gnome-session
-rwxr-xr-x  1 root   root      65624 2010-03-31 02:24 gnome-session-properties
-rwxr-xr-x  1 root   root      10944 2010-03-31 02:24 gnome-session-save
lrwxrwxrwx  1 root   root         50 2010-06-18 16:12 gnome-settings-daemon -> ../lib/gnome-settings-daemon/gnome-settings-daemon
-rwxr-xr-x  1 root   root      69872 2010-03-30 10:34 gnome-sound-recorder
-rwxr-xr-x  1 root   root     113328 2010-03-31 21:57 gnome-system-log
-rwxr-xr-x  1 root   root     244816 2010-01-20 09:06 gnome-system-monitor
-rwxr-xr-x  1 root   root     305464 2010-03-26 23:09 gnome-terminal
-rwxr-xr-x  1 root   root       1394 2010-03-26 23:08 gnome-terminal.wrapper
lrwxrwxrwx  1 root   root         35 2010-07-06 10:09 gnome-text-editor -> /etc/alternatives/gnome-text-editor
-rwxr-xr-x  1 root   root      23128 2010-04-29 19:09 gnome-thumbnail-font
-rwxr-xr-x  1 root   root      40488 2010-04-29 19:09 gnome-typing-monitor
-rwxr-xr-x  1 root   root     173600 2010-03-30 10:34 gnome-volume-control
-rwxr-xr-x  1 root   root     115240 2010-03-30 10:34 gnome-volume-control-applet
-rwxr-xr-x  1 root   root      23352 2010-04-29 19:09 gnome-window-properties
-rwxr-xr-x  1 root   root       4504 2010-03-30 20:23 gnome-wm
lrwxrwxrwx  1 root   root         35 2010-06-18 15:37 gnome-www-browser -> /etc/alternatives/gnome-www-browser
-rwsr-xr-x  1 root   root      63848 2010-01-27 04:09 gpasswd
-rwxr-xr-x  1 root   root     975264 2010-01-05 21:44 gpg
-rwxr-xr-x  1 root   root      56144 2010-01-05 21:44 gpgsplit
-rwxr-xr-x  1 root   root     355984 2010-01-05 21:44 gpgv
-rwxr-xr-x  1 root   root       3303 2010-01-05 21:44 gpg-zip
lrwxrwxrwx  1 root   root          3 2010-06-18 15:37 gpic -> pic
-rwxr-xr-x  1 root   root      94472 2010-06-18 21:43 gprof
-rwxr-xr-x  1 root   root      83792 2010-02-22 21:23 groff
-rwxr-xr-x  1 root   root       9269 2010-02-22 21:23 grog
-rwxr-xr-x  1 root   root     145648 2010-02-22 21:23 grops
-rwxr-xr-x  1 root   root     100144 2010-02-22 21:23 grotty
-rwxr-xr-x  1 root   root      39392 2010-03-05 14:41 groups
-rwxr-xr-x  1 root   root      89016 2009-12-06 09:03 growisofs
-rwxr-xr-x  1 root   root      10504 2010-07-02 07:28 grub-bin2h
-rwxr-xr-x  1 root   root      31280 2010-07-02 07:28 grub-editenv
-rwxr-xr-x  1 root   root      23272 2010-07-02 07:28 grub-mkelfimage
-rwxr-xr-x  1 root   root      23528 2010-07-02 07:28 grub-mkfont
-rwxr-xr-x  1 root   root      47896 2010-07-02 07:28 grub-mkimage
-rwxr-xr-x  1 root   root      97656 2010-07-02 07:28 grub-mkisofs
-rwxr-xr-x  1 root   root      31656 2010-07-02 07:28 grub-mkpasswd-pbkdf2
-rwxr-xr-x  1 root   root      14824 2010-07-02 07:28 grub-mkrelpath
-rwxr-xr-x  1 root   root       5925 2010-07-02 07:26 grub-mkrescue
-rwxr-xr-x  1 root   root      39840 2010-07-02 07:28 grub-script-check
-rwxr-xr-x  1 root   root      10408 2010-07-13 03:58 gs
-rwxr-xr-x  1 root   root        379 2010-07-13 03:58 gsbj
-rwxr-xr-x  1 root   root        381 2010-07-13 03:58 gsdj
-rwxr-xr-x  1 root   root        384 2010-07-13 03:58 gsdj500
-rwxr-xr-x  1 root   root        382 2010-07-13 03:58 gslj
-rwxr-xr-x  1 root   root        379 2010-07-13 03:58 gslp
-rwxr-xr-x  1 root   root        306 2010-07-13 03:58 gsnd
-rwxr-xr-x  1 root   root       3173 2010-03-10 06:03 gst-feedback-0.10
-rwxr-xr-x  1 root   root      40096 2010-03-10 06:03 gst-inspect-0.10
-rwxr-xr-x  1 root   root      27552 2010-03-10 06:03 gst-launch-0.10
lrwxrwxrwx  1 root   root         41 2010-06-18 15:37 gstreamer-codec-install -> /etc/alternatives/gstreamer-codec-install
-rwxr-xr-x  1 root   root      29720 2010-03-30 10:34 gstreamer-properties
-rwxr-xr-x  1 root   root      14832 2010-03-10 06:03 gst-typefind-0.10
-rwxr-xr-x  1 root   root       1734 2010-03-10 10:42 gst-visualise-0.10
-rwxr-xr-x  1 root   root      23144 2010-03-10 06:03 gst-xmlinspect-0.10
-rwxr-xr-x  1 root   root      27560 2010-03-10 06:03 gst-xmllaunch-0.10
lrwxrwxrwx  1 root   root          3 2010-06-18 15:37 gtbl -> tbl
-rwxr-xr-x  1 root   root      14504 2010-06-16 19:39 gtf
lrwxrwxrwx  1 root   root         42 2010-07-06 10:07 gtk-query-immodules-2.0 -> ../lib/libgtk2.0-0/gtk-query-immodules-2.0
lrwxrwxrwx  1 root   root         40 2010-07-06 10:07 gtk-update-icon-cache -> ../lib/libgtk2.0-0/gtk-update-icon-cache
-rwxr-xr-x  1 root   root      95024 2010-04-09 20:15 gtk-window-decorator
-rwxr-xr-x  1 root   root      74168 2010-03-30 01:39 gucharmap
-rwxr-xr-x  1 root   root      10664 2010-05-12 20:02 gvfs-cat
-rwxr-xr-x  1 root   root      10904 2010-05-12 20:02 gvfs-copy
-rwxr-xr-x  1 root   root      15000 2010-05-12 20:02 gvfs-info
-rwxr-xr-x  1 root   root        879 2010-05-12 20:01 gvfs-less
-rwxr-xr-x  1 root   root      15168 2010-05-12 20:02 gvfs-ls
-rwxr-xr-x  1 root   root      10568 2010-05-12 20:02 gvfs-mkdir
-rwxr-xr-x  1 root   root      10576 2010-05-12 20:02 gvfs-monitor-dir
-rwxr-xr-x  1 root   root      10576 2010-05-12 20:02 gvfs-monitor-file
-rwxr-xr-x  1 root   root      27496 2010-05-12 20:02 gvfs-mount
-rwxr-xr-x  1 root   root      10808 2010-05-12 20:02 gvfs-move
-rwxr-xr-x  1 root   root      10632 2010-05-12 20:02 gvfs-open
-rwxr-xr-x  1 root   root      10464 2010-05-12 20:02 gvfs-rename
-rwxr-xr-x  1 root   root      10560 2010-05-12 20:02 gvfs-rm
-rwxr-xr-x  1 root   root      10904 2010-05-12 20:02 gvfs-save
-rwxr-xr-x  1 root   root      10664 2010-05-12 20:02 gvfs-set-attribute
-rwxr-xr-x  1 root   root      10568 2010-05-12 20:02 gvfs-trash
-rwxr-xr-x  1 root   root      10728 2010-05-12 20:02 gvfs-tree
-rwxr-xr-x  1 root   root       2661 2010-07-10 00:01 gwibber-service
-rwxr-xr-x  1 root   root      28036 2010-04-23 18:37 h2ph
-rwxr-xr-x  1 root   root      60385 2010-04-23 18:37 h2xs
-rwxr-xr-x  1 root   root      19112 2010-05-09 21:59 hal-device
-rwxr-xr-x  1 root   root      14864 2010-05-09 21:59 hal-disable-polling
-rwxr-xr-x  1 root   root      10640 2010-05-09 21:59 hal-find-by-capability
-rwxr-xr-x  1 root   root      10672 2010-05-09 21:59 hal-find-by-property
-rwxr-xr-x  1 root   root      10768 2010-05-09 21:59 hal-get-property
-rwxr-xr-x  1 root   root      10680 2010-05-09 21:59 hal-is-caller-locked-out
-rwxr-xr-x  1 root   root      14984 2010-05-09 21:59 hal-lock
-rwxr-xr-x  1 root   root      15152 2010-05-09 21:59 hal-set-property
-rwxr-xr-x  1 root   root      54256 2010-04-09 21:25 hcitool
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 hd -> hexdump
-rwxr-xr-x  1 root   root      47616 2010-03-05 14:41 head
lrwxrwxrwx  1 root   root         11 2010-09-01 07:47 HEAD -> lwp-request
-rwxr-xr-x  1 root   root       2126 2010-04-16 23:19 helpztags
-rwxr-xr-x  1 root   root      31176 2009-11-11 05:35 hexdump
-rwxr-xr-x  1 root   root      58440 2010-03-25 19:12 hipercdecode
-rwxr-xr-x  1 root   root     120328 2010-03-23 07:00 host
-rwxr-xr-x  1 root   root      35232 2010-03-05 14:41 hostid
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-align -> ../share/hplip/align.py
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-clean -> ../share/hplip/clean.py
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 hp-colorcal -> ../share/hplip/colorcal.py
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 hp-fab -> ../share/hplip/fab.py
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 hp-firmware -> ../share/hplip/firmware.py
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-hpdio -> ../share/hplip/hpdio.py
-rwxr-xr-x  1 root   root     611872 2010-04-12 20:48 hpijs
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 hp-info -> ../share/hplip/info.py
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 hp-levels -> ../share/hplip/levels.py
lrwxrwxrwx  1 root   root         25 2010-06-18 15:37 hp-makeuri -> ../share/hplip/makeuri.py
-rwxr-xr-x  1 root   root      19080 2010-04-12 20:48 hp-mkuri
lrwxrwxrwx  1 root   root         27 2010-06-18 15:37 hp-pkservice -> ../share/hplip/pkservice.py
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 hp-plugin -> ../share/hplip/plugin.py
-rwxr-xr-x  1 root   root        662 2010-04-12 20:47 hp-plugin-ubuntu
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-probe -> ../share/hplip/probe.py
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-query -> ../share/hplip/query.py
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 hp-scan -> ../share/hplip/scan.py
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 hp-setup -> ../share/hplip/setup.py
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 hp-testpage -> ../share/hplip/testpage.py
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 hp-timedate -> ../share/hplip/timedate.py
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 hp-unload -> ../share/hplip/unload.py
-rwxr-xr-x  1 root   root      18440 2010-04-14 06:23 htdbm
-rwxr-xr-x  1 root   root      14352 2010-04-14 06:23 htdigest
-rwxr-xr-x  1 root   root      14352 2010-04-14 06:23 htpasswd
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 i386 -> setarch
-rwxr-xr-x  1 root   root     131096 2010-03-28 05:12 ibus-daemon
-rwxr-xr-x  1 root   root       1082 2010-03-28 05:12 ibus-setup
-rwxr-xr-x  1 root   root       1131 2010-02-02 13:07 ibus-table-createdb
-rwxr-xr-x  1 root   root      27088 2010-03-20 11:55 iceauth
-rwxr-xr-x  1 root   root      45760 2010-03-13 06:40 ico
-rwxr-xr-x  1 root   root      60272 2010-06-14 23:58 iconv
-rwxr-xr-x  1 root   root      39440 2010-03-05 14:41 id
-rwxr-xr-x  1 root   root       6312 2009-11-27 10:20 identify
-rwxr-xr-x  1 root   root      18760 2010-03-29 10:04 iecset
-rwxr-xr-x  1 root   root       3091 2009-12-11 14:45 igawk
-rwxr-xr-x  1 root   root      39832 2009-09-19 03:01 ijs_pxljr
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 import
-rwxr-xr-x  1 root   root      14184 2009-12-06 14:03 im-switch
-rwxr-xr-x  1 root   root     178024 2010-02-12 00:49 info
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 infobrowser -> /etc/alternatives/infobrowser
-rwxr-xr-x  1 root   root      51824 2010-03-07 15:25 infocmp
-rwxr-xr-x  1 root   root      20824 2010-02-12 00:49 infokey
lrwxrwxrwx  1 root   root          3 2010-06-18 15:37 infotocap -> tic
-rwxr-xr-x  1 root   root      14256 2010-07-30 08:54 innochecksum
-rwxr-xr-x  1 root   root     400192 2010-07-30 08:53 innotop
-rwxr-xr-x  1 root   root      17080 2010-01-28 22:11 inputattach
-rwxr-xr-x  1 root   root      97448 2010-03-05 14:41 install
-rwxr-xr-x  1 root   root       1216 2010-02-12 00:49 install-info
-rwxr-xr-x  1 root   root     232928 2010-02-05 04:59 install-menu
-rwxr-xr-x  1 root   root       4336 2010-04-23 18:37 instmodsh
-rwxr-xr-x  1 root   root      26904 2010-04-02 06:45 intel_audio_dump
-rwxr-xr-x  1 root   root      10456 2010-04-02 06:45 intel_bios_dumper
-rwxr-xr-x  1 root   root      18640 2010-04-02 06:45 intel_bios_reader
-rwxr-xr-x  1 root   root      63896 2010-04-02 06:45 intel_error_decode
-rwxr-xr-x  1 root   root      63888 2010-04-02 06:45 intel_gpu_dump
-rwxr-xr-x  1 root   root      14664 2010-04-02 06:45 intel_gpu_time
-rwxr-xr-x  1 root   root      27024 2010-04-02 06:45 intel_gpu_top
-rwxr-xr-x  1 root   root      14608 2010-04-02 06:45 intel_gtt
-rwxr-xr-x  1 root   root      14688 2010-04-02 06:45 intel_lid
-rwxr-xr-x  1 root   root      43312 2010-04-02 06:45 intel_reg_dumper
-rwxr-xr-x  1 root   root      14616 2010-04-02 06:45 intel_reg_read
-rwxr-xr-x  1 root   root      14616 2010-04-02 06:45 intel_reg_write
-rwxr-xr-x  1 root   root      10408 2010-04-02 06:45 intel_stepping
-rwxr-xr-x  1 root   root      14640 2010-04-02 06:45 intel_upload_blit_large
-rwxr-xr-x  1 root   root      14656 2010-04-02 06:45 intel_upload_blit_large_gtt
-rwxr-xr-x  1 root   root      14656 2010-04-02 06:45 intel_upload_blit_large_map
-rwxr-xr-x  1 root   root      14648 2010-04-02 06:45 intel_upload_blit_small
-rwxr-xr-x  1 root   root        482 2010-04-15 16:42 invest-chart
-rwxr-xr-x  1 root   root      10496 2010-03-23 04:57 ionice
-rwxr-xr-x  1 root   root      10456 2010-03-23 04:57 ipcmk
-rwxr-xr-x  1 root   root      10480 2010-03-23 04:57 ipcrm
-rwxr-xr-x  1 root   root      22752 2010-03-23 04:57 ipcs
-rwxr-xr-x  1 root   root      18992 2010-04-09 22:01 ipod-read-sysinfo-extended
-rwxr-xr-x  1 root   root      10472 2010-04-09 22:01 ipod-time-sync
-rwxr-xr-x  1 root   root      10456 2010-04-09 18:39 iproxy
-rwxr-xr-x  1 root   root      18920 2010-03-06 08:03 iptables-xml
-rwxr-xr-x  1 root   root     163664 2010-03-20 06:50 isodump
-rwxr-xr-x  1 root   root     326688 2010-03-20 06:50 isoinfo
-rwxr-xr-x  1 root   root     163632 2010-03-20 06:50 isovfy
-rwxr-xr-x  1 root   root       6715 2010-01-21 11:05 ispell-wrapper
-rwxr-xr-x  1 root   root      15605 2010-05-19 02:41 jockey-gtk
-rwxr-xr-x  1 root   root       3715 2010-05-19 02:41 jockey-text
-rwxr-xr-x  1 root   root      47664 2010-03-05 14:41 join
-rwxr-xr-x  1 root   root      10392 2010-03-13 05:09 jpegexiforient
-rwxr-xr-x  1 root   root      31056 2010-03-13 05:09 jpegtran
-rwxr-xr-x  1 root   root      10552 2010-04-19 19:07 kerneloops-submit
-rwxr-xr-x  1 root   root      23616 2010-01-18 19:34 killall
-rwxr-xr-x  1 root   root       3759 2010-04-01 01:31 koi8rxterm
-rwxr-xr-x  1 root   root       1902 2010-03-20 06:46 kvm-ok
-rwxr-xr-x  1 root   root      14640 2010-04-09 21:25 l2ping
-rwxr-xr-x  1 root   root      18784 2010-03-31 01:30 last
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 lastb -> last
-rwxr-xr-x  1 root   root      14680 2010-01-27 04:09 lastlog
-rwxr-xr-x  1 root   root        237 2010-04-23 00:32 launchpad-integration
-rwxr-xr-x  1 root   root      58472 2010-03-25 19:12 lavadecode
-rwxr-xr-x  1 root   root       7812 2008-05-30 16:22 lcf
lrwxrwxrwx  1 root   root          6 2010-07-06 10:07 ld -> ld.bfd
-rwxr-xr-x  1 root   root     558824 2010-06-18 21:43 ld.bfd
-rwxr-xr-x  1 root   root       5279 2010-06-14 23:52 ldd
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 less -> /bin/less
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 lessecho -> /bin/lessecho
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 lessfile -> /bin/lesspipe
lrwxrwxrwx  1 root   root         12 2010-06-18 15:37 lesskey -> /bin/lesskey
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 lesspipe -> /bin/lesspipe
-rwxr-xr-x  1 root   root     145912 2010-03-02 21:31 lexgrog
-rwxr-xr-x  1 root   root     973592 2010-09-03 06:44 lftp
-rwxr-xr-x  1 root   root       1353 2010-09-03 06:44 lftpget
-rwxr-xr-x  1 root   root      15724 2010-04-23 18:37 libnetcfg
-rwxr-xr-x  1 root   root       6248 2010-03-23 04:57 line
-rwxr-xr-x  1 root   root      35232 2010-03-05 14:41 link
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 linux32 -> setarch
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 linux64 -> setarch
-rwxr-xr-x  1 root   root       1592 2010-02-11 10:06 linux-boot-prober
-rwxr-xr-x  1 root   root      10872 2010-03-23 07:28 listres
-rwxr-xr-x  1 root   root      14976 2010-01-18 19:11 lnstat
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 loadkeys -> /bin/loadkeys
-rwxr-xr-x  1 root   root      23096 2010-03-13 01:29 loadunimap
-rwxr-xr-x  1 root   root      38632 2010-06-14 23:58 locale
-rwxr-xr-x  1 root   root     322720 2010-06-14 23:58 localedef
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 locate -> /etc/alternatives/locate
-rwxr-xr-x  1 root   root      14704 2010-01-15 03:57 lockfile-check
-rwxr-xr-x  1 root   root      14704 2010-01-15 03:57 lockfile-create
-rwxr-xr-x  1 root   root      14704 2010-01-15 03:57 lockfile-remove
-rwxr-xr-x  1 root   root      14704 2010-01-15 03:57 lockfile-touch
-rwxr-xr-x  1 root   root      15312 2010-03-23 04:57 logger
-rwxr-xr-x  1 root   root      35248 2010-03-05 14:41 logname
-rwxr-xr-x  1 root   root      10504 2009-11-11 05:35 look
-rwxr-xr-x  1 root   root       2763 2009-11-11 05:35 lorder
-rwxr-xr-x  1 root   root      18352 2010-06-19 01:19 lp
-rwxr-xr-x  1 root   root      14336 2010-06-19 01:19 lpoptions
-rwsr-xr-x  1 root   lpadmin   14256 2010-06-19 01:19 lppasswd
-rwxr-xr-x  1 root   root      18432 2010-06-19 01:19 lpq
-rwxr-xr-x  1 root   root      14256 2010-06-19 01:19 lpr
-rwxr-xr-x  1 root   root      10160 2010-06-19 01:19 lprm
-rwxr-xr-x  1 root   root      47960 2009-12-19 05:53 lp_solve
-rwxr-xr-x  1 root   root      26840 2010-06-19 01:19 lpstat
-rwxr-xr-x  1 root   root      10504 2010-04-19 14:31 lsattr
-rwxr-xr-x  1 root   root       3638 2009-06-03 06:19 lsb_release
-rwxr-xr-x  1 root   root      22976 2010-03-23 04:57 lscpu
-rwxr-xr-x  1 root   root      23136 2010-05-09 21:59 lshal
-rwxr-xr-x  1 root   root     549080 2010-03-07 14:34 lshw
-rwxr-xr-x  1 root   root     131312 2010-03-07 14:33 lsof
-rwxr-xr-x  1 root   root      57400 2010-03-10 10:38 lspci
-rwxr-xr-x  1 root   root       1081 2008-12-12 03:39 lspgpot
-rwxr-xr-x  1 root   root       2479 2008-07-16 00:55 lss16toppm
lrwxrwxrwx  1 root   root         13 2010-06-18 15:37 lsusb -> ../sbin/lsusb
-rwxr-xr-x  1 root   root     136344 2010-03-07 14:38 ltrace
-rwxr-xr-x  1 root   root      42200 2010-03-23 07:28 luit
-rwxr-xr-x  1 root   root       8131 2010-08-28 05:32 lwp-download
-rwxr-xr-x  1 root   root       2607 2010-08-28 05:32 lwp-dump
-rwxr-xr-x  1 root   root       2389 2010-08-28 05:32 lwp-mirror
-rwxr-xr-x  1 root   root      14547 2010-08-28 05:32 lwp-request
-rwxr-xr-x  1 root   root      15062 2010-08-28 05:32 lwp-rget
-rwxr-xr-x  1 root   root        419 2010-04-01 01:31 lxterm
lrwxrwxrwx  1 root   root          2 2010-06-18 15:37 lz -> uz
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 lzcat -> lzma
-rwxr-xr-x  1 root   root     105248 2010-03-07 14:41 lzma
-rwxr-xr-x  1 root   root       3725 2009-11-06 00:41 m17n-db
-rwxr-xr-x  1 root   root     192280 2010-04-02 02:56 magnifier
lrwxrwxrwx  1 root   root         22 2010-06-26 10:00 mail -> /etc/alternatives/mail
lrwxrwxrwx  1 root   root         22 2010-06-26 10:00 Mail -> /etc/alternatives/Mail
-rwxr-sr-x  1 root   mail      14704 2010-01-15 03:57 mail-lock
lrwxrwxrwx  1 root   root         16 2010-06-26 09:59 mailq -> ../sbin/sendmail
-rwxr-sr-x  1 root   mail      14704 2010-01-15 03:57 mail-touchlock
-rwxr-sr-x  1 root   mail      14704 2010-01-15 03:57 mail-unlock
lrwxrwxrwx  1 root   root         23 2010-06-26 10:00 mailx -> /etc/alternatives/mailx
-rwxr-xr-x  1 root   root     166112 2010-03-20 13:36 make
-rwxr-xr-x  1 root   root       2524 2010-03-23 20:40 make-memtest86+-boot-floppy
-rwxr-xr-x  1 root   root      19219 2010-01-05 12:02 make_method
-rwxr-xr-x  1 root   root        893 2010-02-18 10:48 mako-render
-rwxr-xr-x  1 root   root     250808 2010-03-02 21:31 man
-rwxr-xr-x  1 root   root     269368 2010-03-02 21:31 mandb
-rwxr-xr-x  1 root   root        586 2010-04-15 14:06 manhole
-rwxr-xr-x  1 root   root      89528 2010-03-02 21:31 manpath
-rwxr-xr-x  1 root   root      19024 2010-03-13 01:29 mapscrn
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mattrib -> mtools
-rwxr-xr-x  1 root   root     117840 2010-01-15 03:59 mawk
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mbadblocks -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mcat -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mcd -> mtools
-rwxr-xr-x  1 root   root       1679 2009-11-14 05:51 mcheck
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mclasserase -> mtools
-rwxr-xr-x  1 root   root        840 2009-11-14 05:51 mcomp
-rwxr-xr-x  1 root   root      14704 2010-03-23 04:57 mcookie
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mcopy -> mtools
-rwxr-xr-x  1 root   root     118552 2010-04-09 12:36 mc-tool
-rwxr-xr-x  1 root   root      10472 2010-04-09 12:36 mc-wait-for-name
-rwxr-xr-x  1 root   root      43520 2010-03-05 14:41 md5sum
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 md5sum.textutils -> md5sum
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mdel -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mdeltree -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mdir -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mdu -> mtools
-rwxr-xr-x  1 root   root      10344 2010-03-31 01:30 mesg
-rwxr-xr-x  1 root   root     556944 2010-04-10 04:43 metacity
-rwxr-xr-x  1 root   root      10432 2010-04-10 04:43 metacity-message
-rwxr-xr-x  1 root   root      28240 2010-04-10 04:43 metacity-theme-viewer
-rwxr-xr-x  1 root   root      28352 2010-04-10 04:43 metacity-window-demo
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mformat -> mtools
-rwxr-xr-x  1 root   root      20104 2010-03-07 14:48 min12xxw
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 minfo -> mtools
-rwxr-xr-x  1 root   root       8325 2008-07-16 00:55 mkdiskimage
-rwxr-xr-x  1 root   root      39360 2010-03-05 14:41 mkfifo
-rwxr-xr-x  1 root   root        131 2010-01-12 02:31 mkfontdir
-rwxr-xr-x  1 root   root      31680 2010-01-12 02:31 mkfontscale
lrwxrwxrwx  1 root   root         11 2010-06-18 15:37 mkisofs -> genisoimage
-rwxr-xr-x  1 root   root      10536 2009-11-14 05:51 mkmanifest
-rwxr-xr-x  1 root   root      16163 2010-03-13 01:29 mk_modmap
-rwxr-xr-x  1 root   root        598 2010-04-15 14:06 mktap
-rwxr-xr-x  1 root   root      23064 2010-03-20 06:50 mkzftree
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mlabel -> mtools
-rwxr-sr-x  1 root   mlocate   35432 2010-03-24 23:35 mlocate
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mmd -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mmount -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mmove -> mtools
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 mogrify
-rwxr-xr-x  1 root   root    2536688 2010-04-23 02:30 mono
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 montage
-rwxr-xr-x  1 root   root        838 2010-03-03 18:14 motd+shell
-rwxr-xr-x  1 root   root      61288 2010-03-29 09:34 mousetweaks
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mpartition -> mtools
-rwxr-xr-x  1 root   root    4476552 2010-04-03 00:58 mplayer
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mrd -> mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mren -> mtools
-rwxr-xr-x  1 root   root      10472 2010-03-07 14:53 mscompress
-rwxr-xr-x  1 root   root      10456 2010-03-07 14:53 msexpand
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mshowfat -> mtools
-rwxr-xr-x  1 root   root       1412 2010-07-30 08:53 msql2mysql
-rwxr-xr-x  1 root   root     173824 2009-11-14 05:51 mtools
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mtoolstest -> mtools
-rwsr-xr-x  1 root   root      62416 2010-03-07 14:56 mtr
-rwxr-xr-x  1 root   root       6524 2010-06-14 23:51 mtrace
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mtype -> mtools
-rwxr-xr-x  1 root   root        777 2009-11-14 05:51 mxtar
-rwxr-xr-x  1 root   root    1875208 2010-07-30 08:54 myisamchk
-rwxr-xr-x  1 root   root    1751688 2010-07-30 08:54 myisam_ftdump
-rwxr-xr-x  1 root   root    1750760 2010-07-30 08:54 myisamlog
-rwxr-xr-x  1 root   root    1793256 2010-07-30 08:54 myisampack
-rwxr-xr-x  1 root   root    1451816 2010-07-30 08:54 my_print_defaults
-rwxr-xr-x  1 root   root     183376 2010-07-30 08:54 mysql
-rwxr-xr-x  1 root   root     110788 2010-07-30 08:53 mysqlaccess
-rwxr-xr-x  1 root   root      38704 2010-07-30 08:54 mysqladmin
lrwxrwxrwx  1 root   root         10 2010-08-05 10:58 mysqlanalyze -> mysqlcheck
-rwxr-xr-x  1 root   root     186224 2010-07-30 08:54 mysqlbinlog
-rwxr-xr-x  1 root   root      11876 2010-07-30 08:53 mysqlbug
-rwxr-xr-x  1 root   root      35616 2010-07-30 08:54 mysqlcheck
-rwxr-xr-x  1 root   root     446080 2010-07-30 08:54 mysql_client_test
-rwxr-xr-x  1 root   root    8788592 2010-07-30 08:54 mysql_client_test_embedded
-rwxr-xr-x  1 root   root       4169 2010-07-30 08:53 mysql_convert_table_format
-rwxr-xr-x  1 root   root      23034 2010-07-30 08:53 mysqld_multi
-rwxr-xr-x  1 root   root      16561 2010-07-30 08:53 mysqld_safe
-rwxr-xr-x  1 root   root     101696 2010-07-30 08:54 mysqldump
-rwxr-xr-x  1 root   root       6602 2010-07-30 08:53 mysqldumpslow
-rwxr-xr-x  1 root   root       3245 2010-07-30 08:53 mysql_find_rows
-rwxr-xr-x  1 root   root        483 2010-07-30 08:53 mysql_fix_extensions
-rwxr-xr-x  1 root   root       5834 2010-07-30 08:53 mysql_fix_privilege_tables
-rwxr-xr-x  1 root   root      31485 2010-07-30 08:53 mysqlhotcopy
-rwxr-xr-x  1 root   root      30968 2010-07-30 08:54 mysqlimport
-rwxr-xr-x  1 root   root      14530 2010-07-30 08:53 mysql_install_db
lrwxrwxrwx  1 root   root         10 2010-08-05 10:58 mysqloptimize -> mysqlcheck
lrwxrwxrwx  1 root   root         10 2010-08-05 10:58 mysqlrepair -> mysqlcheck
-rwxr-xr-x  1 root   root      39016 2010-07-30 08:53 mysqlreport
-rwxr-xr-x  1 root   root       6586 2010-07-30 08:53 mysql_secure_installation
-rwxr-xr-x  1 root   root      16689 2010-07-30 08:53 mysql_setpermission
-rwxr-xr-x  1 root   root      29616 2010-07-30 08:54 mysqlshow
-rwxr-xr-x  1 root   root      52672 2010-07-30 08:54 mysqlslap
-rwxr-xr-x  1 root   root     229360 2010-07-30 08:54 mysqltest
-rwxr-xr-x  1 root   root    8523664 2010-07-30 08:54 mysqltest_embedded
-rwxr-xr-x  1 root   root    1425960 2010-07-30 08:54 mysql_tzinfo_to_sql
-rwxr-xr-x  1 root   root      66560 2010-07-30 08:54 mysql_upgrade
-rwxr-xr-x  1 root   root     173608 2010-07-30 08:54 mysql_waitpid
-rwxr-xr-x  1 root   root       3818 2010-07-30 08:53 mysql_zap
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 mzip -> mtools
-rwxr-xr-x  1 root   root      14944 2010-03-23 04:57 namei
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 nano -> /bin/nano
-rwxr-xr-x  1 root   root    1831936 2010-07-08 01:00 nautilus
-rwxr-xr-x  1 root   root     102240 2010-07-08 01:00 nautilus-autorun-software
-rwxr-xr-x  1 root   root     598728 2010-07-08 01:00 nautilus-connect-server
-rwxr-xr-x  1 root   root     581880 2010-07-08 01:00 nautilus-file-management-properties
-rwxr-xr-x  1 root   root      27736 2010-03-30 04:29 nautilus-sendto
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 nawk -> /etc/alternatives/nawk
-rwxr-xr-x  1 root   root      29832 2009-11-11 05:35 ncal
-rwxr-xr-x  1 root   root       5248 2010-03-07 15:25 ncurses5-config
-rwxr-xr-x  1 root   root       5259 2010-03-07 15:25 ncursesw5-config
-rwxr-xr-x  1 root   root        271 2010-02-22 21:23 neqn
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 net -> /etc/alternatives/net
-rwxr-xr-x  1 root   root      85384 2010-03-07 15:14 netkit-ftp
-rwxr-xr-x  1 root   root    6403728 2010-04-10 03:36 net.samba3
-rwxr-xr-x  1 root   root      26770 2010-06-02 15:04 net-snmp-config
lrwxrwxrwx  1 root   root         16 2010-06-26 09:59 newaliases -> ../sbin/sendmail
-rwsr-xr-x  1 root   root      32416 2010-01-27 04:09 newgrp
-rwxr-xr-x  1 root   root      31224 2010-03-05 15:59 ngettext
-rwxr-xr-x  1 root   root      39376 2010-03-05 14:41 nice
-rwxr-xr-x  1 root   root     113360 2010-03-05 14:41 nl
-rwxr-xr-x  1 root   root      40664 2010-06-18 21:43 nm
-rwxr-xr-x  1 root   root     382616 2010-04-03 11:51 nm-applet
lrwxrwxrwx  1 root   root         27 2010-06-18 15:37 nmblookup -> /etc/alternatives/nmblookup
-rwxr-xr-x  1 root   root    1141968 2010-04-10 03:36 nmblookup.samba3
-rwxr-xr-x  1 root   root     374112 2010-04-03 11:51 nm-connection-editor
-rwxr-xr-x  1 root   root      23392 2010-04-10 11:39 nm-tool
-rwxr-xr-x  1 root   root      39408 2010-03-05 14:41 nohup
-rwxr-xr-x  1 root   root       3403 2010-02-22 21:23 nroff
-rwxr-xr-x  1 root   root     120136 2010-03-23 07:00 nslookup
-rwxr-xr-x  1 root   root      19032 2010-01-18 19:11 nstat
-rwxr-xr-x  1 root   root      59432 2010-03-23 07:00 nsupdate
-rwxr-xr-x  1 root   root      27064 2010-03-07 14:25 ntfscat
-rwxr-xr-x  1 root   root      31152 2010-03-07 14:25 ntfscluster
-rwxr-xr-x  1 root   root      31176 2010-03-07 14:25 ntfscmp
-rwxr-xr-x  1 root   root      27064 2010-03-07 14:25 ntfsfix
-rwxr-xr-x  1 root   root      51760 2010-03-07 14:25 ntfsinfo
-rwxr-xr-x  1 root   root      28232 2010-03-07 14:25 ntfsls
-rwxr-xr-x  1 root   root      44208 2010-03-07 14:25 ntfsmount
-rwxr-xr-x  1 root   root     183664 2010-04-09 13:14 ntpdc
-rwxr-xr-x  1 root   root     181168 2010-04-09 13:14 ntpq
-rwxr-xr-x  1 root   root       7715 2010-04-09 13:14 ntpsweep
-rwxr-xr-x  1 root   root       2029 2010-04-09 13:14 ntptrace
lrwxrwxrwx  1 root   root         35 2010-06-21 14:59 nvidia-bug-report.sh -> /etc/alternatives/nvidia_bug_report
-rwxr-xr-x  1 root   root        257 2010-04-04 14:15 nvidia-detector
-rwxr-xr-x  1 root   root    1625968 2010-04-09 21:51 nvidia-settings
lrwxrwxrwx  1 root   root         28 2010-06-21 14:59 nvidia-smi -> /etc/alternatives/nvidia_smi
lrwxrwxrwx  1 root   root         32 2010-06-21 14:59 nvidia-xconfig -> /etc/alternatives/nvidia_xconfig
-rwxr-xr-x  1 root   root      58440 2010-03-25 19:12 oakdecode
-rwxr-xr-x  1 root   root     155952 2009-11-18 06:29 obex-data-server
-rwxr-xr-x  1 root   root     211616 2010-06-18 21:43 objcopy
-rwxr-xr-x  1 root   root     276096 2010-06-18 21:43 objdump
-rwxr-xr-x  1 root   root      20320 2010-03-13 06:40 oclock
-rwxr-xr-x  1 root   root      59952 2010-03-05 14:41 od
-rwxr-xr-x  1 root   root       8341 2009-11-18 06:29 ods-server
-rwxr-xr-x  1 root   root       6296 2010-03-07 07:14 oil-bugreport
-rwxr-xr-x  1 root   root     225832 2010-03-10 00:23 oldfind
-rwxr-xr-x  1 root   root     414384 2010-04-02 09:57 omshell
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 on_ac_power -> /sbin/on_ac_power
-rwxr-xr-x  1 root   root        387 2010-04-14 15:26 onboard
-rwxr-xr-x  1 root   root         76 2010-04-14 15:26 onboard-settings
-rwxr-xr-x  1 root   root         52 2010-06-03 16:01 ooffice
-rwxr-xr-x  1 root   root         63 2010-06-03 16:01 oofromtemplate
lrwxrwxrwx  1 root   root          7 2010-06-18 16:16 openoffice.org -> ooffice
-rwxr-xr-x  1 root   root     453248 2010-03-31 05:11 openssl
-rwxr-xr-x  1 root   root      58440 2010-03-25 19:12 opldecode
-rwxr-xr-x  1 root   root       6901 2010-07-08 01:11 orca
-rwxr-xr-x  1 root   root       3685 2010-02-11 10:06 os-prober
-rwxr-xr-x  1 root   root      10480 2010-03-27 14:58 pabrowse
-rwxr-xr-x  1 root   root      39928 2010-03-27 14:58 pacat
-rwxr-xr-x  1 root   root      10512 2010-03-27 14:58 pacmd
-rwxr-xr-x  1 root   root      43912 2010-03-27 14:58 pactl
-rwxr-xr-x  1 root   root       2314 2010-03-27 14:56 padsp
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 pager -> /etc/alternatives/pager
-rwxr-xr-x  1 root   root     128984 2010-04-11 22:13 palimpsest
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 pamon -> pacat
-rwxr-xr-x  1 root   root      19248 2010-07-08 01:19 panel-test-applets
-rwxr-xr-x  1 root   root      10536 2010-03-07 07:22 paperconf
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 paplay -> pacat
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 parec -> pacat
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 parecord -> pacat
-rwxr-xr-x  1 root   root       8704 2010-04-27 02:20 parsechangelog
-rwxr-xr-x  1 root   root      18704 2010-03-23 04:57 partx
-rwsr-xr-x  1 root   root      42856 2010-01-27 04:09 passwd
-rwxr-xr-x  1 root   root      39376 2010-03-05 14:41 paste
-rwxr-xr-x  1 root   root      14768 2010-03-27 14:58 pasuspender
-rwxr-xr-x  1 root   root     113544 2010-04-05 10:46 patch
-rwxr-xr-x  1 root   root      39360 2010-03-05 14:41 pathchk
-rwxr-xr-x  1 root   root      14632 2010-03-27 14:58 pax11publish
-rwxr-xr-x  1 root   root      10760 2010-03-10 10:38 pcimodules
-rwxr-xr-x  1 root   root      47584 2010-03-07 16:13 pcretest
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 pdb -> pdb2.6
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 pdb2.6 -> ../lib/python2.6/pdb.py
-rwxr-xr-x  1 root   root    1590696 2010-04-10 03:36 pdbedit
-rwxr-xr-x  1 root   root        738 2010-07-13 03:58 pdf2dsc
-rwxr-xr-x  1 root   root        943 2010-07-13 03:58 pdf2ps
-rwxr-xr-x  1 root   root      19040 2010-05-05 16:37 pdffonts
-rwxr-xr-x  1 root   root      31424 2010-05-05 16:37 pdfimages
-rwxr-xr-x  1 root   root      23360 2010-05-05 16:37 pdfinfo
-rwxr-xr-x  1 root   root        589 2010-07-13 03:58 pdfopt
-rwxr-xr-x  1 root   root      14848 2010-05-05 16:37 pdftoabw
-rwxr-xr-x  1 root   root      77128 2010-05-05 16:37 pdftohtml
-rwxr-xr-x  1 root   root      19104 2010-05-05 16:37 pdftoppm
-rwxr-xr-x  1 root   root      19072 2010-05-05 16:37 pdftops
-rwxr-xr-x  1 root   root      19272 2010-05-05 16:37 pdftotext
-rwxr-xr-x  1 root   root      10456 2010-01-18 19:34 peekfd
-rwxr-xr-x  1 root   root      10416 2010-04-23 18:38 perl
-rwxr-xr-x  1 root   root      10416 2010-04-23 18:38 perl5.10.1
-rwxr-xr-x  1 root   root      45160 2010-04-23 18:37 perlbug
-rwxr-xr-x  1 root   root        125 2010-04-23 18:37 perldoc
-rwxr-xr-x  1 root   root      12354 2010-04-23 18:37 perlivp
-rwxr-xr-x  1 root   root      45160 2010-04-23 18:37 perlthanks
-rwxr-xr-x  1 root   root    1447848 2010-07-30 08:54 perror
-rwxr-xr-x  1 root   root        537 2010-07-13 03:58 pf2afm
-rwxr-xr-x  1 root   root        553 2010-07-13 03:58 pfbtopfa
lrwxrwxrwx  1 root   root         10 2010-06-18 15:37 pftp -> netkit-ftp
-rwxr-xr-x  1 root   root      31392 2010-03-23 04:57 pg
-rwxr-xr-x  1 root   root     356072 2009-12-11 14:45 pgawk
-rwxr-xr-x  1 root   root      18912 2009-12-17 06:34 pgrep
-rwxr-xr-x  1 root   root     238184 2010-02-22 21:23 pic
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 pico -> /etc/alternatives/pico
-rwxr-xr-x  1 root   root       7337 2010-04-23 18:37 piconv
-rwxr-xr-x  1 root   root       2264 2010-01-20 13:05 pilconvert.py
-rwxr-xr-x  1 root   root      15316 2010-01-20 13:05 pildriver.py
-rwxr-xr-x  1 root   root       2499 2010-01-20 13:05 pilfile.py
-rwxr-xr-x  1 root   root        980 2010-01-20 13:05 pilfont.py
-rwxr-xr-x  1 root   root       2308 2010-01-20 13:05 pilprint.py
-rwxr-xr-x  1 root   root      43632 2010-03-05 14:41 pinky
-rwxr-xr-x  1 root   root      10560 2010-04-10 00:47 pkaction
-rwxr-xr-x  1 root   root      10544 2010-04-10 00:47 pkcheck
-rwsr-xr-x  1 root   root      19096 2010-04-10 00:47 pkexec
-rwxr-xr-x  1 root   root      56520 2010-03-07 16:22 pkg-config
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 pkill -> pgrep
-rwxr-xr-x  1 root   root       4531 2010-04-23 18:37 pl2pm
-rwxr-xr-x  1 root   root        146 2010-03-07 16:36 plog
-rwxr-xr-x  1 root   root      19232 2010-04-27 19:05 plymouth-log-viewer
-rwxr-xr-x  1 root   root      14680 2009-12-17 06:34 pmap
-rwxr-xr-x  1 root   root        981 2010-04-30 23:21 pm-is-supported
-rwxr-xr-x  1 root   root     628672 2010-02-16 20:42 pnm2ppa
-rwxr-xr-x  1 root   root       2338 2010-04-23 18:37 pod2html
-rwxr-xr-x  1 root   root      10255 2010-04-23 18:37 pod2latex
-rwxr-xr-x  1 root   root      21175 2010-04-23 18:37 pod2man
-rwxr-xr-x  1 root   root       9080 2010-04-23 18:37 pod2text
-rwxr-xr-x  1 root   root       3342 2010-04-23 18:37 pod2usage
-rwxr-xr-x  1 root   root       3699 2010-04-23 18:37 podchecker
-rwxr-xr-x  1 root   root       2527 2010-04-23 18:37 podselect
-rwxr-xr-x  1 root   root       2837 2010-03-07 16:36 poff
-rwxr-xr-x  1 root   root      27600 2010-03-29 09:34 pointer-capture-applet
-rwxr-xr-x  1 root   root       1625 2010-03-07 16:36 pon
lrwxrwxrwx  1 root   root         11 2010-09-01 07:47 POST -> lwp-request
-rwxr-xr-x  1 root   root       9602 2008-07-16 00:55 ppmtolss16
-rwxr-xr-x  1 root   root      72368 2010-03-05 14:41 pr
-rwxr-xr-x  1 root   root       5656 2010-03-25 03:10 precat
-rwxr-xr-x  1 root   root      43640 2010-02-22 21:23 preconv
-rwxr-xr-x  1 root   root       2987 2010-04-23 18:37 prename
-rwxr-xr-x  1 root   root       5656 2010-03-25 03:10 preunzip
-rwxr-xr-x  1 root   root       5656 2010-03-25 03:10 prezip
-rwxr-xr-x  1 root   root      10400 2010-03-25 03:10 prezip-bin
lrwxrwxrwx  1 root   root         11 2010-06-18 15:37 print -> run-mailcap
-rwxr-xr-x  1 root   root        428 2010-07-13 03:58 printafm
-rwxr-xr-x  1 root   root      35240 2010-03-05 14:41 printenv
-rwxr-xr-x  1 root   root      18656 2009-11-11 05:35 printerbanner
-rwxr-xr-x  1 root   root       5640 2010-03-25 19:12 printer-profile
-rwxr-xr-x  1 root   root      47648 2010-03-05 14:41 printf
-rwxr-xr-x  1 root   root    1076408 2010-04-10 03:36 profiles
-rwxr-xr-x  1 root   root      10544 2010-02-11 12:17 protoc
-rwxr-xr-x  1 root   root       9439 2010-04-23 18:37 prove
-rwxr-xr-x  1 root   root      14616 2010-01-18 19:34 prtstat
-rwxr-xr-x  1 root   root        786 2010-07-13 03:58 ps2ascii
-rwxr-xr-x  1 root   root       2825 2010-07-13 03:58 ps2epsi
lrwxrwxrwx  1 root   root         24 2010-07-14 07:45 ps2pdf -> /etc/alternatives/ps2pdf
-rwxr-xr-x  1 root   root        260 2010-07-13 03:58 ps2pdf12
-rwxr-xr-x  1 root   root        260 2010-07-13 03:58 ps2pdf13
-rwxr-xr-x  1 root   root        260 2010-07-13 03:58 ps2pdf14
-rwxr-xr-x  1 root   root       1130 2010-07-13 03:58 ps2pdfwr
-rwxr-xr-x  1 root   root        676 2010-07-13 03:58 ps2ps
-rwxr-xr-x  1 root   root        704 2010-07-13 03:58 ps2ps2
lrwxrwxrwx  1 root   root          8 2010-07-14 07:45 ps2txt -> ps2ascii
-rwxr-xr-x  1 root   root      53325 2010-04-23 18:37 psed
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 psfaddtable -> psfxtable
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 psfgettable -> psfxtable
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 psfstriptable -> psfxtable
-rwxr-xr-x  1 root   root      18760 2010-03-13 01:29 psfxtable
-rwxr-xr-x  1 root   root      23256 2010-01-18 19:34 pstree
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 pstree.x11 -> pstree
-rwxr-xr-x  1 root   root      36601 2010-04-23 18:37 pstruct
-rwxr-xr-x  1 root   root       2788 2010-04-23 18:37 ptar
-rwxr-xr-x  1 root   root       2514 2010-04-23 18:37 ptardiff
-rwxr-xr-x  1 root   root     137984 2010-03-05 14:41 ptx
-rwxr-xr-x  1 root   root      71712 2010-03-27 14:58 pulseaudio
-rwxr-xr-x  1 root   root       7962 2010-03-10 06:18 purple-remote
-rwxr-xr-x  1 root   root        776 2010-03-10 06:18 purple-send
-rwxr-xr-x  1 root   root        635 2010-03-10 06:18 purple-send-async
-rwxr-xr-x  1 root   root      11965 2010-03-10 06:18 purple-url-handler
-rwxr-xr-x  1 root   root      10456 2009-12-17 06:34 pwdx
-rwxr-xr-x  1 root   root       3752 2010-04-01 01:26 py3_compilefiles
-rwxr-xr-x  1 root   root      94805 2010-04-01 01:26 pycentral
-rwxr-xr-x  1 root   root       8615 2010-04-01 04:09 pyclean
-rwxr-xr-x  1 root   root      14241 2010-04-01 04:09 pycompile
-rwxr-xr-x  1 root   root       3723 2010-04-01 01:26 py_compilefiles
lrwxrwxrwx  1 root   root          8 2010-06-18 15:37 pydoc -> pydoc2.6
-rwxr-xr-x  1 root   root         79 2010-04-17 00:41 pydoc2.6
lrwxrwxrwx  1 root   root         12 2010-06-18 15:37 pygettext -> pygettext2.6
-rwxr-xr-x  1 root   root      22103 2010-04-17 00:41 pygettext2.6
-rwxr-xr-x  1 root   root        545 2010-04-15 14:06 pyhtmlizer
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 python -> python2.6
lrwxrwxrwx  1 root   root          9 2010-06-18 15:37 python2 -> python2.6
-rwxr-xr-x  1 root   root    2613296 2010-04-17 00:42 python2.6
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x  1 root   root      58472 2010-03-25 19:12 qpdldecode
-rwxr-xr-x  1 root   root      56168 2010-06-18 21:43 ranlib
-rwxr-xr-x  1 root   root      10408 2009-11-18 07:16 rarian-example
-rwxr-xr-x  1 root   root       1495 2009-11-18 07:16 rarian-sk-config
-rwxr-xr-x  1 root   root        563 2009-11-18 07:16 rarian-sk-extract
-rwxr-xr-x  1 root   root       6304 2009-11-18 07:16 rarian-sk-gen-uuid
-rwxr-xr-x  1 root   root      76560 2009-11-18 07:16 rarian-sk-get-cl
-rwxr-xr-x  1 root   root        399 2009-11-18 07:16 rarian-sk-get-content-list
-rwxr-xr-x  1 root   root        419 2009-11-18 07:16 rarian-sk-get-extended-content-list
-rwxr-xr-x  1 root   root        382 2009-11-18 07:16 rarian-sk-get-scripts
-rwxr-xr-x  1 root   root       1171 2009-11-18 07:16 rarian-sk-install
-rwxr-xr-x  1 root   root      84816 2009-11-18 07:16 rarian-sk-migrate
-rwxr-xr-x  1 root   root      72408 2009-11-18 07:16 rarian-sk-preinstall
-rwxr-xr-x  1 root   root        821 2009-11-18 07:16 rarian-sk-rebuild
-rwxr-xr-x  1 root   root       9525 2009-11-18 07:16 rarian-sk-update
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 rcp -> /etc/alternatives/rcp
-rwxr-xr-x  1 root   root     246864 2010-03-07 18:49 rdesktop
-rwxr-xr-x  1 root   root        298 2009-12-22 09:36 rdfpipe
-rwxr-xr-x  1 root   root      10408 2010-03-13 05:09 rdjpgcom
-rwxr-xr-x  1 root   root     297832 2010-06-18 21:43 readelf
-rwxr-xr-x  1 root   root     192576 2010-03-20 06:50 readom
-rwxr-xr-x  1 root   root      55320 2009-12-18 18:18 rearj
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 red -> /bin/ed
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 rename -> /etc/alternatives/rename
-rwxr-xr-x  1 root   root      10448 2010-03-23 04:57 rename.ul
-rwxr-xr-x  1 root   root      10432 2010-03-23 04:57 renice
-rwxr-xr-x  1 root   root    1438248 2010-07-30 08:54 replace
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 reset -> tset
-rwxr-xr-x  1 root   root      14632 2010-04-01 01:31 resize
-rwxr-xr-x  1 root   root    1434760 2010-07-30 08:54 resolveip
-rwxr-xr-x  1 root   root    1438856 2010-07-30 08:54 resolve_stack_dump
-rwxr-xr-x  1 root   root      10480 2010-03-23 04:57 rev
-rwxr-xr-x  1 root   root      40352 2010-04-09 21:25 rfcomm
-rwxr-xr-x  1 root   root         30 2010-03-05 16:33 rgrep
-rwxr-xr-x  1 root   root      35768 2010-06-25 21:33 rhythmbox
-rwxr-xr-x  1 root   root      28544 2010-06-25 21:33 rhythmbox-client
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 rlogin -> /etc/alternatives/rlogin
lrwxrwxrwx  1 root   root         13 2010-06-26 09:59 rmail -> ../sbin/rmail
-rwxr-xr-x  1 root   root        173 2009-12-27 05:26 routef
-rwxr-xr-x  1 root   root       1262 2009-12-27 05:26 routel
-rwxr-xr-x  1 root   root    5700040 2010-04-10 03:36 rpcclient
-rwxr-xr-x  1 root   root      88896 2010-06-14 23:58 rpcgen
-rwxr-xr-x  1 root   root      18792 2010-06-14 23:58 rpcinfo
-rwxr-xr-x  1 root   root      26888 2009-12-06 09:03 rpl8
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 rsh -> /etc/alternatives/rsh
-rwxr-xr-x  1 root   root       2613 2009-12-08 01:10 rstart
-rwxr-xr-x  1 root   root       1435 2009-12-08 01:10 rstartd
-rwxr-xr-x  1 root   root     405400 2010-03-31 02:15 rsync
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 rtstat -> lnstat
-rwxr-xr-x  1 root   root      39440 2010-03-05 14:41 runcon
lrwxrwxrwx  1 root   root         25 2010-06-18 15:37 run_erl -> ../lib/erlang/bin/run_erl
-rwxr-xr-x  1 root   root      16898 2010-01-16 11:05 run-mailcap
-rwxr-xr-x  1 root   root         57 2010-03-25 03:10 run-with-aspell
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 rview -> /etc/alternatives/rview
-rwxr-xr-x  1 root   root      53325 2010-04-23 18:37 s2p
-rwxr-xr-x  1 root   root     134744 2010-04-15 17:25 sane-find-scanner
-rwxr-xr-x  1 root   root       9760 2009-12-09 00:05 savelog
-rwxr-xr-x  1 root   root      48336 2010-04-15 17:25 scanimage
-rwxr-xr-x  1 root   root      59528 2010-05-20 03:30 scp
-rwxr-sr-x  1 root   utmp     376112 2009-11-11 05:54 screen
-rwxr-xr-x  1 root   root      10488 2010-03-13 01:29 screendump
lrwxrwxrwx  1 root   root         23 2010-07-06 10:07 screen-launcher -> /usr/bin/byobu-launcher
lrwxrwxrwx  1 root   root         21 2010-07-06 10:07 screen-profiles-status -> /usr/bin/byobu-status
-rwxr-xr-x  1 root   root      14744 2010-03-23 04:57 script
-rwxr-xr-x  1 root   root      10496 2010-03-23 04:57 scriptreplay
lrwxrwxrwx  1 root   root         16 2010-06-18 15:37 scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx  1 root   root         18 2010-06-18 15:37 scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx  1 root   root         16 2010-06-18 15:37 scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx  1 root   root         35 2010-06-18 15:37 scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         21 2010-06-18 15:37 scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx  1 root   root         20 2010-06-18 15:37 scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx  1 root   root         16 2010-06-18 15:37 scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x  1 root   root      40104 2009-11-10 22:00 sctp_darn
-rwxr-xr-x  1 root   root      18936 2009-11-10 22:00 sctp_status
-rwxr-xr-x  1 root   root      27128 2009-11-10 22:00 sctp_test
-rwxr-xr-x  1 root   root      27216 2009-11-05 17:33 sdiff
-rwxr-xr-x  1 root   root      83632 2010-04-09 21:25 sdptool
-rwxr-xr-x  1 root   root     682328 2010-04-09 20:49 seahorse
-rwxr-xr-x  1 root   root     586832 2010-04-09 20:49 seahorse-daemon
lrwxrwxrwx  1 root   root         11 2010-06-18 15:37 see -> run-mailcap
-rwxr-xr-x  1 root   root        474 2010-01-21 11:05 select-default-iwrap
-rwxr-xr-x  1 root   root       1197 2010-04-09 10:45 select-editor
-rwxr-xr-x  1 root   root       1388 2010-04-09 10:45 sensible-browser
-rwxr-xr-x  1 root   root       1109 2010-04-09 10:45 sensible-editor
-rwxr-xr-x  1 root   root        288 2010-04-09 10:45 sensible-pager
-rwxr-xr-x  1 root   root      22992 2010-02-16 04:19 sensors
-rwxr-xr-x  1 root   root      14018 2010-02-16 04:19 sensors-conf-convert
-rwxr-xr-x  1 root   root      39392 2010-03-05 14:41 seq
lrwxrwxrwx  1 root   root         17 2010-06-18 15:37 service -> /usr/sbin/service
-rwxr-xr-x  1 root   root      10496 2010-03-20 11:55 sessreg
-rwxr-xr-x  1 root   root      10944 2010-03-23 04:57 setarch
-rwxr-xr-x  1 root   root      10464 2010-03-13 01:29 setkeycodes
-rwxr-xr-x  1 root   root      10480 2010-03-13 01:29 setleds
-rwxr-xr-x  1 root   root      10448 2010-03-13 01:29 setlogcons
-rwxr-xr-x  1 root   root      10536 2010-03-13 01:29 setmetamode
-rwxr-xr-x  1 root   root      18768 2010-03-10 10:38 setpci
-rwxr-xr-x  1 root   root       6328 2010-03-23 04:57 setsid
-rwxr-xr-x  1 root   root      23112 2010-03-23 04:57 setterm
-rwxr-xr-x  1 root   root      22872 2009-12-08 01:22 setxkbmap
-rwxr-xr-x  1 root   root      92304 2010-05-20 03:30 sftp
lrwxrwxrwx  1 root   root          6 2010-06-18 15:37 sg -> newgrp
-rwxr-xr-x  1 root   root      47616 2010-03-05 14:41 sha1sum
-rwxr-xr-x  1 root   root      55816 2010-03-05 14:41 sha224sum
-rwxr-xr-x  1 root   root      55816 2010-03-05 14:41 sha256sum
-rwxr-xr-x  1 root   root      59912 2010-03-05 14:41 sha384sum
-rwxr-xr-x  1 root   root      59912 2010-03-05 14:41 sha512sum
-rwxr-xr-x  1 root   root      98728 2010-04-15 19:27 shares-admin
-rwxr-xr-x  1 root   root       7655 2010-04-23 18:37 shasum
-rwxr-xr-x  1 root   root      18744 2010-03-13 01:29 showconsolefont
-rwxr-xr-x  1 root   root      14592 2010-03-07 20:57 showfont
-rwxr-xr-x  1 root   root      14592 2010-03-13 01:29 showkey
-rwxr-xr-x  1 root   root       6328 2010-03-20 11:55 showrgb
-rwxr-xr-x  1 root   root      60120 2010-03-05 14:41 shred
-rwxr-xr-x  1 root   root      47696 2010-03-05 14:41 shuf
-rwxr-xr-x  1 root   root     127544 2010-04-29 15:22 simple-scan
-rwxr-xr-x  1 root   root      27584 2010-06-18 21:43 size
-rwxr-xr-x  1 root   root      18800 2009-12-17 06:34 skill
-rwxr-xr-x  1 root   root      14656 2009-12-17 06:34 slabtop
lrwxrwxrwx  1 root   root          3 2010-06-18 16:11 slogin -> ssh
-rwxr-xr-x  1 root   root      58472 2010-03-25 19:12 slxdecode
-rwxr-xr-x  1 root   root     115096 2010-03-07 15:41 smartdimmer
-rwxr-xr-x  1 root   root    5543336 2010-04-10 03:36 smbcacls
-rwxr-xr-x  1 root   root    5465544 2010-04-10 03:36 smbclient
-rwxr-xr-x  1 root   root    1162824 2010-04-10 03:36 smbcontrol
-rwxr-xr-x  1 root   root    5391752 2010-04-10 03:36 smbcquotas
-rwxr-xr-x  1 root   root    5502344 2010-04-10 03:36 smbget
-rwxr-xr-x  1 root   root    5391784 2010-04-10 03:36 smbpasswd
-rwxr-xr-x  1 root   root    2714840 2010-04-10 03:36 smbspool
lrwxrwxrwx  1 root   root         27 2010-06-18 16:31 smbstatus -> /etc/alternatives/smbstatus
-rwxr-xr-x  1 root   root    1137872 2010-04-10 03:36 smbstatus.samba3
-rwxr-xr-x  1 root   root       4910 2010-04-10 03:34 smbtar
-rwxr-xr-x  1 root   root    5367176 2010-04-10 03:36 smbtree
-rwxr-xr-x  1 root   root      23048 2009-12-08 01:10 smproxy
lrwxrwxrwx  1 root   root          5 2010-06-18 15:37 snice -> skill
-rwxr-xr-x  1 root   root      31256 2010-02-22 21:23 soelim
lrwxrwxrwx  1 root   root         33 2010-06-18 16:16 soffice -> ../lib/openoffice/program/soffice
lrwxrwxrwx  1 root   root         40 2010-07-29 11:16 software-center -> ../share/software-center/software-center
-rwxr-xr-x  1 root   root       4307 2010-04-15 15:02 software-properties-gtk
-rwxr-xr-x  1 root   root      93328 2010-03-05 14:41 sort
-rwxr-xr-x  1 root   root        142 2010-04-15 23:04 spd-conf
-rwxr-xr-x  1 root   root      19424 2010-04-16 02:29 spd-say
-rwxr-xr-x  1 root   root      27288 2010-03-29 10:04 speaker-test
-rwxr-xr-x  1 root   root     130512 2010-04-16 02:29 speech-dispatcher
-rwxr-xr-x  1 root   root       2369 2010-04-16 02:29 speechd-server-spawn
-rwxr-xr-x  1 root   root      17452 2010-04-23 18:37 splain
-rwxr-xr-x  1 root   root      64144 2010-03-05 14:41 split
-rwxr-xr-x  1 root   root      10432 2010-03-13 01:29 splitfont
-rwxr-xr-x  1 root   root      23096 2010-06-14 23:58 sprof
-rwxr-xr-x  1 root   root     339712 2010-05-20 03:30 ssh
-rwxr-xr-x  1 root   root     109448 2010-05-20 03:30 ssh-add
-rwxr-sr-x  1 root   ssh       92296 2010-05-20 03:30 ssh-agent
-rwxr-xr-x  1 root   root       1452 2010-05-20 03:30 ssh-argv0
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x  1 root   root       1316 2010-05-20 03:30 ssh-copy-id
-rwxr-xr-x  1 root   root     138120 2010-05-20 03:30 ssh-keygen
-rwxr-xr-x  1 root   root     191832 2010-05-20 03:30 ssh-keyscan
-rwxr-xr-x  1 root   root     101256 2010-05-20 03:30 ssh-vulnkey
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 start_embedded -> ../lib/erlang/bin/start
-rwxr-xr-x  1 root   root       1246 2010-03-27 14:56 start-pulseaudio-x11
-rwxr-xr-x  1 root   root       4481 2009-12-08 01:40 startx
-rwxr-xr-x  1 root   root      55872 2010-03-05 14:41 stat
-rwxr-xr-x  1 root   root     301968 2010-02-16 04:31 strace
-rwxr-xr-x  1 root   root       6296 2009-11-27 10:20 stream
-rwxr-xr-x  1 root   root      27584 2010-06-18 21:43 strings
-rwxr-xr-x  1 root   root     211624 2010-06-18 21:43 strip
-rwsr-xr-x  2 root   root     148024 2010-09-01 06:40 sudo
-rwsr-xr-x  2 root   root     148024 2010-09-01 06:40 sudoedit
-rwxr-xr-x  1 root   root      43544 2010-03-05 14:41 sum
-rwxr-xr-x  1 root   root       3031 2010-02-05 04:59 su-to-root
-rwxr-xr-x  1 root   root      22200 2010-04-16 07:37 synclient
-rwxr-xr-x  1 root   root      14704 2010-04-16 07:37 syndaemon
-rwxr-xr-x  1 root   root      29776 2008-07-16 00:55 syslinux
-rwxr-xr-x  1 root   root       1421 2008-07-16 00:55 syslinux2ansi
-rwxr-xr-x  1 root   root         95 2010-05-03 23:58 system-config-printer
-rwxr-xr-x  1 root   root         80 2010-05-03 23:58 system-config-printer-applet
-rwxr-xr-x  1 root   root      14664 2010-03-07 15:25 tabs
-rwxr-xr-x  1 root   root     105136 2010-03-05 14:41 tac
-rwxr-xr-x  1 root   root      60048 2010-03-05 14:41 tail
-rwxr-xr-x  1 root   root        535 2010-04-15 14:06 tap2deb
-rwxr-xr-x  1 root   root        622 2010-04-15 14:06 tap2rpm
-rwxr-xr-x  1 root   root        603 2010-04-15 14:06 tapconvert
-rwxr-xr-x  1 root   root      22478 2010-03-20 10:33 tasksel
-rwxr-xr-x  1 root   root      14592 2010-03-23 04:57 taskset
-rwxr-xr-x  1 root   root     117344 2010-02-22 21:23 tbl
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 tclsh -> /etc/alternatives/tclsh
-rwxr-xr-x  1 root   root       6264 2009-11-06 23:17 tclsh8.4
-rwxr-xr-x  1 root   root      59488 2010-04-10 03:36 tdbbackup
-rwxr-xr-x  1 root   root      35296 2010-03-05 14:41 tee
lrwxrwxrwx  1 root   root         24 2010-06-18 15:37 telnet -> /etc/alternatives/telnet
-rwxr-xr-x  1 root   root      95376 2010-03-07 15:16 telnet.netkit
-rwxr-xr-x  1 root   root      31184 2010-03-05 14:41 test
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 testparm -> /etc/alternatives/testparm
-rwxr-xr-x  1 root   root    1080528 2010-04-10 03:36 testparm.samba3
-rwxr-xr-x  1 root   root       2295 2009-11-14 05:51 tgz
-rwxr-xr-x  1 root   root      51904 2010-03-07 15:25 tic
-rwxr-xr-x  1 root   root       6152 2010-04-09 13:14 tickadj
-rwxr-xr-x  1 root   root      14928 2010-03-07 20:16 time
-rwxr-xr-x  1 root   root     115464 2010-04-15 19:27 time-admin
-rwxr-xr-x  1 root   root      10512 2009-12-17 06:34 tload
-rwxr-xr-x  1 root   root      14728 2010-03-07 15:25 toe
-rwxr-xr-x  1 root   root       1561 2010-04-29 17:08 tomboy
-rwxr-xr-x  1 root   root        570 2010-04-29 17:08 tomboy-panel
-rwxr-xr-x  1 root   root      82504 2009-12-17 06:34 top
-rwxr-xr-x  1 root   root      95272 2010-02-05 06:46 toshset
lrwxrwxrwx  1 root   root         10 2010-06-18 15:37 touch -> /bin/touch
-rwxr-xr-x  1 root   root      14760 2010-03-07 15:25 tput
-rwxr-xr-x  1 root   root      51696 2010-03-05 14:41 tr
-rwxr-xr-x  1 root   root      14624 2010-03-12 22:41 tracepath
-rwxr-xr-x  1 root   root      14672 2010-03-12 22:41 tracepath6
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 traceroute6 -> /etc/alternatives/traceroute6
-rwsr-xr-x  1 root   root      18928 2010-03-12 22:41 traceroute6.iputils
-rwxr-xr-x  1 root   root        677 2010-04-15 14:06 trial
-rwxr-xr-x  1 root   root     503760 2010-02-22 21:23 troff
-rwxr-xr-x  1 root   root      60008 2010-03-05 14:41 truncate
-rwxr-xr-x  1 root   root      89864 2010-02-09 14:38 tsclient
-rwxr-xr-x  1 root   root      18992 2010-03-07 15:25 tset
-rwxr-xr-x  1 root   root      43456 2010-03-05 14:41 tsort
-rwxr-xr-x  1 root   root      35248 2010-03-05 14:41 tty
-rwxr-xr-x  1 root   root        614 2010-04-15 14:06 twistd
-rwxr-xr-x  1 root   root       7261 2010-06-14 23:51 tzselect
-rwxr-xr-x  1 root   root      11387 2010-06-21 20:06 u1sdtool
lrwxrwxrwx  1 root   root         10 2010-06-18 15:37 ubuntu-bug -> apport-bug
-rwxr-xr-x  1 root   root       2549 2010-06-21 20:06 ubuntuone-launch
-rwxr-xr-x  1 root   root       6037 2010-06-01 20:11 ubuntu-support-status
-rwxr-xr-x  1 root   root      37925 2009-08-27 15:16 ucf
-rwxr-xr-x  1 root   root      19290 2008-05-30 16:22 ucfq
-rwxr-xr-x  1 root   root      10405 2008-05-30 16:22 ucfr
-rwxr-xr-x  1 root   root      18736 2010-01-12 02:31 ucs2any
-rwxr-xr-x  1 root   root      44832 2010-06-08 18:27 udisks
-rwxr-xr-x  1 root   root      14600 2009-11-11 05:35 ul
-rwxr-xr-x  1 root   root     171496 2010-04-15 17:25 umax_pp
-rwxr-xr-x  1 root   root      19931 2010-04-30 01:02 unattended-upgrade
lrwxrwxrwx  1 root   root         18 2010-06-18 16:18 unattended-upgrades -> unattended-upgrade
-rwxr-xr-x  1 root   root      39400 2010-03-05 14:41 unexpand
-rwxr-xr-x  1 root   root        530 2010-03-13 01:29 unicode_stop
-rwxr-xr-x  1 root   root      43536 2010-03-05 14:41 uniq
-rwxr-xr-x  1 root   root      35232 2010-03-05 14:41 unlink
lrwxrwxrwx  1 root   root          4 2010-06-18 15:37 unlzma -> lzma
-rwxr-xr-x  1 root   root         50 2010-06-03 16:01 unopkg
-rwxr-xr-x  1 root   root      10416 2010-03-23 04:57 unshare
-rwxr-xr-x  1 root   root     154376 2010-03-07 20:33 unzip
-rwxr-xr-x  1 root   root      72376 2010-03-07 20:33 unzipsfx
-rwxr-xr-x  1 root   root      37191 2010-06-29 03:40 update-alternatives
lrwxrwxrwx  1 root   root         26 2010-06-18 15:37 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x  1 root   root      39680 2010-03-24 23:35 updatedb.mlocate
-rwxr-xr-x  1 root   root      19040 2010-04-09 21:54 update-desktop-database
-rwxr-xr-x  1 root   root       5297 2010-03-31 04:16 update-gconf-defaults
-rwxr-xr-x  1 root   root       4380 2010-06-01 20:05 update-manager
-rwxr-xr-x  1 root   root     122496 2010-02-05 04:59 update-menus
-rwxr-xr-x  1 root   root        672 2010-04-17 12:18 update-mime-database
-rwxr-xr-x  1 root   root      48112 2010-04-17 12:18 update-mime-database.real
-rwxr-xr-x  1 root   root      70056 2010-04-14 06:59 update-notifier
-rwxr-xr-x  1 root   root       3331 2010-03-10 10:38 update-pciids
-rwxr-xr-x  1 root   root       6165 2010-01-18 18:56 update-perl-sax-parsers
-rwxr-xr-x  1 root   root      23152 2010-03-05 21:20 upower
-rwxr-xr-x  1 root   root       6264 2009-12-17 06:34 uptime
-rwxr-xr-x  1 root   root       3089 2010-04-14 01:53 usb-creator-gtk
-rwxr-xr-x  1 root   root       4202 2009-11-07 04:26 usb-devices
-rwxr-xr-x  1 root   root       6320 2010-03-25 19:12 usb_printerid
-rwxr-xr-x  1 root   root      39392 2010-03-05 14:41 users
-rwxr-xr-x  1 root   root     141248 2010-04-15 19:27 users-admin
-rwxr-xr-x  1 root   root       6336 2010-03-23 04:57 uuidgen
-rwxr-xr-x  1 root   root       3674 2010-04-01 01:31 uxterm
-rwxr-xr-x  1 root   root       2220 2009-11-14 05:51 uz
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 vboxheadless -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 VBoxHeadless -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 vboxmanage -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 VBoxManage -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 vboxsdl -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 VBoxSDL -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 vboxwebsrv -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         20 2010-06-18 15:37 vi -> /etc/alternatives/vi
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 view -> /etc/alternatives/view
-rwxr-xr-x  1 root   root      23872 2010-03-23 07:28 viewres
-rwxr-xr-x  1 root   root     754744 2010-04-16 23:33 vim.tiny
-rwxr-xr-x  1 root   root     312208 2010-06-25 15:06 vinagre
-rwxr-xr-x  1 root   root      10560 2010-04-09 18:02 vino-passwd
-rwxr-xr-x  1 root   root      61336 2010-04-09 18:02 vino-preferences
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 virtualbox -> ../share/virtualbox/VBox.sh
lrwxrwxrwx  1 root   root         27 2010-06-19 10:58 VirtualBox -> ../share/virtualbox/VBox.sh
-rwxr-xr-x  1 root   root       6264 2010-04-23 01:14 vmmouse_detect
-rwxr-xr-x  1 root   root      22832 2009-12-17 06:34 vmstat
-rwxr-xr-x  1 root   root       6328 2009-11-10 19:07 volname
lrwxrwxrwx  1 root   root         19 2010-06-18 15:37 w -> /etc/alternatives/w
-rwxr-xr-x  1 root   root    1287264 2010-08-04 19:30 w3m
-rwxr-xr-x  1 root   root       1132 2010-08-04 19:30 w3mman
-rwxr-sr-x  1 root   tty       14824 2010-03-23 04:57 wall
-rwxr-xr-x  1 root   root      15320 2009-12-17 06:34 watch
-rwxr-xr-x  1 root   root      47696 2010-03-05 14:41 wc
-rwxr-xr-x  1 root   root        326 2010-07-13 03:58 wftopfa
-rwxr-xr-x  1 root   root     353336 2010-09-02 02:13 wget
-rwxr-xr-x  1 root   root     187544 2010-03-02 21:31 whatis
-rwxr-xr-x  1 root   root      15096 2010-03-23 04:57 whereis
lrwxrwxrwx  1 root   root         10 2010-06-18 15:37 which -> /bin/which
-rwxr-xr-x  1 root   root      27240 2010-02-24 08:33 whiptail
-rwxr-xr-x  1 root   root      47712 2010-03-05 14:41 who
-rwxr-xr-x  1 root   root      35248 2010-03-05 14:41 whoami
-rwxr-xr-x  1 root   root      54448 2010-03-20 16:08 whois
lrwxrwxrwx  1 root   root         22 2010-06-18 15:37 wish -> /etc/alternatives/wish
-rwxr-xr-x  1 root   root       6288 2009-11-06 23:34 wish8.4
-rwxr-xr-x  1 root   root        210 2009-11-10 21:59 withsctp
-rwxr-xr-x  1 root   root     401984 2010-03-20 06:50 wodim
-rwxr-xr-x  1 root   root      10400 2010-03-25 03:10 word-list-compress
-rwxr-xr-x  1 root   root      27352 2010-03-07 20:54 wpa_passphrase
-rwxr-xr-x  1 root   root      14672 2009-12-17 06:34 w.procps
lrwxrwxrwx  1 root   root         23 2010-06-18 15:37 write -> /etc/alternatives/write
-rwxr-xr-x  1 root   root      10432 2010-03-13 05:09 wrjpgcom
lrwxrwxrwx  1 root   root         29 2010-06-18 15:37 www-browser -> /etc/alternatives/www-browser
-rwsr-sr-x  1 root   root      10520 2010-04-09 12:07 X
lrwxrwxrwx  1 root   root          1 2010-06-18 15:37 X11 -> .
-rwxr-xr-x  1 root   root     137568 2010-03-13 06:40 x11perf
-rwxr-xr-x  1 root   root       2703 2010-03-13 06:40 x11perfcomp
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 x86_64 -> setarch
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 x86_64-linux-gnu-cpp -> cpp-4.4
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 x86_64-linux-gnu-cpp-4.4 -> cpp-4.4
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 x86_64-linux-gnu-gcc -> gcc-4.4
lrwxrwxrwx  1 root   root          7 2010-06-18 15:37 x86_64-linux-gnu-gcc-4.4 -> gcc-4.4
-rwxr-xr-x  1 root   root      43600 2010-03-10 00:23 xargs
-rwxr-xr-x  1 root   root      40280 2009-12-08 01:36 xauth
-rwxr-xr-x  1 root   root      20760 2010-03-13 06:40 xbiff
-rwxr-xr-x  1 root   root      97488 2010-02-17 13:27 xbrlapi
-rwxr-xr-x  1 root   root      32256 2010-03-13 06:40 xcalc
-rwxr-xr-x  1 root   root      19208 2010-03-13 06:40 xclipboard
-rwxr-xr-x  1 root   root      42624 2010-03-13 06:40 xclock
-rwxr-xr-x  1 root   root      31712 2010-03-20 11:55 xcmsdb
-rwxr-xr-x  1 root   root      19888 2010-03-13 06:40 xconsole
-rwxr-xr-x  1 root   root      14728 2010-03-13 06:40 xcursorgen
-rwxr-xr-x  1 root   root      14944 2010-03-13 06:40 xcutsel
-rwxr-xr-x  1 root   root      14806 2010-03-12 18:54 xdg-desktop-icon
-rwxr-xr-x  1 root   root      39267 2010-03-12 18:54 xdg-desktop-menu
-rwxr-xr-x  1 root   root      17738 2010-03-12 18:54 xdg-email
-rwxr-xr-x  1 root   root      24129 2010-03-12 18:54 xdg-icon-resource
-rwxr-xr-x  1 root   root      28264 2010-03-12 18:54 xdg-mime
-rwxr-xr-x  1 root   root      10229 2010-03-12 18:54 xdg-open
-rwxr-xr-x  1 root   root      19319 2010-03-12 18:54 xdg-screensaver
-rwxr-xr-x  1 root   root        234 2010-04-17 08:06 xdg-user-dir
-rwxr-xr-x  1 root   root      19184 2010-01-26 04:22 xdg-user-dirs-gtk-update
-rwxr-xr-x  1 root   root      18872 2010-04-17 08:06 xdg-user-dirs-update
-rwxr-xr-x  1 root   root      92360 2010-03-13 06:40 xditview
-rwxr-xr-x  1 root   root      32104 2010-03-23 07:28 xdpyinfo
-rwxr-xr-x  1 root   root      10384 2010-03-23 07:28 xdriinfo
-rwxr-xr-x  1 root   root     612560 2010-03-13 06:40 xedit
-rwxr-xr-x  1 root   root      23056 2010-03-23 07:28 xev
-rwxr-xr-x  1 root   root      20416 2010-03-13 06:40 xeyes
-rwxr-xr-x  1 root   root      24768 2010-03-23 07:28 xfd
-rwxr-xr-x  1 root   root      37160 2010-03-23 07:28 xfontsel
-rwxr-xr-x  1 root   root      10416 2010-03-07 20:57 xfsinfo
-rwxr-xr-x  1 root   root      10440 2010-03-20 11:55 xgamma
-rwxr-xr-x  1 root   root      64480 2010-03-13 06:40 xgc
-rwxr-xr-x  1 root   root      14720 2010-03-20 11:55 xhost
-rwxr-xr-x  1 root   root      18960 2009-12-08 01:40 xinit
-rwxr-xr-x  1 root   root      40136 2010-04-16 03:10 xinput
-rwxr-xr-x  1 root   root      14560 2009-12-08 01:22 xkbbell
-rwxr-xr-x  1 root   root     201272 2009-12-08 01:22 xkbcomp
-rwxr-xr-x  1 root   root      35296 2009-12-08 01:22 xkbevd
-rwxr-xr-x  1 root   root     101096 2009-12-08 01:22 xkbprint
-rwxr-xr-x  1 root   root      23800 2009-12-08 01:22 xkbvleds
-rwxr-xr-x  1 root   root      19704 2009-12-08 01:22 xkbwatch
-rwxr-xr-x  1 root   root      14495 2010-03-20 11:55 xkeystone
-rwxr-xr-x  1 root   root      14752 2010-03-23 07:28 xkill
-rwxr-xr-x  1 root   root      15456 2010-03-13 06:40 xload
-rwxr-xr-x  1 root   root      19824 2010-03-13 06:40 xlogo
-rwxr-xr-x  1 root   root      10448 2010-03-23 07:28 xlsatoms
-rwxr-xr-x  1 root   root      10496 2010-03-23 07:28 xlsclients
-rwxr-xr-x  1 root   root      23016 2010-03-23 07:28 xlsfonts
-rwxr-xr-x  1 root   root      37680 2010-03-13 06:40 xmag
-rwxr-xr-x  1 root   root      59512 2010-03-13 06:40 xman
-rwxr-xr-x  1 root   root      19728 2010-03-23 07:28 xmessage
-rwxr-xr-x  1 root   root       7204 2010-04-19 16:26 xml2po
-rwxr-xr-x  1 root   root      18776 2009-12-16 15:54 xmlcatalog
-rwxr-xr-x  1 root   root      61696 2009-12-16 15:54 xmllint
-rwxr-xr-x  1 root   root      31536 2010-03-20 11:55 xmodmap
-rwxr-xr-x  1 root   root      10672 2010-03-13 06:40 xmore
-rwxr-xr-x  1 root   root    1901280 2010-06-16 19:39 Xorg
-rwxr-xr-x  1 root   root       4961 2010-01-18 18:58 xpath
lrwxrwxrwx  1 root   root         33 2010-09-09 07:38 xpcshell-1.9.2 -> ../lib/xulrunner-1.9.2.9/xpcshell
-rwxr-xr-x  1 root   root      37760 2010-03-23 07:28 xprop
-rwxr-xr-x  1 root   root      58472 2010-03-25 19:12 xqxdecode
-rwxr-xr-x  1 root   root      47736 2010-03-20 11:55 xrandr
-rwxr-xr-x  1 root   root      27200 2010-03-20 11:55 xrdb
-rwxr-xr-x  1 root   root      10744 2010-03-20 11:55 xrefresh
-rwxr-xr-x  1 root   root     231560 2010-04-16 01:10 xscreensaver
-rwxr-xr-x  1 root   root      22928 2010-04-16 01:10 xscreensaver-command
-rwxr-xr-x  1 root   root     198472 2010-04-16 01:10 xscreensaver-demo
-rwxr-xr-x  1 root   root     123504 2010-04-16 01:10 xscreensaver-getimage
-rwxr-xr-x  1 root   root      16299 2010-04-16 01:09 xscreensaver-getimage-file
-rwxr-xr-x  1 root   root       5044 2010-04-16 01:09 xscreensaver-getimage-video
-rwxr-xr-x  1 root   root      22864 2010-04-16 01:10 xscreensaver-gl-helper
-rwxr-xr-x  1 root   root      26805 2010-04-16 01:09 xscreensaver-text
lrwxrwxrwx  1 root   root         35 2010-06-18 15:37 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x  1 root   root      31304 2010-03-20 11:55 xset
-rwxr-xr-x  1 root   root      10432 2010-03-20 11:55 xsetmode
-rwxr-xr-x  1 root   root      10440 2010-03-20 11:55 xsetpointer
-rwxr-xr-x  1 root   root      14696 2010-03-20 11:55 xsetroot
-rwxr-xr-x  1 root   root      38560 2010-04-23 06:59 xsetwacom
-rwxr-xr-x  1 root   root      23008 2010-01-19 23:32 xsltproc
-rwxr-xr-x  1 root   root      85600 2009-12-08 01:10 xsm
-rwxr-xr-x  1 root   root      15240 2010-03-20 11:55 xstdcmap
-rwxr-xr-x  1 root   root       4093 2010-04-23 18:37 xsubpp
-rwxr-sr-x  1 root   utmp     418176 2010-04-01 01:31 xterm
lrwxrwxrwx  1 root   root         37 2010-06-18 15:37 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
lrwxrwxrwx  1 root   root         27 2010-09-09 07:39 xulrunner -> /etc/alternatives/xulrunner
lrwxrwxrwx  1 root   root         34 2010-09-09 07:38 xulrunner-1.9.2 -> ../lib/xulrunner-1.9.2.9/xulrunner
-rwxr-xr-x  1 root   root      32728 2010-03-20 11:55 xvidtune
-rwxr-xr-x  1 root   root      14552 2010-03-23 07:28 xvinfo
-rwxr-xr-x  1 root   root      27096 2010-03-13 06:40 xwd
lrwxrwxrwx  1 root   root         34 2010-06-18 15:37 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x  1 root   root      31192 2010-03-23 07:28 xwininfo
-rwxr-xr-x  1 root   root      27048 2010-03-13 06:40 xwud
lrwxrwxrwx  1 root   root         31 2010-06-18 15:37 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x  1 root   root      14736 2010-04-16 23:36 xxd
-rwxr-xr-x  1 root   root     315344 2010-04-17 11:23 yelp
-rwxr-xr-x  1 root   root      35232 2010-03-05 14:41 yes
-rwxr-xr-x  1 root   root      14608 2010-06-14 23:58 zdump
-rwxr-xr-x  1 root   root      77976 2010-03-29 22:03 zenity
-rwxr-xr-x  1 root   root     188312 2010-02-16 04:38 zip
-rwxr-xr-x  1 root   root      86112 2010-02-16 04:38 zipcloak
-rwxr-xr-x  1 root   root       2953 2010-03-07 20:33 zipgrep
-rwxr-xr-x  1 root   root     154376 2010-03-07 20:33 zipinfo
-rwxr-xr-x  1 root   root      81688 2010-02-16 04:38 zipnote
-rwxr-xr-x  1 root   root      81688 2010-02-16 04:38 zipsplit
-rwxr-xr-x  1 root   root      62568 2010-03-25 19:12 zjsdecode
-rwxr-xr-x  1 root   root     171576 2010-03-02 21:31 zsoelim

```

HTH.

---

### Post by sikander3786 on 2010-09-14
How did you change the permissions? Can you post the exact command?

There are already many post on this issue. See if one helps you.

[http://www.google.com.pk/search?hl=en&q=+site:ubuntuforums.org+change+permission+/usr+ubuntu&sa=X&ei=dCSPTILtK46iuQPD7LDfCw&ved=0CCEQrQIwAQ](http://www.google.com.pk/search?hl=en&q=+site:ubuntuforums.org+change+permission+/usr+ubuntu&sa=X&ei=dCSPTILtK46iuQPD7LDfCw&ved=0CCEQrQIwAQ)

---

### Post by anntzer on 2010-09-14
Well, sudo chmod root /usr/bin/*. That's pretty straightforward.
Actually I had just installed miktex-tools (trying to have an up-to-date tex installation...), which put the binaries in /usr/bin with a different ownership than root. Naively believing that all /usr/bin was owned by root, I typed that bad command...
And now startx gives me: User not allowed to run the X server, aborting. sudo startx still works, though. Any idea of what happened?
--
I have to use (sudo) startx because directly logging in from the login graphical prompt doesn't work anymore...

---

### Post by sikander3786 on 2010-09-14
I am unable to figure it out because nearly 99% files in my /usr/bin are owned by root.

```


-rwxr-xr-x 1 root   root    2288240 2010-04-16 19:06 /usr/bin/python2.6
lrwxrwxrwx 1 root   root         29 2010-08-29 12:53 /usr/bin/pyversions -> ../share/python/pyversions.py
-rwxr-xr-x 1 root   root    3969636 2010-01-05 12:14 /usr/bin/qcad
-rwxr-xr-x 1 root   root      53492 2010-03-25 13:12 /usr/bin/qpdldecode
-rwxr-xr-x 1 root   root         43 2010-04-24 07:22 /usr/bin/qvlc
-rwxr-xr-x 1 root   root      50908 2010-04-19 07:00 /usr/bin/ranlib
-rwxr-xr-x 1 root   root       5516 2009-11-18 00:25 /usr/bin/rarian-example
-rwxr-xr-x 1 root   root       1495 2009-11-18 00:25 /usr/bin/rarian-sk-config
-rwxr-xr-x 1 root   root        563 2009-11-18 00:25 /usr/bin/rarian-sk-extract
-rwxr-xr-x 1 root   root       5512 2009-11-18 00:25 /usr/bin/rarian-sk-gen-uuid
-rwxr-xr-x 1 root   root      71464 2009-11-18 00:25 /usr/bin/rarian-sk-get-cl
-rwxr-xr-x 1 root   root        399 2009-11-18 00:25 /usr/bin/rarian-sk-get-content-list
-rwxr-xr-x 1 root   root        419 2009-11-18 00:25 /usr/bin/rarian-sk-get-extended-content-list
-rwxr-xr-x 1 root   root        382 2009-11-18 00:25 /usr/bin/rarian-sk-get-scripts
-rwxr-xr-x 1 root   root       1171 2009-11-18 00:25 /usr/bin/rarian-sk-install
-rwxr-xr-x 1 root   root      79688 2009-11-18 00:25 /usr/bin/rarian-sk-migrate
-rwxr-xr-x 1 root   root      67340 2009-11-18 00:25 /usr/bin/rarian-sk-preinstall
-rwxr-xr-x 1 root   root        821 2009-11-18 00:25 /usr/bin/rarian-sk-rebuild
-rwxr-xr-x 1 root   root       9525 2009-11-18 00:25 /usr/bin/rarian-sk-update
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/rcp -> /etc/alternatives/rcp
-rwxr-xr-x 1 root   root     216212 2010-03-07 09:31 /usr/bin/rdesktop
-rwxr-xr-x 1 root   root        298 2009-12-22 03:41 /usr/bin/rdfpipe
-rwxr-xr-x 1 root   root     278444 2010-04-19 07:00 /usr/bin/readelf
-rwxr-xr-x 1 root   root     172688 2010-03-20 00:43 /usr/bin/readom
lrwxrwxrwx 1 root   root          7 2010-08-29 12:53 /usr/bin/red -> /bin/ed
lrwxrwxrwx 1 root   root         24 2010-08-29 12:53 /usr/bin/rename -> /etc/alternatives/rename
-rwxr-xr-x 1 root   root       5532 2010-03-22 22:51 /usr/bin/rename.ul
-rwxr-xr-x 1 root   root       9620 2010-03-22 22:51 /usr/bin/renice
lrwxrwxrwx 1 root   root          4 2010-08-29 12:53 /usr/bin/reset -> tset
-rwxr-xr-x 1 root   root       9676 2010-03-31 14:47 /usr/bin/resize
-rwxr-xr-x 1 root   root      13864 2010-03-12 12:05 /usr/bin/resizecons
-rwxr-xr-x 1 root   root       5544 2010-03-22 22:51 /usr/bin/rev
-rwxr-xr-x 1 root   root      30800 2010-04-09 15:35 /usr/bin/rfcomm
-rwxr-xr-x 1 root   root         30 2010-03-05 09:47 /usr/bin/rgrep
-rwxr-xr-x 1 root   root      30476 2010-04-16 14:51 /usr/bin/rhythmbox
-rwxr-xr-x 1 root   root      22916 2010-04-16 14:51 /usr/bin/rhythmbox-client
lrwxrwxrwx 1 root   root         24 2010-08-29 12:53 /usr/bin/rlogin -> /etc/alternatives/rlogin
-rwxr-xr-x 1 root   root        173 2009-12-26 23:26 /usr/bin/routef
-rwxr-xr-x 1 root   root       1262 2009-12-26 23:26 /usr/bin/routel
-rwxr-xr-x 1 root   root    5388288 2010-04-09 20:29 /usr/bin/rpcclient
-rwxr-xr-x 1 root   root      79684 2010-04-22 22:15 /usr/bin/rpcgen
-rwxr-xr-x 1 root   root      13800 2010-04-22 22:15 /usr/bin/rpcinfo
-rwxr-xr-x 1 root   root      21944 2009-12-06 02:41 /usr/bin/rpl8
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/rsh -> /etc/alternatives/rsh
-rwxr-xr-x 1 root   root       2613 2009-12-07 19:01 /usr/bin/rstart
-rwxr-xr-x 1 root   root       1435 2009-12-07 19:01 /usr/bin/rstartd
-rwxr-xr-x 1 root   root     370328 2010-03-30 14:02 /usr/bin/rsync
lrwxrwxrwx 1 root   root          6 2010-08-29 12:53 /usr/bin/rtstat -> lnstat
-rwxr-xr-x 1 root   root      34364 2010-03-05 08:29 /usr/bin/runcon
lrwxrwxrwx 1 root   root         25 2010-08-29 12:53 /usr/bin/run_erl -> ../lib/erlang/bin/run_erl
-rwxr-xr-x 1 root   root      16898 2010-01-16 05:05 /usr/bin/run-mailcap
-rwxr-xr-x 1 root   root         57 2010-03-24 21:08 /usr/bin/run-with-aspell
lrwxrwxrwx 1 root   root         23 2010-09-01 12:31 /usr/bin/rview -> /etc/alternatives/rview
-rwxr-xr-x 1 root   root         42 2010-04-24 07:22 /usr/bin/rvlc
-rwxr-xr-x 1 root   root      53325 2010-04-23 13:22 /usr/bin/s2p
-rwxr-xr-x 1 root   root     129208 2010-04-15 07:24 /usr/bin/sane-find-scanner
-rwxr-xr-x 1 root   root       9760 2009-12-08 18:00 /usr/bin/savelog
-rwxr-xr-x 1 root   root      42940 2010-04-15 07:24 /usr/bin/scanimage
-rwxr-xr-x 1 root   root      50616 2010-03-08 20:36 /usr/bin/scp
-rwxr-sr-x 1 root   utmp     340604 2009-11-10 23:06 /usr/bin/screen
-rwxr-xr-x 1 root   root       9648 2010-03-12 12:05 /usr/bin/screendump
lrwxrwxrwx 1 root   root         23 2010-08-29 12:53 /usr/bin/screen-launcher -> /usr/bin/byobu-launcher
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/screen-profiles-status -> /usr/bin/byobu-status
-rwxr-xr-x 1 root   root      13824 2010-03-22 22:51 /usr/bin/script
-rwxr-xr-x 1 root   root       9656 2010-03-22 22:51 /usr/bin/scriptreplay
lrwxrwxrwx 1 root   root         16 2010-08-29 12:53 /usr/bin/scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx 1 root   root         17 2010-08-29 12:53 /usr/bin/scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx 1 root   root         18 2010-08-29 12:53 /usr/bin/scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx 1 root   root         16 2010-08-29 12:53 /usr/bin/scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx 1 root   root         26 2010-08-29 12:53 /usr/bin/scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx 1 root   root         35 2010-08-29 12:53 /usr/bin/scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         21 2010-08-29 12:53 /usr/bin/scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx 1 root   root         17 2010-08-29 12:53 /usr/bin/scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx 1 root   root         20 2010-08-29 12:53 /usr/bin/scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx 1 root   root         17 2010-08-29 12:53 /usr/bin/scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx 1 root   root         17 2010-08-29 12:53 /usr/bin/scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx 1 root   root         16 2010-08-29 12:53 /usr/bin/scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x 1 root   root      38820 2009-11-10 14:46 /usr/bin/sctp_darn
-rwxr-xr-x 1 root   root      18024 2009-11-10 14:46 /usr/bin/sctp_status
-rwxr-xr-x 1 root   root      26216 2009-11-10 14:46 /usr/bin/sctp_test
-rwxr-xr-x 1 root   root      22136 2009-11-05 11:31 /usr/bin/sdiff
-rwxr-xr-x 1 root   root      75112 2010-04-09 15:35 /usr/bin/sdptool
-rwxr-xr-x 1 root   root     620152 2010-04-09 15:08 /usr/bin/seahorse
-rwxr-xr-x 1 root   root     529316 2010-04-09 15:08 /usr/bin/seahorse-daemon
lrwxrwxrwx 1 root   root         11 2010-08-29 12:53 /usr/bin/see -> run-mailcap
-rwxr-xr-x 1 root   root        474 2010-01-21 05:05 /usr/bin/select-default-iwrap
-rwxr-xr-x 1 root   root       1197 2010-04-09 05:45 /usr/bin/select-editor
-rwxr-xr-x 1 root   root       1388 2010-04-09 05:45 /usr/bin/sensible-browser
-rwxr-xr-x 1 root   root       1109 2010-04-09 05:45 /usr/bin/sensible-editor
-rwxr-xr-x 1 root   root        288 2010-04-09 05:45 /usr/bin/sensible-pager
-rwxr-xr-x 1 root   root      17988 2010-02-15 22:17 /usr/bin/sensors
-rwxr-xr-x 1 root   root      14018 2010-02-15 22:17 /usr/bin/sensors-conf-convert
-rwxr-xr-x 1 root   root      34336 2010-03-05 08:29 /usr/bin/seq
lrwxrwxrwx 1 root   root         17 2010-08-29 12:53 /usr/bin/service -> /usr/sbin/service
-rwxr-xr-x 1 root   root       9652 2010-03-20 03:51 /usr/bin/sessreg
-rwxr-xr-x 1 root   root       9904 2010-03-22 22:51 /usr/bin/setarch
-rwxr-xr-x 1 root   root       9636 2010-03-12 12:05 /usr/bin/setkeycodes
-rwxr-xr-x 1 root   root       9684 2010-03-12 12:05 /usr/bin/setleds
-rwxr-xr-x 1 root   root       5532 2010-03-12 12:05 /usr/bin/setlogcons
-rwxr-xr-x 1 root   root       5604 2010-03-12 12:05 /usr/bin/setmetamode
-rwxr-xr-x 1 root   root      13788 2010-03-10 03:08 /usr/bin/setpci
-rwxr-xr-x 1 root   root       5520 2010-03-22 22:51 /usr/bin/setsid
-rwxr-xr-x 1 root   root      22232 2010-03-22 22:51 /usr/bin/setterm
-rwxr-xr-x 1 root   root      21988 2009-12-07 19:04 /usr/bin/setxkbmap
-rwxr-xr-x 1 root   root      87488 2010-03-08 20:36 /usr/bin/sftp
lrwxrwxrwx 1 root   root          6 2010-08-29 12:53 /usr/bin/sg -> newgrp
-rwxr-xr-x 1 root   root      42604 2010-03-05 08:29 /usr/bin/sha1sum
-rwxr-xr-x 1 root   root      46704 2010-03-05 08:29 /usr/bin/sha224sum
-rwxr-xr-x 1 root   root      46704 2010-03-05 08:29 /usr/bin/sha256sum
-rwxr-xr-x 1 root   root     104048 2010-03-05 08:29 /usr/bin/sha384sum
-rwxr-xr-x 1 root   root     104048 2010-03-05 08:29 /usr/bin/sha512sum
-rwxr-xr-x 1 root   root      82488 2010-04-15 10:15 /usr/bin/shares-admin
-rwxr-xr-x 1 root   root       7655 2010-04-23 13:22 /usr/bin/shasum
-rwxr-xr-x 1 root   root      13780 2010-03-12 12:05 /usr/bin/showconsolefont
-rwxr-xr-x 1 root   root      13760 2010-03-07 11:28 /usr/bin/showfont
-rwxr-xr-x 1 root   root       9652 2010-03-12 12:05 /usr/bin/showkey
-rwxr-xr-x 1 root   root       5520 2010-03-20 03:51 /usr/bin/showrgb
-rwxr-xr-x 1 root   root      55000 2010-03-05 08:29 /usr/bin/shred
-rwxr-xr-x 1 root   root      38548 2010-03-05 08:29 /usr/bin/shuf
-rwxr-xr-x 1 root   root      45054 2009-03-10 01:02 /usr/bin/simple-ccsm
-rwxr-xr-x 1 root   root     109136 2010-04-16 12:16 /usr/bin/simple-scan
-rwxr-xr-x 1 root   root      22320 2010-04-19 07:00 /usr/bin/size
-rwxr-xr-x 1 root   root      13804 2009-12-17 00:34 /usr/bin/skill
-rwxr-xr-x 1 root   root      13780 2009-12-17 00:34 /usr/bin/slabtop
lrwxrwxrwx 1 root   root          3 2010-08-29 12:53 /usr/bin/slogin -> ssh
-rwxr-xr-x 1 root   root      53492 2010-03-25 13:12 /usr/bin/slxdecode
-rwxr-xr-x 1 root   root      88756 2010-03-07 08:37 /usr/bin/smartdimmer
-rwxr-xr-x 1 root   root    5242336 2010-04-09 20:29 /usr/bin/smbcacls
-rwxr-xr-x 1 root   root    5168640 2010-04-09 20:29 /usr/bin/smbclient
-rwxr-xr-x 1 root   root    1030736 2010-04-09 20:28 /usr/bin/smbcontrol
-rwxr-xr-x 1 root   root    5090784 2010-04-09 20:29 /usr/bin/smbcquotas
-rwxr-xr-x 1 root   root    5197276 2010-04-09 20:29 /usr/bin/smbget
-rwxr-xr-x 1 root   root    5094880 2010-04-09 20:29 /usr/bin/smbpasswd
-rwxr-xr-x 1 root   root    2484556 2010-04-09 20:29 /usr/bin/smbspool
lrwxrwxrwx 1 root   root         27 2010-09-09 21:19 /usr/bin/smbstatus -> /etc/alternatives/smbstatus
-rwxr-xr-x 1 root   root    1010008 2010-04-09 20:28 /usr/bin/smbstatus.samba3
-rwxr-xr-x 1 root   root       4910 2010-04-09 20:27 /usr/bin/smbtar
-rwxr-xr-x 1 root   root    5070300 2010-04-09 20:29 /usr/bin/smbtree
-rwxr-xr-x 1 root   root      17976 2009-12-07 19:01 /usr/bin/smproxy
lrwxrwxrwx 1 root   root          5 2010-08-29 12:53 /usr/bin/snice -> skill
-rwxr-xr-x 1 root   root      30344 2010-02-22 15:21 /usr/bin/soelim
lrwxrwxrwx 1 root   root         33 2010-08-29 12:53 /usr/bin/soffice -> ../lib/openoffice/program/soffice
lrwxrwxrwx 1 root   root         40 2010-08-29 12:53 /usr/bin/software-center -> ../share/software-center/software-center
-rwxr-xr-x 1 root   root       4307 2010-04-15 10:02 /usr/bin/software-properties-gtk
-rwxr-xr-x 1 root   root      79820 2010-03-05 08:29 /usr/bin/sort
-rwxr-xr-x 1 root   root        142 2010-04-15 18:04 /usr/bin/spd-conf
-rwxr-xr-x 1 root   root      14144 2010-04-15 18:05 /usr/bin/spd-say
-rwxr-xr-x 1 root   root      22160 2010-03-29 04:02 /usr/bin/speaker-test
-rwxr-xr-x 1 root   root     116764 2010-04-15 18:05 /usr/bin/speech-dispatcher
-rwxr-xr-x 1 root   root       2369 2010-04-15 18:04 /usr/bin/speechd-server-spawn
-rwxr-xr-x 1 root   root      17452 2010-04-23 13:22 /usr/bin/splain
-rwxr-xr-x 1 root   root      54964 2010-03-05 08:29 /usr/bin/split
-rwxr-xr-x 1 root   root       5524 2010-03-12 12:05 /usr/bin/splitfont
-rwxr-xr-x 1 root   root      22076 2010-04-22 22:15 /usr/bin/sprof
-rwxr-xr-x 1 root   root     321988 2010-03-08 20:36 /usr/bin/ssh
-rwxr-xr-x 1 root   root     100324 2010-03-08 20:36 /usr/bin/ssh-add
-rwxr-sr-x 1 root   ssh       79240 2010-03-08 20:36 /usr/bin/ssh-agent
-rwxr-xr-x 1 root   root       1452 2010-03-08 20:35 /usr/bin/ssh-argv0
lrwxrwxrwx 1 root   root         29 2010-08-29 12:53 /usr/bin/ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x 1 root   root       1316 2010-03-08 20:35 /usr/bin/ssh-copy-id
-rwxr-xr-x 1 root   root     124904 2010-03-08 20:36 /usr/bin/ssh-keygen
-rwxr-xr-x 1 root   root     174328 2010-03-08 20:36 /usr/bin/ssh-keyscan
-rwxr-xr-x 1 root   root      88040 2010-03-08 20:36 /usr/bin/ssh-vulnkey
lrwxrwxrwx 1 root   root         23 2010-08-29 12:53 /usr/bin/start_embedded -> ../lib/erlang/bin/start
-rwxr-xr-x 1 root   root       1305 2010-01-27 07:30 /usr/bin/startfluxbox
-rwxr-xr-x 1 root   root       1246 2010-03-27 04:37 /usr/bin/start-pulseaudio-x11
-rwxr-xr-x 1 root   root       4481 2009-12-07 19:07 /usr/bin/startx
-rwxr-xr-x 1 root   root      50824 2010-03-05 08:29 /usr/bin/stat
-rwxr-xr-x 1 root   root     206584 2010-02-15 22:35 /usr/bin/strace
-rwxr-xr-x 1 root   root       5504 2009-11-27 04:22 /usr/bin/stream
-rwxr-xr-x 1 root   root      22304 2010-04-19 07:00 /usr/bin/strings
-rwxr-xr-x 1 root   root     192268 2010-04-19 07:00 /usr/bin/strip
-rwsr-xr-x 1 root   root     127664 2010-04-13 22:43 /usr/bin/sudo
-rwsr-xr-x 1 root   root     127664 2010-04-13 22:43 /usr/bin/sudoedit
-rwxr-xr-x 1 root   root      38516 2010-03-05 08:29 /usr/bin/sum
-rwxr-xr-x 1 root   root       3031 2010-02-04 22:42 /usr/bin/su-to-root
-rwxr-xr-x 1 root   root         46 2010-04-24 07:22 /usr/bin/svlc
-rwxr-xr-x 1 root   root      16368 2010-04-16 02:17 /usr/bin/synclient
-rwxr-xr-x 1 root   root       9708 2010-04-16 02:17 /usr/bin/syndaemon
-rwxr-xr-x 1 root   root      28956 2008-07-15 19:06 /usr/bin/syslinux
-rwxr-xr-x 1 root   root       1421 2008-07-15 19:06 /usr/bin/syslinux2ansi
-rwxr-xr-x 1 root   root         95 2010-04-10 23:30 /usr/bin/system-config-printer
-rwxr-xr-x 1 root   root         80 2010-04-10 23:30 /usr/bin/system-config-printer-applet
-rwxr-xr-x 1 root   root       9704 2010-03-07 08:33 /usr/bin/tabs
-rwxr-xr-x 1 root   root      34432 2010-03-05 08:29 /usr/bin/tac
-rwxr-xr-x 1 root   root      50864 2010-03-05 08:29 /usr/bin/tail
-rwxr-xr-x 1 root   root        535 2010-04-15 09:06 /usr/bin/tap2deb
-rwxr-xr-x 1 root   root        622 2010-04-15 09:06 /usr/bin/tap2rpm
-rwxr-xr-x 1 root   root        603 2010-04-15 09:06 /usr/bin/tapconvert
-rwxr-xr-x 1 root   root      22478 2010-03-20 04:33 /usr/bin/tasksel
-rwxr-xr-x 1 root   root       9652 2010-03-22 22:51 /usr/bin/taskset
-rwxr-xr-x 1 root   root     116396 2010-02-22 15:21 /usr/bin/tbl
lrwxrwxrwx 1 root   root         23 2010-08-29 12:53 /usr/bin/tclsh -> /etc/alternatives/tclsh
-rwxr-xr-x 1 root   root       5492 2009-11-06 16:49 /usr/bin/tclsh8.4
-rwxr-xr-x 1 root   root      54628 2010-04-09 20:28 /usr/bin/tdbbackup
-rwxr-xr-x 1 root   root      30240 2010-03-05 08:29 /usr/bin/tee
lrwxrwxrwx 1 root   root         24 2010-08-29 12:53 /usr/bin/telnet -> /etc/alternatives/telnet
-rwxr-xr-x 1 root   root      80056 2010-03-07 08:23 /usr/bin/telnet.netkit
-rwxr-xr-x 1 root   root      26188 2010-03-05 08:29 /usr/bin/test
lrwxrwxrwx 1 root   root         26 2010-08-29 12:53 /usr/bin/testparm -> /etc/alternatives/testparm
-rwxr-xr-x 1 root   root     952660 2010-04-09 20:29 /usr/bin/testparm.samba3
-rwxr-xr-x 1 root   root       2295 2009-11-13 23:45 /usr/bin/tgz
-rwxr-xr-x 1 root   root      50852 2010-03-07 08:33 /usr/bin/tic
-rwxr-xr-x 1 root   root      13960 2010-03-07 10:48 /usr/bin/time
-rwxr-xr-x 1 root   root      94932 2010-04-15 10:15 /usr/bin/time-admin
-rwxr-xr-x 1 root   root       9668 2009-12-17 00:34 /usr/bin/tload
-rwxr-xr-x 1 root   root       9716 2010-03-07 08:33 /usr/bin/toe
-rwxr-xr-x 1 root   root       1561 2010-03-30 14:43 /usr/bin/tomboy
-rwxr-xr-x 1 root   root        570 2010-03-30 14:43 /usr/bin/tomboy-panel
-rwxr-xr-x 1 root   root      68524 2009-12-17 00:34 /usr/bin/top
-rwxr-xr-x 1 root   root      88984 2010-02-05 00:23 /usr/bin/toshset
-rwxr-xr-x 1 root   root     459612 2010-04-14 16:34 /usr/bin/totem
-rwxr-xr-x 1 root   root     151432 2010-04-14 16:34 /usr/bin/totem-audio-preview
-rwxr-xr-x 1 root   root     151436 2010-04-14 16:34 /usr/bin/totem-video-indexer
-rwxr-xr-x 1 root   root     162996 2010-04-14 16:34 /usr/bin/totem-video-thumbnailer
lrwxrwxrwx 1 root   root         10 2010-08-29 12:53 /usr/bin/touch -> /bin/touch
-rwxr-xr-x 1 root   root       9752 2010-03-07 08:33 /usr/bin/tput
-rwxr-xr-x 1 root   root      46688 2010-03-05 08:29 /usr/bin/tr
-rwxr-xr-x 1 root   root       9676 2010-03-12 04:12 /usr/bin/tracepath
-rwxr-xr-x 1 root   root       9700 2010-03-12 04:12 /usr/bin/tracepath6
lrwxrwxrwx 1 root   root         29 2010-08-29 12:53 /usr/bin/traceroute6 -> /etc/alternatives/traceroute6
-rwsr-xr-x 1 root   root      13952 2010-03-12 04:12 /usr/bin/traceroute6.iputils
-rwxr-xr-x 1 root   root     693924 2010-04-14 04:25 /usr/bin/transmission
-rwxr-xr-x 1 root   root        677 2010-04-15 09:06 /usr/bin/trial
-rwxr-xr-x 1 root   root     479820 2010-02-22 15:21 /usr/bin/troff
-rwxr-xr-x 1 root   root      50848 2010-03-05 08:29 /usr/bin/truncate
-rwxr-xr-x 1 root   root      92344 2010-02-09 08:37 /usr/bin/tsclient
-rwxr-xr-x 1 root   root      18016 2010-03-07 08:33 /usr/bin/tset
-rwxr-xr-x 1 root   root      38420 2010-03-05 08:29 /usr/bin/tsort
-rwxr-xr-x 1 root   root      30216 2010-03-05 08:29 /usr/bin/tty
-rwxr-xr-x 1 root   root        614 2010-04-15 09:06 /usr/bin/twistd
-rwxr-xr-x 1 root   root       7259 2010-04-22 21:56 /usr/bin/tzselect
-rwxr-xr-x 1 root   root      11387 2010-04-23 17:56 /usr/bin/u1sdtool
lrwxrwxrwx 1 root   root         10 2010-08-29 12:53 /usr/bin/ubuntu-bug -> apport-bug
-rwxr-xr-x 1 root   root       2549 2010-04-23 17:56 /usr/bin/ubuntuone-launch
-rwxr-xr-x 1 root   root      41866 2010-04-23 17:56 /usr/bin/ubuntuone-preferences
-rwxr-xr-x 1 root   root       6037 2010-04-24 07:28 /usr/bin/ubuntu-support-status
-rwxr-xr-x 1 root   root      37925 2009-08-27 11:16 /usr/bin/ucf
-rwxr-xr-x 1 root   root      19290 2008-05-30 11:22 /usr/bin/ucfq
-rwxr-xr-x 1 root   root      10405 2008-05-30 11:22 /usr/bin/ucfr
-rwxr-xr-x 1 root   root      17868 2010-01-11 20:28 /usr/bin/ucs2any
-rwxr-xr-x 1 root   root      43312 2010-04-13 13:12 /usr/bin/udisks
-rwxr-xr-x 1 root   root      13752 2009-11-10 21:12 /usr/bin/ul
-rwxr-xr-x 1 root   root     174700 2010-04-15 07:24 /usr/bin/umax_pp
-rwxr-xr-x 1 root   root      19931 2010-03-20 04:43 /usr/bin/unattended-upgrade
lrwxrwxrwx 1 root   root         18 2010-08-29 12:53 /usr/bin/unattended-upgrades -> unattended-upgrade
-rwxr-xr-x 1 root   root      34396 2010-03-05 08:29 /usr/bin/unexpand
-rwxr-xr-x 1 root   root        530 2010-03-12 12:05 /usr/bin/unicode_stop
-rwxr-xr-x 1 root   root      38452 2010-03-05 08:29 /usr/bin/uniq
-rwxr-xr-x 1 root   root      30212 2010-03-05 08:29 /usr/bin/unlink
lrwxrwxrwx 1 root   root          4 2010-08-29 12:53 /usr/bin/unlzma -> lzma
-rwxr-xr-x 1 root   root         50 2010-04-24 04:28 /usr/bin/unopkg
-rwxr-xr-x 1 root   root       5516 2010-03-22 22:51 /usr/bin/unshare
-rwxr-xr-x 1 root   root     153336 2010-03-07 11:04 /usr/bin/unzip
-rwxr-xr-x 1 root   root      67220 2010-03-07 11:04 /usr/bin/unzipsfx
-rwxr-xr-x 1 root   root      37191 2010-04-15 22:23 /usr/bin/update-alternatives
lrwxrwxrwx 1 root   root         26 2010-08-29 12:53 /usr/bin/updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x 1 root   root      34492 2010-03-24 15:16 /usr/bin/updatedb.mlocate
-rwxr-xr-x 1 root   root      13932 2010-04-09 15:37 /usr/bin/update-desktop-database
-rwxr-xr-x 1 root   root       5297 2010-03-30 17:43 /usr/bin/update-gconf-defaults
-rwxr-xr-x 1 root   root       4380 2010-04-24 07:28 /usr/bin/update-manager
-rwxr-xr-x 1 root   root     116968 2010-02-04 22:42 /usr/bin/update-menus
-rwxr-xr-x 1 root   root        672 2010-04-17 06:57 /usr/bin/update-mime-database
-rwxr-xr-x 1 root   root      42836 2010-04-17 06:57 /usr/bin/update-mime-database.real
-rwxr-xr-x 1 root   root      60004 2010-04-14 01:52 /usr/bin/update-notifier
-rwxr-xr-x 1 root   root       3331 2010-03-10 03:08 /usr/bin/update-pciids
-rwxr-xr-x 1 root   root       6165 2010-01-18 12:56 /usr/bin/update-perl-sax-parsers
-rwxr-xr-x 1 root   root      18028 2010-03-05 15:20 /usr/bin/upower
-rwxr-xr-x 1 root   root       5488 2009-12-17 00:34 /usr/bin/uptime
-rwxr-xr-x 1 root   root       3089 2010-04-13 20:53 /usr/bin/usb-creator-gtk
-rwxr-xr-x 1 root   root       4202 2009-11-06 22:20 /usr/bin/usb-devices
-rwxr-xr-x 1 root   root       5520 2010-03-25 13:12 /usr/bin/usb_printerid
-rwxr-xr-x 1 root   root      30244 2010-03-05 08:29 /usr/bin/users
-rwxr-xr-x 1 root   root     122176 2010-04-15 10:15 /usr/bin/users-admin
-rwxr-xr-x 1 root   root       5524 2010-03-22 22:51 /usr/bin/uuidgen
-rwxr-xr-x 1 root   root       3674 2010-03-31 14:47 /usr/bin/uxterm
-rwxr-xr-x 1 root   root       2220 2009-11-13 23:45 /usr/bin/uz
lrwxrwxrwx 1 root   root         44 2010-08-29 13:14 /usr/bin/VBoxClient -> /opt/VBoxGuestAdditions-3.2.8/bin/VBoxClient
lrwxrwxrwx 1 root   root         48 2010-08-29 13:14 /usr/bin/VBoxClient-all -> /opt/VBoxGuestAdditions-3.2.8/bin/VBoxClient-all
lrwxrwxrwx 1 root   root         45 2010-08-29 13:14 /usr/bin/VBoxControl -> /opt/VBoxGuestAdditions-3.2.8/bin/VBoxControl
lrwxrwxrwx 1 root   root         20 2010-09-01 12:31 /usr/bin/vi -> /etc/alternatives/vi
lrwxrwxrwx 1 root   root         22 2010-09-01 12:31 /usr/bin/view -> /etc/alternatives/view
-rwxr-xr-x 1 root   root      18440 2010-03-23 01:23 /usr/bin/viewres
-rwxr-xr-x 1 root   root     638492 2010-04-16 17:49 /usr/bin/vim.tiny
-rwxr-xr-x 1 root   root     279360 2010-04-15 01:14 /usr/bin/vinagre
-rwxr-xr-x 1 root   root       9688 2010-04-09 13:05 /usr/bin/vino-passwd
-rwxr-xr-x 1 root   root      51460 2010-04-09 13:05 /usr/bin/vino-preferences
-rwxr-xr-x 1 root   root       9644 2010-04-24 07:23 /usr/bin/vlc
-rwxr-xr-x 1 root   root       9680 2010-04-24 07:23 /usr/bin/vlc-wrapper
-rwxr-xr-x 1 root   root       5492 2010-04-22 19:48 /usr/bin/vmmouse_detect
-rwxr-xr-x 1 root   root      22024 2009-12-17 00:34 /usr/bin/vmstat
-rwxr-xr-x 1 root   root       5520 2009-11-10 05:20 /usr/bin/volname
lrwxrwxrwx 1 root   root         19 2010-08-29 12:53 /usr/bin/w -> /etc/alternatives/w
-rwxr-xr-x 1 root   root    1192164 2009-11-10 23:02 /usr/bin/w3m
-rwxr-xr-x 1 root   root       1132 2009-11-10 23:02 /usr/bin/w3mman
-rwxr-sr-x 1 root   tty       13864 2010-03-22 22:51 /usr/bin/wall
-rwxr-xr-x 1 root   root      14212 2009-12-17 00:34 /usr/bin/watch
-rwxr-xr-x 1 root   root      42636 2010-03-05 08:29 /usr/bin/wc
-rwxr-xr-x 1 root   root        326 2010-04-09 15:15 /usr/bin/wftopfa
-rwxr-xr-x 1 root   root     333364 2010-01-06 19:02 /usr/bin/wget
-rwxr-xr-x 1 root   root     102344 2010-03-02 15:31 /usr/bin/whatis
-rwxr-xr-x 1 root   root       9912 2010-03-22 22:51 /usr/bin/whereis
lrwxrwxrwx 1 root   root         10 2010-08-29 12:53 /usr/bin/which -> /bin/which
-rwxr-xr-x 1 root   root      22100 2010-02-24 01:42 /usr/bin/whiptail
-rwxr-xr-x 1 root   root      38548 2010-03-05 08:29 /usr/bin/who
-rwxr-xr-x 1 root   root      30220 2010-03-05 08:29 /usr/bin/whoami
-rwxr-xr-x 1 root   root      41912 2010-03-20 06:23 /usr/bin/whois
lrwxrwxrwx 1 root   root         22 2010-08-29 12:53 /usr/bin/wish -> /etc/alternatives/wish
-rwxr-xr-x 1 root   root       5500 2009-11-06 17:02 /usr/bin/wish8.4
-rwxr-xr-x 1 root   root        210 2009-11-10 14:46 /usr/bin/withsctp
-rwxr-xr-x 1 root   root     371208 2010-03-20 00:43 /usr/bin/wodim
-rwxr-xr-x 1 root   root       5512 2010-03-24 21:08 /usr/bin/word-list-compress
-rwxr-xr-x 1 root   root      22180 2010-03-07 11:24 /usr/bin/wpa_passphrase
-rwxr-xr-x 1 root   root      13844 2009-12-17 00:34 /usr/bin/w.procps
lrwxrwxrwx 1 root   root         23 2010-08-29 12:53 /usr/bin/write -> /etc/alternatives/write
lrwxrwxrwx 1 root   root         29 2010-08-29 12:53 /usr/bin/www-browser -> /etc/alternatives/www-browser
-rwsr-sr-x 1 root   root       9664 2010-04-09 04:53 /usr/bin/X
lrwxrwxrwx 1 root   root          1 2010-08-29 12:53 /usr/bin/X11 -> .
-rwxr-xr-x 1 root   root     113008 2010-03-12 23:30 /usr/bin/x11perf
-rwxr-xr-x 1 root   root       2703 2010-03-12 23:30 /usr/bin/x11perfcomp
-rwxr-xr-x 1 root   root      34392 2010-03-09 18:22 /usr/bin/xargs
-rwxr-xr-x 1 root   root      30780 2009-12-07 19:06 /usr/bin/xauth
-rwxr-xr-x 1 root   root      15228 2010-03-12 23:30 /usr/bin/xbiff
-rwxr-xr-x 1 root   root      75672 2010-02-17 07:10 /usr/bin/xbrlapi
-rwxr-xr-x 1 root   root      26768 2010-03-12 23:30 /usr/bin/xcalc
-rwxr-xr-x 1 root   root      14020 2010-03-12 23:30 /usr/bin/xclipboard
-rwxr-xr-x 1 root   root      36400 2010-03-12 23:30 /usr/bin/xclock
-rwxr-xr-x 1 root   root      30560 2010-03-20 03:51 /usr/bin/xcmsdb
-rwxr-xr-x 1 root   root      14560 2010-03-12 23:30 /usr/bin/xconsole
-rwxr-xr-x 1 root   root      13816 2010-03-12 23:30 /usr/bin/xcursorgen
-rwxr-xr-x 1 root   root       9864 2010-03-12 23:30 /usr/bin/xcutsel
-rwxr-xr-x 1 root   root      14806 2010-03-12 12:54 /usr/bin/xdg-desktop-icon
-rwxr-xr-x 1 root   root      39267 2010-03-12 12:54 /usr/bin/xdg-desktop-menu
-rwxr-xr-x 1 root   root      17738 2010-03-12 12:54 /usr/bin/xdg-email
-rwxr-xr-x 1 root   root      24129 2010-03-12 12:54 /usr/bin/xdg-icon-resource
-rwxr-xr-x 1 root   root      28264 2010-03-12 12:54 /usr/bin/xdg-mime
-rwxr-xr-x 1 root   root      10229 2010-03-12 12:54 /usr/bin/xdg-open
-rwxr-xr-x 1 root   root      19319 2010-03-12 12:54 /usr/bin/xdg-screensaver
-rwxr-xr-x 1 root   root        234 2010-04-17 03:03 /usr/bin/xdg-user-dir
-rwxr-xr-x 1 root   root      18100 2010-01-25 22:21 /usr/bin/xdg-user-dirs-gtk-update
-rwxr-xr-x 1 root   root      17944 2010-04-17 03:03 /usr/bin/xdg-user-dirs-update
-rwxr-xr-x 1 root   root      59796 2010-03-12 23:30 /usr/bin/xditview
-rwxr-xr-x 1 root   root      26628 2010-03-23 01:23 /usr/bin/xdpyinfo
-rwxr-xr-x 1 root   root       5500 2010-03-23 01:23 /usr/bin/xdriinfo
-rwxr-xr-x 1 root   root     526004 2010-03-12 23:30 /usr/bin/xedit
-rwxr-xr-x 1 root   root      22104 2010-03-23 01:23 /usr/bin/xev
-rwxr-xr-x 1 root   root      18992 2010-03-12 23:30 /usr/bin/xeyes
-rwxr-xr-x 1 root   root      23112 2010-03-23 01:23 /usr/bin/xfd
-rwxr-xr-x 1 root   root      31340 2010-03-23 01:23 /usr/bin/xfontsel
-rwxr-xr-x 1 root   root       5516 2010-03-07 11:28 /usr/bin/xfsinfo
-rwxr-xr-x 1 root   root       9624 2010-03-20 03:51 /usr/bin/xgamma
-rwxr-xr-x 1 root   root      53284 2010-03-12 23:30 /usr/bin/xgc
-rwxr-xr-x 1 root   root      13812 2010-03-20 03:51 /usr/bin/xhost
-rwxr-xr-x 1 root   root      13876 2009-12-07 19:07 /usr/bin/xinit
-rwxr-xr-x 1 root   root      38836 2010-04-15 19:01 /usr/bin/xinput
-rwxr-xr-x 1 root   root       9640 2009-12-07 19:04 /usr/bin/xkbbell
-rwxr-xr-x 1 root   root     181408 2009-12-07 19:04 /usr/bin/xkbcomp
-rwxr-xr-x 1 root   root      30244 2009-12-07 19:04 /usr/bin/xkbevd
-rwxr-xr-x 1 root   root      89800 2009-12-07 19:04 /usr/bin/xkbprint
-rwxr-xr-x 1 root   root      18420 2009-12-07 19:04 /usr/bin/xkbvleds
-rwxr-xr-x 1 root   root      14356 2009-12-07 19:04 /usr/bin/xkbwatch
-rwxr-xr-x 1 root   root      14495 2010-03-20 03:51 /usr/bin/xkeystone
-rwxr-xr-x 1 root   root       9744 2010-03-23 01:23 /usr/bin/xkill
-rwxr-xr-x 1 root   root      14288 2010-03-12 23:30 /usr/bin/xload
-rwxr-xr-x 1 root   root      14408 2010-03-12 23:30 /usr/bin/xlogo
-rwxr-xr-x 1 root   root       9628 2010-03-23 01:23 /usr/bin/xlsatoms
-rwxr-xr-x 1 root   root       9652 2010-03-23 01:23 /usr/bin/xlsclients
-rwxr-xr-x 1 root   root      22064 2010-03-23 01:23 /usr/bin/xlsfonts
-rwxr-xr-x 1 root   root      31672 2010-03-12 23:30 /usr/bin/xmag
-rwxr-xr-x 1 root   root      53120 2010-03-12 23:30 /usr/bin/xman
-rwxr-xr-x 1 root   root      14360 2010-03-23 01:23 /usr/bin/xmessage
-rwxr-xr-x 1 root   root       7204 2010-04-19 11:26 /usr/bin/xml2po
-rwxr-xr-x 1 root   root      13792 2009-12-16 09:50 /usr/bin/xmlcatalog
-rwxr-xr-x 1 root   root      55760 2009-12-16 09:50 /usr/bin/xmllint
-rwxr-xr-x 1 root   root      26376 2010-03-20 03:51 /usr/bin/xmodmap
-rwxr-xr-x 1 root   root       9748 2010-03-12 23:30 /usr/bin/xmore
-rwxr-xr-x 1 root   root    1749448 2010-04-23 22:16 /usr/bin/Xorg
-rwxr-xr-x 1 root   root       4961 2010-01-18 12:58 /usr/bin/xpath
lrwxrwxrwx 1 root   root         33 2010-08-29 13:30 /usr/bin/xpcshell-1.9.2 -> ../lib/xulrunner-1.9.2.8/xpcshell
-rwxr-xr-x 1 root   root      31504 2010-03-23 01:23 /usr/bin/xprop
-rwxr-xr-x 1 root   root      53492 2010-03-25 13:12 /usr/bin/xqxdecode
-rwxr-xr-x 1 root   root      46708 2010-03-20 03:51 /usr/bin/xrandr
-rwxr-xr-x 1 root   root      22100 2010-03-20 03:51 /usr/bin/xrdb
-rwxr-xr-x 1 root   root       9820 2010-03-20 03:51 /usr/bin/xrefresh
-rwxr-xr-x 1 root   root     113440 2010-04-15 16:47 /usr/bin/xscreensaver-getimage
-rwxr-xr-x 1 root   root      16299 2010-04-15 16:47 /usr/bin/xscreensaver-getimage-file
-rwxr-xr-x 1 root   root       5044 2010-04-15 16:47 /usr/bin/xscreensaver-getimage-video
-rwxr-xr-x 1 root   root      17892 2010-04-15 16:47 /usr/bin/xscreensaver-gl-helper
-rwxr-xr-x 1 root   root      26805 2010-04-15 16:47 /usr/bin/xscreensaver-text
lrwxrwxrwx 1 root   root         35 2010-08-29 12:53 /usr/bin/x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x 1 root   root      30296 2010-03-20 03:51 /usr/bin/xset
-rwxr-xr-x 1 root   root       5524 2010-03-20 03:51 /usr/bin/xsetmode
-rwxr-xr-x 1 root   root       9624 2010-03-20 03:51 /usr/bin/xsetpointer
-rwxr-xr-x 1 root   root      13804 2010-03-20 03:51 /usr/bin/xsetroot
-rwxr-xr-x 1 root   root      34348 2010-04-23 01:55 /usr/bin/xsetwacom
-rwxr-xr-x 1 root   root      22056 2010-01-19 17:32 /usr/bin/xsltproc
-rwxr-xr-x 1 root   root      75892 2009-12-07 19:01 /usr/bin/xsm
-rwxr-xr-x 1 root   root      10052 2010-03-20 03:51 /usr/bin/xstdcmap
-rwxr-xr-x 1 root   root       4093 2010-04-23 13:22 /usr/bin/xsubpp
-rwxr-sr-x 1 root   utmp     354444 2010-03-31 14:47 /usr/bin/xterm
lrwxrwxrwx 1 root   root         37 2010-08-29 12:53 /usr/bin/x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
lrwxrwxrwx 1 root   root         27 2010-08-29 13:30 /usr/bin/xulrunner -> /etc/alternatives/xulrunner
lrwxrwxrwx 1 root   root         34 2010-08-29 13:30 /usr/bin/xulrunner-1.9.2 -> ../lib/xulrunner-1.9.2.8/xulrunner
-rwxr-xr-x 1 root   root      31292 2010-03-20 03:51 /usr/bin/xvidtune
-rwxr-xr-x 1 root   root       9632 2010-03-23 01:23 /usr/bin/xvinfo
-rwxr-xr-x 1 root   root      22048 2010-03-12 23:30 /usr/bin/xwd
lrwxrwxrwx 1 root   root         36 2010-09-08 20:51 /usr/bin/x-window-decorator -> /etc/alternatives/x-window-decorator
lrwxrwxrwx 1 root   root         34 2010-08-29 12:53 /usr/bin/x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x 1 root   root      26144 2010-03-23 01:23 /usr/bin/xwininfo
-rwxr-xr-x 1 root   root      26120 2010-03-12 23:30 /usr/bin/xwud
lrwxrwxrwx 1 root   root         31 2010-09-09 14:47 /usr/bin/x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x 1 root   root      13876 2010-04-16 17:50 /usr/bin/xxd
-rwxr-xr-x 1 root   root     270720 2010-04-17 05:15 /usr/bin/yelp
-rwxr-xr-x 1 root   root      30208 2010-03-05 08:29 /usr/bin/yes
-rwxr-xr-x 1 root   root      13764 2010-04-22 22:15 /usr/bin/zdump
-rwxr-xr-x 1 root   root      66444 2010-03-29 16:02 /usr/bin/zenity
-rwxr-xr-x 1 root   root     181104 2010-02-15 22:40 /usr/bin/zip
-rwxr-xr-x 1 root   root      80352 2010-02-15 22:40 /usr/bin/zipcloak
-rwxr-xr-x 1 root   root       2953 2010-03-07 11:04 /usr/bin/zipgrep
-rwxr-xr-x 1 root   root     153336 2010-03-07 11:04 /usr/bin/zipinfo
-rwxr-xr-x 1 root   root      76060 2010-02-15 22:40 /usr/bin/zipnote
-rwxr-xr-x 1 root   root      80156 2010-02-15 22:40 /usr/bin/zipsplit
-rwxr-xr-x 1 root   root      57588 2010-03-25 13:12 /usr/bin/zjsdecode
-rwxr-xr-x 1 root   root      88168 2010-03-02 15:31 /usr/bin/zsoelim

```


> **anntzer said:**
> sudo chmod root /usr/bin/*.

How did you do that?

```

malik@Ubuntu:~$ sudo chmod root /usr/bin/*
chmod: invalid mode: `root'
Try `chmod --help' for more information.

```

---

### Post by robsoles on 2010-09-14
Would you please check /var/log/messages (and perhaps other logs under /var/log) and try to find the entries relating to the point in time that this 'User not allowed ...' error occurs?

It is odd because by my understanding your command should have changed the user but not the group of the files and (again, AFAIK) changing the owner alone to root (from root!?) shouldn't have made a permissions issue for startx's dependencies.

Please paste relevant parts of the log. It would be cool if you googled 'ubuntu forum tags' and found out how to make a 'code' block of them for us.

---

### Post by gmargo on 2010-09-14
On my 10.04 Lucid system the **at** command is owned by **daemon**.
```

gmargo@lucid1 927$ ls -l /usr/bin/ | grep -v "root   root"
total 142660
-rwsr-sr-x 1 daemon daemon    42812 Mar  4  2010 at
-rwxr-sr-x 1 root   tty        9708 Nov 10  2009 bsd-write
-rwxr-sr-x 1 root   shadow    53428 Jan 26  2010 chage
-rwxr-sr-x 1 root   crontab   31656 Apr 14 16:29 crontab
-rwxr-sr-x 1 root   mail      13924 Jan 14  2010 dotlockfile
-rwxr-sr-x 1 root   shadow    18104 Jan 26  2010 expiry
-rwsr-xr-x 1 root   lpadmin   13540 Jun 18 08:08 lppasswd
-rwxr-sr-x 3 root   mail       9760 Jan 14  2010 mail-lock
-rwxr-sr-x 3 root   mail       9760 Jan 14  2010 mail-touchlock
-rwxr-sr-x 3 root   mail       9760 Jan 14  2010 mail-unlock
-rwxr-sr-x 1 root   mlocate   30316 Mar 24 03:16 mlocate
-rwxr-sr-x 1 root   utmp     340604 Nov 10  2009 screen
-rwxr-sr-x 1 root   ssh       79240 May 19 09:31 ssh-agent
-rwxr-sr-x 1 root   tty       13864 Mar 22 10:51 wall
-rwxr-sr-x 1 root   utmp     354444 Mar 31 02:47 xterm
gmargo@lucid1 928$ dpkg -S /usr/bin/at
at: /usr/bin/at

```

---

### Post by anntzer on 2010-09-15
> **sikander3786 said:**
> I am unable to figure it out because nearly 99% files in my /usr/bin are owned by root.

How did you do that?

```

malik@Ubuntu:~$ sudo chmod root /usr/bin/*
chmod: invalid mode: `root'
Try `chmod --help' for more information.

```

Sorry, I meant chown.

My /var/log/auth.log has a section like
```

Sep 13 22:11:45 antony sudo:   antony : TTY=pts/1 ; PWD=/home/antony/Bureau ; USER=root ; COMMAND=/bin/chown root /usr/bin/[ /usr/bin/2to3 /usr/bin/2to3-2.6 /usr/bin/2to3-3.1 /usr/bin/411toppm /usr/bin/7z /usr/bin/7za /usr/bin/a2p /usr/bin/a2ping /usr/bin/aconnect /usr/bin/acpi_fakekey /usr/bin/acpi_listen /usr/bin/acyclic /usr/bin/add-apt-repository /usr/bin/addftinfo /usr/bin/addpart /usr/bin/addr2line /usr/bin/afm2afm /usr/bin/afm2pl /usr/bin/afm2tfm /usr/bin/afmtodit /usr/bin/aircrack-ng /usr/bin/airdecap-ng /usr/bin/airdecloak-ng /usr/bin/airolib-ng /usr/bin/akonadi2xml /usr/bin/akonadi_birthdays_resource /usr/bin/akonadi_contacts_resource /usr/bin/akonadi_control /usr/bin/akonadictl /usr/bin/akonadi_ical_resource /usr/bin/akonadi_imap_resource /usr/bin/akonadi_kabc_resource /usr/bin/akonadi_kcal_resource /usr/bin/akonadi_knut_resource /usr/bin/akonadi_kolabproxy_resource /usr/bin/akonadi_localbookmarks_resource /usr/bin/akonadi_maildir_resource
Sep 13 22:11:45 antony sudo:   antony : (command continued) /usr/bin/akonadi_maildispatcher_agent /usr/bin/akonadi_mailtransport_dummy_resource /usr/bin/akonadi_mbox_resource /usr/bin/akonadi_microblog_resource /usr/bin/akonadi_nepomuk_calendar_feeder /usr/bin/akonadi_nepomuk_contact_feeder /usr/bin/akonadi_nepomuktag_resource /usr/bin/akonadi_nntp_resource /usr/bin/akonadi_notes_resource /usr/bin/akonadi_pop3_resource /usr/bin/akonadiserver /usr/bin/akonaditray /usr/bin/akonadi_vcarddir_resource /usr/bin/akonadi_vcard_resource /usr/bin/akregator /usr/bin/akregatorstorageexporter /usr/bin/aleph /usr/bin/allcm /usr/bin/allec /usr/bin/allneeded /usr/bin/alsamixer /usr/bin/alsamixergui /usr/bin/amarok /usr/bin/amarok_afttagger /usr/bin/amarokcollectionscanner /usr/bin/amarokmp3tunesharmonydaemon /usr/bin/amarokpkg /usr/bin/amidi /usr/bin/amixer /usr/bin/amuFormat.sh /usr/bin/animate /usr/bin/ant /usr/bin/antlr3 /usr/bin/anytopnm /usr/bin/aoss /usr/bin/aot-compile /usr/bin/aplay

```
(and so on for many lines)

And now I'm unable to locate!
```

locate: ne peut ouvrir `/var/lib/mlocate/mlocate.db': Permission non accordée

```
("cannot open ..., permission denied")

---

### Post by gmargo on 2010-09-15
> **anntzer said:**
> 
And now I'm unable to locate!
```

locate: ne peut ouvrir `/var/lib/mlocate/mlocate.db': Permission non accordée

```("cannot open ..., permission denied")

Did you modify permissions or groups as well?  The locate command (mlocate) should be set-group-id to the mlocate group.
```

gmargo@euler 2238$ ls -l /usr/bin/mlocate /usr/bin/updatedb.mlocate
-rwxr-sr-x 1 root mlocate 30316 Mar 24 03:16 /usr/bin/mlocate
-rwxr-xr-x 1 root root    34492 Mar 24 03:16 /usr/bin/updatedb.mlocate

```

---

