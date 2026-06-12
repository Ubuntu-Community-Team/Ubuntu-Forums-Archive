---
title: "constant unmounts of ext drive"
date: 2010-05-08
forum: General Help
---

### Post by cmcanulty on 2010-05-08
I have a ext4 (I have tried ext3 & NTFS and all behve the same) that unmounts every few minutes or seconds on my Gateway laptop. On my netbook it doesn't unmount. Both ate running Lucid though it did this inJaunty and Karmic   also. I am attaching some code in the hopes of solving this I will also post another with the grsync error messages. This makes backing up impossible. This happens with a Western Digital 120GB ext drive and a Maxtor 500GB ext drive.Thank you.

```

cmcanulty@Gateway:~$ sudo fdisk -l
[sudo] password for cmcanulty: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2e1d2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5599    44973936   83  Linux
/dev/sda2           38540       38913     3004124+   5  Extended
/dev/sda3            5600       38539   264590550   83  Linux
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
cmcanulty@Gateway:~$ 
cmcanulty@Gateway:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              43G  2.6G   38G   7% /
none                  497M  304K  497M   1% /dev
none                  501M  100K  501M   1% /dev/shm
none                  501M   96K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
/dev/sda3             249G   80G  157G  34% /home
/dev/sdb1             111G  188M  105G   1% /media/sdb1
cmcanulty@Gateway:~$ 
```

---

### Post by cmcanulty on 2010-05-08
More data, these are the grsync errors I am not  sure if that is considered code so I put code tags to be safe

```
*** Launching RSYNC command:
rsync -r -t -p -o -g -x -v --progress -b /home/cmcanulty/ /media/sdb1/

sending incremental file list
rsync: chgrp "/media/sdb1/." failed: Operation not permitted (1)
./
.ICEauthority
       21834 100%    0.00kB/s    0:00:00 (xfer#1, to-check=1682/1684)
.ICEauthority~
       11914 100%  612.36kB/s    0:00:00 (xfer#2, to-check=1681/1684)
.ICEauthority~~
       16412 100%  616.44kB/s    0:00:00 (xfer#3, to-check=1680/1684)
.ICEauthority~~~
         310 100%   11.21kB/s    0:00:00 (xfer#4, to-check=1679/1684)
.ICEauthority~~~~
       11914 100%  430.92kB/s    0:00:00 (xfer#5, to-check=1678/1684)
.ICEauthority~~~~~
       20604 100%  503.03kB/s    0:00:00 (xfer#6, to-check=1677/1684)
.ICEauthority~~~~~~
       20604 100%  394.53kB/s    0:00:00 (xfer#7, to-check=1676/1684)
.bash_history
        9438 100%  146.30kB/s    0:00:00 (xfer#8, to-check=1675/1684)
.bash_history~
        5475 100%   79.80kB/s    0:00:00 (xfer#9, to-check=1674/1684)
.bash_history~~
        9891 100%  144.17kB/s    0:00:00 (xfer#10, to-check=1673/1684)
.bash_history~~~
        5460 100%   74.06kB/s    0:00:00 (xfer#11, to-check=1672/1684)
.bash_history~~~~
        5475 100%   73.24kB/s    0:00:00 (xfer#12, to-check=1671/1684)
.bash_history~~~~~
       12331 100%  164.96kB/s    0:00:00 (xfer#13, to-check=1670/1684)
.bash_history~~~~~~
       12342 100%  154.52kB/s    0:00:00 (xfer#14, to-check=1669/1684)
.bash_logout
         220 100%    2.39kB/s    0:00:00 (xfer#15, to-check=1668/1684)
.bash_logout~
         220 100%    2.36kB/s    0:00:00 (xfer#16, to-check=1667/1684)
.bash_logout~~
         220 100%    2.36kB/s    0:00:00 (xfer#17, to-check=1666/1684)
.bashrc
        3208 100%   31.02kB/s    0:00:00 (xfer#18, to-check=1665/1684)
.bashrc~
        3180 100%   30.45kB/s    0:00:00 (xfer#19, to-check=1664/1684)
.bashrc~~
        3180 100%   30.45kB/s    0:00:00 (xfer#20, to-check=1663/1684)
.bashrc~~~
        3103 100%   29.42kB/s    0:00:00 (xfer#21, to-check=1662/1684)
.data
       12288 100%  103.45kB/s    0:00:00 (xfer#22, to-check=1661/1684)
.dmrc
          42 100%    0.31kB/s    0:00:00 (xfer#23, to-check=1660/1684)
.dmrc~
          42 100%    0.29kB/s    0:00:00 (xfer#24, to-check=1659/1684)
.dmrc~~
          41 100%    0.28kB/s    0:00:00 (xfer#25, to-check=1658/1684)
.dmrc~~~
          41 100%    0.26kB/s    0:00:00 (xfer#26, to-check=1657/1684)
.esd_auth
          16 100%    0.10kB/s    0:00:00 (xfer#27, to-check=1656/1684)
.esd_auth~
          16 100%    0.10kB/s    0:00:00 (xfer#28, to-check=1655/1684)
.esd_auth~~
          16 100%    0.10kB/s    0:00:00 (xfer#29, to-check=1654/1684)
.gksu.lock
           0 100%    0.00kB/s    0:00:00 (xfer#30, to-check=1653/1684)
.gksu.lock~
           0 100%    0.00kB/s    0:00:00 (xfer#31, to-check=1652/1684)
.gksu.lock~~
           0 100%    0.00kB/s    0:00:00 (xfer#32, to-check=1651/1684)
.gksu.lock~~~
           0 100%    0.00kB/s    0:00:00 (xfer#33, to-check=1650/1684)
.gksu.lock~~~~
           0 100%    0.00kB/s    0:00:00 (xfer#34, to-check=1649/1684)
.gksu.lock~~~~~
           0 100%    0.00kB/s    0:00:00 (xfer#35, to-check=1648/1684)
.gksu.lock~~~~~~
           0 100%    0.00kB/s    0:00:00 (xfer#36, to-check=1647/1684)
.gtk-bookmarks
         572 100%    3.56kB/s    0:00:00 (xfer#37, to-check=1646/1684)
.gtk-bookmarks~
         609 100%    3.79kB/s    0:00:00 (xfer#38, to-check=1645/1684)
.gtk-bookmarks~~
         555 100%    3.43kB/s    0:00:00 (xfer#39, to-check=1644/1684)
.gtk-bookmarks~~~
         157 100%    0.97kB/s    0:00:00 (xfer#40, to-check=1643/1684)
.gtk-bookmarks~~~~
         609 100%    3.76kB/s    0:00:00 (xfer#41, to-check=1642/1684)
.gtk-bookmarks~~~~~
         696 100%    4.30kB/s    0:00:00 (xfer#42, to-check=1641/1684)
.gtk-bookmarks~~~~~~
         696 100%    4.02kB/s    0:00:00 (xfer#43, to-check=1640/1684)
.isomaster
         676 100%    3.67kB/s    0:00:00 (xfer#44, to-check=1639/1684)
.mailcap
        3136 100%   16.92kB/s    0:00:00 (xfer#45, to-check=1638/1684)
.printer-groups.xml
          37 100%    0.20kB/s    0:00:00 (xfer#46, to-check=1637/1684)
.profile
         675 100%    3.64kB/s    0:00:00 (xfer#47, to-check=1636/1684)
.profile~
         675 100%    3.62kB/s    0:00:00 (xfer#48, to-check=1635/1684)
.profile~~
         675 100%    3.53kB/s    0:00:00 (xfer#49, to-check=1634/1684)
.pulse-cookie
         256 100%    1.34kB/s    0:00:00 (xfer#50, to-check=1633/1684)
.pulse-cookie~
         256 100%    1.33kB/s    0:00:00 (xfer#51, to-check=1632/1684)
.pulse-cookie~~
         256 100%    1.32kB/s    0:00:00 (xfer#52, to-check=1631/1684)
.pychessconf
        2474 100%   12.78kB/s    0:00:00 (xfer#53, to-check=1630/1684)
.qGorc
        1280 100%    6.61kB/s    0:00:00 (xfer#54, to-check=1629/1684)
.rdata
       94208 100%  457.71kB/s    0:00:00 (xfer#55, to-check=1628/1684)
.recently-used
        2253 100%   10.63kB/s    0:00:00 (xfer#56, to-check=1627/1684)
.recently-used.xbel
      191554 100%  890.78kB/s    0:00:00 (xfer#57, to-check=1626/1684)
.recently-used.xbel~
      153165 100%  682.99kB/s    0:00:00 (xfer#58, to-check=1625/1684)
.recently-used.xbel~~
      173299 100%  758.91kB/s    0:00:00 (xfer#59, to-check=1624/1684)
.recently-used.xbel~~~
         218 100%    0.95kB/s    0:00:00 (xfer#60, to-check=1623/1684)
.recently-used.xbel~~~~
      153165 100%  639.21kB/s    0:00:00 (xfer#61, to-check=1622/1684)
.recently-used.xbel~~~~~
      198029 100%  809.15kB/s    0:00:00 (xfer#62, to-check=1621/1684)
.recently-used.xbel~~~~~~
      199492 100%  735.16kB/s    0:00:00 (xfer#63, to-check=1620/1684)
.recently-used~
        2253 100%    8.27kB/s    0:00:00 (xfer#64, to-check=1619/1684)
.recently-used~~
        2819 100%   10.35kB/s    0:00:00 (xfer#65, to-check=1618/1684)
.registry
         237 100%    0.84kB/s    0:00:00 (xfer#66, to-check=1617/1684)
.rsrc
       90112 100%  313.17kB/s    0:00:00 (xfer#67, to-check=1616/1684)
.selected_editor
          66 100%    0.23kB/s    0:00:00 (xfer#68, to-check=1615/1684)
.sudo_as_admin_successful
           0 100%    0.00kB/s    0:00:00 (xfer#69, to-check=1614/1684)
.sudo_as_admin_successful~
           0 100%    0.00kB/s    0:00:00 (xfer#70, to-check=1613/1684)
.text
      479232 100%    1.43MB/s    0:00:00 (xfer#71, to-check=1612/1684)
.ubuntu-10.04-desktop-i386.iso.4Q2j5v
    83886080 100%   24.29MB/s    0:00:03 (xfer#72, to-check=1611/1684)
.usbcreator.log
      144041 100%  453.76kB/s    0:00:00 (xfer#73, to-check=1610/1684)
.usbcreator.log~
      176010 100%  524.04kB/s    0:00:00 (xfer#74, to-check=1609/1684)
.usbcreator.log~~
      176010 100%  420.26kB/s    0:00:00 (xfer#75, to-check=1608/1684)
.xsession-errors
      166875 100%  390.80kB/s    0:00:00 (xfer#76, to-check=1607/1684)
.xsession-errors.old
       87341 100%  169.23kB/s    0:00:00 (xfer#77, to-check=1606/1684)
.xsession-errors.old~
       65785 100%  125.47kB/s    0:00:00 (xfer#78, to-check=1605/1684)
.xsession-errors.old~~
        7846 100%   14.71kB/s    0:00:00 (xfer#79, to-check=1604/1684)
.xsession-errors.old~~~
       65785 100%  122.37kB/s    0:00:00 (xfer#80, to-check=1603/1684)
.xsession-errors.old~~~~
       65785 100%  121.67kB/s    0:00:00 (xfer#81, to-check=1602/1684)
.xsession-errors.old~~~~~
      717210 100%    1.20MB/s    0:00:00 (xfer#82, to-check=1601/1684)
.xsession-errors.old~~~~~~
      270165 100%  417.46kB/s    0:00:00 (xfer#83, to-check=1600/1684)
.xsession-errors~
      117560 100%  176.62kB/s    0:00:00 (xfer#84, to-check=1599/1684)
.xsession-errors~~
        4337 100%    6.51kB/s    0:00:00 (xfer#85, to-check=1598/1684)
.xsession-errors~~~
        3566 100%    5.35kB/s    0:00:00 (xfer#86, to-check=1597/1684)
.xsession-errors~~~~
      119637 100%  175.16kB/s    0:00:00 (xfer#87, to-check=1596/1684)
.xsession-errors~~~~~
      250728 100%  359.55kB/s    0:00:00 (xfer#88, to-check=1595/1684)
.xsession-errors~~~~~~
     1339770 100%    1.65MB/s    0:00:00 (xfer#89, to-check=1594/1684)
App_Runner_0.2.deb
        2294 100%    2.80kB/s    0:00:00 (xfer#90, to-check=1593/1684)
App_Runner_0.2.deb.1
        2294 100%    2.76kB/s    0:00:00 (xfer#91, to-check=1592/1684)
App_Runner_0.2.deb.2
        2294 100%    2.76kB/s    0:00:00 (xfer#92, to-check=1591/1684)
App_Runner_0.2.deb.3
        2294 100%    2.76kB/s    0:00:00 (xfer#93, to-check=1590/1684)
CERTIFICATE
        5360 100%    6.38kB/s    0:00:00 (xfer#94, to-check=1589/1684)
Darcy Library of Beulahtn.jpg
      712878 100%  810.44kB/s    0:00:00 (xfer#95, to-check=1588/1684)
Maxtor.sh
          82 100%    0.09kB/s    0:00:00 (xfer#96, to-check=1587/1684)
Maxtor.sh~
          90 100%    0.10kB/s    0:00:00 (xfer#97, to-check=1586/1684)
Results - FEBE 2010 01-09 17.13.43.html
        2560 100%    2.89kB/s    0:00:00 (xfer#98, to-check=1585/1684)
TaskCoach-0.71.0.tar.gz
     1779131 100%    1.77MB/s    0:00:00 (xfer#99, to-check=1584/1684)
TaxFormsServlet
        1161 100%    1.18kB/s    0:00:00 (xfer#100, to-check=1583/1684)
WD.sh
          78 100%    0.08kB/s    0:00:00 (xfer#101, to-check=1582/1684)
WD.sh~
          78 100%    0.08kB/s    0:00:00 (xfer#102, to-check=1581/1684)
ailurus_10.01-0revision1_all.deb
     1927200 100%    1.75MB/s    0:00:01 (xfer#103, to-check=1580/1684)
backup sources.list
           0 100%    0.00kB/s    0:00:00 (xfer#104, to-check=1579/1684)
bookmarks-2010-01-09.json
     1745396 100%   13.99MB/s    0:00:00 (xfer#105, to-check=1578/1684)
debreate_0.6.2-3_all.deb
       19898 100%  154.22kB/s    0:00:00 (xfer#106, to-check=1577/1684)
du -ch
       18369 100%  134.88kB/s    0:00:00 (xfer#107, to-check=1576/1684)
examples.desktop
         167 100%    1.23kB/s    0:00:00 (xfer#108, to-check=1575/1684)
examples.desktop~
         179 100%    1.31kB/s    0:00:00 (xfer#109, to-check=1574/1684)
firefox-3.6.tar.bz2
    10161471 100%   17.75MB/s    0:00:00 (xfer#110, to-check=1573/1684)
game.001
           0 100%    0.00kB/s    0:00:00 (xfer#111, to-check=1572/1684)
get-flash-videos_1.21-1_all.deb
       47148 100%   84.02kB/s    0:00:00 (xfer#112, to-check=1571/1684)
installed-software
       43839 100%   76.86kB/s    0:00:00 (xfer#113, to-check=1570/1684)
launchpad-update
        1289 100%    2.26kB/s    0:00:00 (xfer#114, to-check=1569/1684)
libflashplayer.so
    11771632 100%   10.79MB/s    0:00:01 (xfer#115, to-check=1568/1684)
log.001
          35 100%    0.74kB/s    0:00:00 (xfer#116, to-check=1567/1684)
missfont.log
         405 100%    8.60kB/s    0:00:00 (xfer#117, to-check=1566/1684)
pclinuxos-phoenix-xfce-2010.iso
   512470048 100%   29.63MB/s    0:00:16 (xfer#118, to-check=1565/1684)
picasa_3.0-current_i386.deb
    31784420 100%   19.79MB/s    0:00:01 (xfer#119, to-check=1564/1684)
profileFx3{default}.fbu
    19531128 100%   14.79MB/s    0:00:01 (xfer#120, to-check=1563/1684)
pup-431.iso
   110043136 100%   27.29MB/s    0:00:03 (xfer#121, to-check=1562/1684)
sqlite3
         814 100%    0.91kB/s    0:00:00 (xfer#122, to-check=1561/1684)
sqlite3~
           0 100%    0.00kB/s    0:00:00 (xfer#123, to-check=1560/1684)
taskcoach_0.77.0-1_all.deb
     1690652 100%    1.62MB/s    0:00:00 (xfer#124, to-check=1559/1684)
taskcoach_0.77.0-1_all.deb~
           0 100%    0.00kB/s    0:00:00 (xfer#125, to-check=1558/1684)
ubucompilator_0.0.1-1_all.english.version.deb
      174618 100%  166.85kB/s    0:00:01 (xfer#126, to-check=1557/1684)
ubucompilator_0.0.1-1_all.english.version.deb~
           0 100%    0.00kB/s    0:00:00 (xfer#127, to-check=1556/1684)
ubuntu-10.04-desktop-i386.iso
   733419520 100%   25.00MB/s    0:00:27 (xfer#128, to-check=1555/1684)
ubuntu-10.04-rc-netbook-i386.iso
   727814144 100%   25.25MB/s    0:00:27 (xfer#129, to-check=1554/1684)
ubuntu-files
           0 100%    0.00kB/s    0:00:00 (xfer#130, to-check=1553/1684)
unetbootin-linux-436
     4164548 100%    6.35MB/s    0:00:00 (xfer#131, to-check=1552/1684)
unetbootin-linux-442
     4174028 100%    4.93MB/s    0:00:00 (xfer#132, to-check=1551/1684)
.AbiSuite/
.Foxit/
rsync: recv_generator: mkdir "/media/sdb1/.AbiSuite" failed: Permission denied (13)
.TaskCoach/
*** Skipping any contents from this failed directory ***
.Trash-0/
rsync: recv_generator: mkdir "/media/sdb1/.Foxit" failed: Permission denied (13)
.Trash-1000/
*** Skipping any contents from this failed directory ***
.VirtualBox/
rsync: recv_generator: mkdir "/media/sdb1/.TaskCoach" failed: Permission denied (13)
.aMule/
*** Skipping any contents from this failed directory ***
.adobe/
rsync: recv_generator: mkdir "/media/sdb1/.Trash-0" failed: Permission denied (13)
.ailurus/
*** Skipping any contents from this failed directory ***
.audacity-data/
rsync: recv_generator: mkdir "/media/sdb1/.Trash-1000" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.VirtualBox" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.aMule" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.adobe" failed: Permission denied (13)
.cache/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.ailurus" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.audacity-data" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.cache" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: mkstemp "/media/sdb1/..ICEauthority.QeMY2c" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~.IDLT0p" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~~.H5u1ZC" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~~~.8GXgZP" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~~~~.s6KwY2" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~~~~~.oHiLZf" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ICEauthority~~~~~~.hAtN2s" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history.CXLR7F" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~.3BfsdT" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~~.O4E6i6" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~~~.Rctzpj" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~~~~.dFGbww" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~~~~~.6RESCJ" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_history~~~~~~.uepjKW" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_logout.mNxsV9" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_logout~.yV9B6m" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bash_logout~~.Ln3LhA" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bashrc.rBcWsN" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bashrc~.ZpZcE0" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bashrc~~.hhGDPd" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..bashrc~~~.rVM40q" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..data.FX2IeE" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..dmrc.pOrUyR" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..dmrc~.max6S4" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..dmrc~~.QyTidi" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..dmrc~~~.Ixxvxv" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..esd_auth.gsrIRI" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..esd_auth~.hvzVbW" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..esd_auth~~.whZ8v9" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock.vnGmQm" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~.UxBAaA" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~~.zKMOuN" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~~~.36d3O0" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~~~~.RqVh9d" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~~~~~.X9Swtr" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gksu.lock~~~~~~.V46LNE" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks.SWy17R" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~.0Whhs5" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~~.e9ehQi" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~~~.bnHhew" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~~~~.qtqiCJ" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~~~~~.lmFj0W" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..gtk-bookmarks~~~~~~.wMcloa" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..isomaster.tH0mMn" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..mailcap.ID5oaB" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..printer-groups.xml.ILvByO" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..profile.CYfOW1" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..profile~.kwg1kf" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..profile~~.7A7mKs" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..pulse-cookie.9zsJ9F" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..pulse-cookie~.NW45yT" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..pulse-cookie~~.sAWsY6" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..pychessconf.HxjQnk" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..qGorc.9yXNOx" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..rdata.Op9LfL" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.qzXaIY" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel.zNtAac" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~.M87iEp" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~~.kg8R8C" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~~~.qAZeEQ" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~~~~.5ENC93" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~~~~~.U9qEGh" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used.xbel~~~~~~.mBaHhv" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used~.TFokTI" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..recently-used~~.jRnYuW" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..registry.lHlK89" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..rsrc.IbQwMn" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..selected_editor.Z08NtB" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..sudo_as_admin_successful.RL15aP" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..sudo_as_admin_successful~.jsdoS2" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..text.uGEGzg" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..ubuntu-10.04-desktop-i386.iso.4Q2j5v.jllTnu" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..usbcreator.log.CkIjEP" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..usbcreator.log~.xVxBVa" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..usbcreator.log~~.TMtUow" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.Xq79SR" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old.JD2Nzd" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~.bCvJhz" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~~.TeKZ0U" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~~~.jusEKg" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~~~~.rOwEuC" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~~~~~.TKA7gY" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors.old~~~~~~.VP5rck" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~.j96KaG" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~~.NNxm91" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~~~.l7c07n" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~~~~.Xei97J" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~~~~~.vVox95" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/..xsession-errors~~~~~~.3Glhhs" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.App_Runner_0.2.deb.loNJDO" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.App_Runner_0.2.deb.1.qLLc0a" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.App_Runner_0.2.deb.2.9zEKmx" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.App_Runner_0.2.deb.3.jFTiJT" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.CERTIFICATE.bHkk7f" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.Darcy Library of Beulahtn.jpg.oIMoyC" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.Maxtor.sh.Yfpt3Y" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.Maxtor.sh~.DEyyyl" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.Results - FEBE 2010 01-09 17.13.43.html.eWHC6H" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.TaskCoach-0.71.0.tar.gz.K1vHE4" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.TaxFormsServlet.Qj7Yrr" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.WD.sh.0alhfO" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.WD.sh~.cUPz2a" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ailurus_10.01-0revision1_all.deb.pEDSPx" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.backup sources.list.Pb0lRU" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.bookmarks-2010-01-09.json.OUWPSh" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.debreate_0.6.2-3_all.deb.aux54E" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.du -ch.N55mi2" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.examples.desktop.3VXdyp" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.examples.desktop~.r6q5NM" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.firefox-3.6.tar.bz2.BjbX39" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.game.001.2Zn4ly" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.get-flash-videos_1.21-1_all.deb.Ng3bEW" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.installed-software.CN1NXk" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.launchpad-update.qJHzhJ" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.libflashplayer.so.tT7ME7" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.log.001.9Yh4ix" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.missfont.log.1OZlXW" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.pclinuxos-phoenix-xfce-2010.iso.J3ZDBm" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.picasa_3.0-current_i386.deb.rL1Nth" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.profileFx3{default}.fbu.lbO9De" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.pup-431.iso.q4hHCd" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.sqlite3.mtDtMk" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.sqlite3~.mmtgWr" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.taskcoach_0.77.0-1_all.deb.uBx35y" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.taskcoach_0.77.0-1_all.deb~.YUKCuG" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ubucompilator_0.0.1-1_all.english.version.deb.bcocTN" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ubucompilator_0.0.1-1_all.english.version.deb~.PTFplV" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ubuntu-10.04-desktop-i386.iso.j8nDN2" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ubuntu-10.04-rc-netbook-i386.iso.F6q5bX" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.ubuntu-files.PkAKPB" failed: Permission denied (13)
.chmsee/
rsync: mkstemp "/media/sdb1/.unetbootin-linux-436.NH8ptg" failed: Permission denied (13)
rsync: mkstemp "/media/sdb1/.unetbootin-linux-442.ypJXzV" failed: Permission denied (13)
rsync: recv_generator: mkdir "/media/sdb1/.chmsee" failed: Permission denied (13)
.compiz/
*** Skipping any contents from this failed directory ***
.config/
rsync: recv_generator: mkdir "/media/sdb1/.compiz" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.config" failed: Permission denied (13)
.cxchromium/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.cxchromium" failed: Permission denied (13)
.dbus/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.dbus" failed: Permission denied (13)
.debreate/
*** Skipping any contents from this failed directory ***
.denemo/
rsync: recv_generator: mkdir "/media/sdb1/.debreate" failed: Permission denied (13)
.dreamchess/
*** Skipping any contents from this failed directory ***
.eboard/
rsync: recv_generator: mkdir "/media/sdb1/.denemo" failed: Permission denied (13)
.euler/
*** Skipping any contents from this failed directory ***
.evolution/
rsync: recv_generator: mkdir "/media/sdb1/.dreamchess" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.eboard" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.euler" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.evolution" failed: Permission denied (13)
.fontconfig/
*** Skipping any contents from this failed directory ***
.gconf/
rsync: recv_generator: mkdir "/media/sdb1/.fontconfig" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.gconf" failed: Permission denied (13)
.gconfd/
*** Skipping any contents from this failed directory ***
.gegl-0.0/
rsync: recv_generator: mkdir "/media/sdb1/.gconfd" failed: Permission denied (13)
.gimp-2.6/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.gegl-0.0" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
.gnash/
rsync: recv_generator: mkdir "/media/sdb1/.gimp-2.6" failed: Permission denied (13)
.gnome-commander/
*** Skipping any contents from this failed directory ***
.gnome/
rsync: recv_generator: mkdir "/media/sdb1/.gnash" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.gnome-commander" failed: Permission denied (13)
.gnome2/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.gnome" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.gnome2" failed: Permission denied (13)
.gnome2_private/
*** Skipping any contents from this failed directory ***
.gnupg/
rsync: recv_generator: mkdir "/media/sdb1/.gnome2_private" failed: Permission denied (13)
.google/
*** Skipping any contents from this failed directory ***
.googleearth/
rsync: recv_generator: mkdir "/media/sdb1/.gnupg" failed: Permission denied (13)
.grsync/
*** Skipping any contents from this failed directory ***
.gstreamer-0.10/
rsync: recv_generator: mkdir "/media/sdb1/.google" failed: Permission denied (13)
.gvfs/
*** Skipping any contents from this failed directory ***
.hardinfo/
rsync: recv_generator: mkdir "/media/sdb1/.googleearth" failed: Permission denied (13)
.helix/
*** Skipping any contents from this failed directory ***
.hplip/
rsync: recv_generator: mkdir "/media/sdb1/.grsync" failed: Permission denied (13)
.icons/
*** Skipping any contents from this failed directory ***
.idlerc/
rsync: recv_generator: mkdir "/media/sdb1/.gstreamer-0.10" failed: Permission denied (13)
.java/
*** Skipping any contents from this failed directory ***
.kde/
rsync: recv_generator: mkdir "/media/sdb1/.gvfs" failed: Permission denied (13)
.kisotmp/
*** Skipping any contents from this failed directory ***
.local/
rsync: recv_generator: mkdir "/media/sdb1/.hardinfo" failed: Permission denied (13)
.lottanzb/
*** Skipping any contents from this failed directory ***
.macromedia/
rsync: recv_generator: mkdir "/media/sdb1/.helix" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.hplip" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.icons" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.idlerc" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.java" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.kde" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.kisotmp" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.local" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.lottanzb" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
.makagiga/
rsync: recv_generator: mkdir "/media/sdb1/.macromedia" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.makagiga" failed: Permission denied (13)
.mission-control/
*** Skipping any contents from this failed directory ***
.mozilla-thunderbird/
rsync: recv_generator: mkdir "/media/sdb1/.mission-control" failed: Permission denied (13)
.mozilla/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.mozilla-thunderbird" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.mozilla" failed: Permission denied (13)
.mplayer/
*** Skipping any contents from this failed directory ***
.nautilus/
rsync: recv_generator: mkdir "/media/sdb1/.mplayer" failed: Permission denied (13)
.nted/
*** Skipping any contents from this failed directory ***
.openoffice.org/
rsync: recv_generator: mkdir "/media/sdb1/.nautilus" failed: Permission denied (13)
.opera/
*** Skipping any contents from this failed directory ***
.picasa/
rsync: recv_generator: mkdir "/media/sdb1/.nted" failed: Permission denied (13)
.pki/
*** Skipping any contents from this failed directory ***
.pulse/
rsync: recv_generator: mkdir "/media/sdb1/.openoffice.org" failed: Permission denied (13)
.pychess/
*** Skipping any contents from this failed directory ***
.pycrust/
rsync: recv_generator: mkdir "/media/sdb1/.opera" failed: Permission denied (13)
.pyshell/
*** Skipping any contents from this failed directory ***
.qt/
rsync: recv_generator: mkdir "/media/sdb1/.picasa" failed: Permission denied (13)
.qtoctave/
*** Skipping any contents from this failed directory ***
.scid/
rsync: recv_generator: mkdir "/media/sdb1/.pki" failed: Permission denied (13)
.scribus/
*** Skipping any contents from this failed directory ***
.ssh/
rsync: recv_generator: mkdir "/media/sdb1/.pulse" failed: Permission denied (13)
.texmf-var/
*** Skipping any contents from this failed directory ***
.themes/
rsync: recv_generator: mkdir "/media/sdb1/.pychess" failed: Permission denied (13)
.thumbnails/
*** Skipping any contents from this failed directory ***
.tsclient/
rsync: recv_generator: mkdir "/media/sdb1/.pycrust" failed: Permission denied (13)
.tuxguitar-1.1/
*** Skipping any contents from this failed directory ***
.tuxpaint/
rsync: recv_generator: mkdir "/media/sdb1/.pyshell" failed: Permission denied (13)
.ubuntu-tweak/
*** Skipping any contents from this failed directory ***
.unison/
rsync: recv_generator: mkdir "/media/sdb1/.qt" failed: Permission denied (13)
.update-manager-core/
*** Skipping any contents from this failed directory ***
.update-notifier/
rsync: recv_generator: mkdir "/media/sdb1/.qtoctave" failed: Permission denied (13)
.wapi/
*** Skipping any contents from this failed directory ***
.wine/
rsync: recv_generator: mkdir "/media/sdb1/.scid" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.scribus" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.ssh" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.texmf-var" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.themes" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.thumbnails" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.tsclient" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.tuxguitar-1.1" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.tuxpaint" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.ubuntu-tweak" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.unison" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.update-manager-core" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.update-notifier" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
Desktop/
rsync: recv_generator: mkdir "/media/sdb1/.wapi" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/.wine" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/Desktop" failed: Permission denied (13)
Documents/
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/Documents" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
MSNBC Rachel Maddow (audio)/
Templates/
rsync: recv_generator: mkdir "/media/sdb1/MSNBC Rachel Maddow (audio)" failed: Permission denied (13)
broadcom-wl-4.80.53.0/
*** Skipping any contents from this failed directory ***
firefox/
rsync: recv_generator: mkdir "/media/sdb1/Templates" failed: Permission denied (13)
gpodder-downloads/
*** Skipping any contents from this failed directory ***
lost+found/
rsync: recv_generator: mkdir "/media/sdb1/broadcom-wl-4.80.53.0" failed: Permission denied (13)
pulse-backup/
*** Skipping any contents from this failed directory ***
scid/
rsync: recv_generator: mkdir "/media/sdb1/firefox" failed: Permission denied (13)

*** Skipping any contents from this failed directory ***
sent 2268021948 bytes  received 13190 bytes  21703685.53 bytes/sec
rsync: recv_generator: mkdir "/media/sdb1/gpodder-downloads" failed: Permission denied (13)
total size is 85639020064  speedup is 37.76
*** Skipping any contents from this failed directory ***
rsync: chgrp "/media/sdb1/lost+found" failed: Operation not permitted (1)
rsync: recv_generator: mkdir "/media/sdb1/pulse-backup" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/media/sdb1/scid" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]


```

I am thinking that since both drives work fine on netbook and both constantly unmount on laptop there would be some log or terminal command I could invoke to explain this problem and hopefully fix it. This is by far the most irritating problem with Ubuntu for me. I unfortunately don't have the knowledge needed to do this on my own.Thank you

---

