---
title: "&quot;No space left on device&quot; error is itself an error."
date: 2009-07-22
forum: General Help
---

### Post by jenkinbr on 2009-07-22
I recently googled for and created a short script to rename jpg images on my computer, and stored it as ~/bin/rename.  The script runs fine, and works beautifully for my purposes, but I ran across some strange happenings while using it.  It ran through fine several times, then when I went to run it after a slight modification, the 'mv' command in the script bombs out with a "No space left on device" error.  I tried several more times, still a problem.  Unmounted and remounted drive - still problems.  The disk is not full, rather it is only 12% used.

```

[COLOR="Blue"]jenkinbr@jenkinbr:/media/TRAVELDRIVE$ cat /home/jenkinbr/bin/randrename [/COLOR]
#!/bin/bash

for fname in *.JPG
do
  mv "$fname" ${RANDOM}${RANDOM}.jpg
done

[COLOR="Blue"]jenkinbr@jenkinbr:/media/TRAVELDRIVE$ df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             17322592   4953624  11489008  31% /
tmpfs                   254608         0    254608   0% /lib/init/rw
varrun                  254608       120    254488   1% /var/run
varlock                 254608         0    254608   0% /var/lock
udev                    254608       180    254428   1% /dev
tmpfs                   254608        76    254532   1% /dev/shm
lrm                     254608      2192    252416   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1            154816488  79103028  67849244  54% /home
/dev/sda4             45199936  31578740  11325108  74% /media/backup
[COLOR="Cyan"]/dev/sdc1              1952544    221824   1730720  12% /media/TRAVELDRIVE[/COLOR]   ### This is the device in question.

[COLOR="Blue"]jenkinbr@jenkinbr:/media/TRAVELDRIVE$ ll ..[/COLOR]
total 48
drwxr-xr-x 4 root     root  4096 2009-01-16 17:05 backup
lrwxrwxrwx 1 root     root     6 2009-06-08 09:50 cdrom -> cdrom0
drwxr-xr-x 2 root     root  4096 2009-06-08 09:50 cdrom0
drwxr-xr-x 2 root     root  4096 2009-06-08 09:50 cdrom1
lrwxrwxrwx 1 root     root     7 2009-06-08 09:50 floppy -> floppy0
drwxr-xr-x 2 root     root  4096 2009-06-08 09:50 floppy0
[COLOR="Cyan"]drwx------ 3 jenkinbr root 16384 2009-07-22 20:24 TRAVELDRIVE[/COLOR]   ### This is the device in question.

[COLOR="Blue"]jenkinbr@jenkinbr:/media/TRAVELDRIVE$ ll[/COLOR]
total 218752
-rwx------ 1 jenkinbr root   452627 2009-07-21 08:13 1023115871.jpg
-rwx------ 1 jenkinbr root   465599 2009-07-21 08:07 102516085.jpg
-rwx------ 1 jenkinbr root   378838 2009-07-14 21:25 1039626234.jpg
-rwx------ 1 jenkinbr root   411809 2009-07-14 22:44 104768738.jpg
-rwx------ 1 jenkinbr root   322221 2004-10-15 09:23 1063929289.jpg
-rwx------ 1 jenkinbr root    46957 2000-07-18 20:35 1068010442.jpg
-rwx------ 1 jenkinbr root    53334 2000-08-12 23:29 1088329523.jpg
-rwx------ 1 jenkinbr root   682832 2009-07-21 08:10 109277024.jpg
-rwx------ 1 jenkinbr root  1122743 2009-01-15 11:33 1116518669.jpg
-rwx------ 1 jenkinbr root   468447 2009-07-21 08:10 112227291.jpg
-rwx------ 1 jenkinbr root   621713 2009-07-17 20:59 1154913207.jpg
-rwx------ 1 jenkinbr root   586548 2008-07-30 23:15 1189030299.jpg
-rwx------ 1 jenkinbr root   586548 2008-07-30 23:15 1223014959.jpg
-rwx------ 1 jenkinbr root   695151 2009-07-20 16:10 123206926.jpg
-rwx------ 1 jenkinbr root   511246 2009-07-14 21:18 1235410448.jpg
-rwx------ 1 jenkinbr root  1014948 2009-07-21 08:06 1245718677.jpg
-rwx------ 1 jenkinbr root  1291059 2008-01-01 23:44 1288415758.jpg
-rwx------ 1 jenkinbr root   406741 2009-07-14 22:43 128953570.jpg
-rwx------ 1 jenkinbr root   665395 2008-07-30 22:59 1294318294.jpg
-rwx------ 1 jenkinbr root   418891 2009-07-17 20:52 1305110797.jpg
-rwx------ 1 jenkinbr root   332114 2005-01-19 19:27 1331731894.jpg
-rwx------ 1 jenkinbr root   406334 2009-07-18 11:26 1335113974.jpg
-rwx------ 1 jenkinbr root   438396 2009-07-17 10:29 1346728310.jpg
-rwx------ 1 jenkinbr root   328224 2002-10-31 16:58 135392751.jpg
-rwx------ 1 jenkinbr root   455011 2003-01-01 01:20 1365404.JPG
-rwx------ 1 jenkinbr root   566968 2009-07-14 22:30 1382324517.jpg
-rwx------ 1 jenkinbr root  1110333 2009-07-18 20:34 139084502.jpg
-rwx------ 1 jenkinbr root   479402 2003-05-26 01:24 1457820652.jpg
-rwx------ 1 jenkinbr root   518499 2009-07-14 21:01 1506017745.jpg
-rwx------ 1 jenkinbr root   572045 2005-04-18 22:32 1513726615.jpg
-rwx------ 1 jenkinbr root   643355 2008-07-30 22:56 1522522031.jpg
-rwx------ 1 jenkinbr root   330440 2003-08-02 06:51 152926106.jpg
-rwx------ 1 jenkinbr root   325426 2003-08-02 07:42 1560914860.jpg
-rwx------ 1 jenkinbr root   286857 2009-07-21 08:08 1571918701.jpg
-rwx------ 1 jenkinbr root   390077 2005-04-18 22:33 157367484.jpg
-rwx------ 1 jenkinbr root   381285 2009-07-18 11:44 1620113825.jpg
-rwx------ 1 jenkinbr root   531725 2009-07-21 08:08 1621530827.jpg
-rwx------ 1 jenkinbr root   318416 2006-08-16 15:41 1623531498.jpg
-rwx------ 1 jenkinbr root   258928 2009-07-20 20:00 1672512437.jpg
-rwx------ 1 jenkinbr root     7078 2006-10-03 16:18 1678116164.jpg
-rwx------ 1 jenkinbr root   418811 2009-07-21 07:41 169130112.jpg
-rwx------ 1 jenkinbr root   338619 2005-04-16 18:16 1693619067.jpg
-rwx------ 1 jenkinbr root   324080 2005-11-15 14:56 1710526848.jpg
-rwx------ 1 jenkinbr root   745831 2008-07-30 23:02 1724829224.jpg
-rwx------ 1 jenkinbr root   473569 2009-07-17 15:11 173566674.jpg
-rwx------ 1 jenkinbr root   327802 2003-08-02 06:51 1736212177.jpg
-rwx------ 1 jenkinbr root   508449 2009-07-17 15:02 1746612224.jpg
-rwx------ 1 jenkinbr root   333747 2005-04-18 19:16 1747029704.jpg
-rwx------ 1 jenkinbr root   428914 2009-07-17 20:16 1776911063.jpg
-rwx------ 1 jenkinbr root   333372 2002-12-24 23:02 181855805.jpg
-rwx------ 1 jenkinbr root   332109 2005-05-27 21:34 182624604.jpg
-rwx------ 1 jenkinbr root   324633 2004-10-15 09:26 1873724139.jpg
-rwx------ 1 jenkinbr root   707399 2009-07-14 22:37 1874124164.jpg
-rwx------ 1 jenkinbr root  1459419 2008-07-30 23:04 187982961.jpg
-rwx------ 1 jenkinbr root   492832 2009-07-17 09:35 189249916.jpg
-rwx------ 1 jenkinbr root   532229 2009-07-18 11:46 1893711918.jpg
-rwx------ 1 jenkinbr root   440198 2009-07-17 15:14 18995412.jpg
-rwx------ 1 jenkinbr root   392595 2003-01-12 12:11 192585409.jpg
-rwx------ 1 jenkinbr root   536816 2009-07-18 11:47 19423243.jpg
-rwx------ 1 jenkinbr root   712094 2008-08-03 19:13 19512982.jpg
-rwx------ 1 jenkinbr root   407705 2009-07-17 14:25 1972326950.jpg
-rwx------ 1 jenkinbr root   386724 2008-08-03 19:06 2009817480.jpg
-rwx------ 1 jenkinbr root   386889 2009-07-18 11:33 201721865.jpg
-rwx------ 1 jenkinbr root   447572 2009-07-21 08:13 204336009.jpg
-rwx------ 1 jenkinbr root   332994 2005-05-27 21:45 2051016289.jpg
-rwx------ 1 jenkinbr root   555009 2008-07-30 22:57 2080810529.jpg
-rwx------ 1 jenkinbr root    72004 2000-12-26 21:21 21165743.jpg
-rwx------ 1 jenkinbr root   543833 2009-07-14 22:35 213412058.jpg
-rwx------ 1 jenkinbr root   320881 2009-07-18 11:36 2137331915.jpg
-rwx------ 1 jenkinbr root   492633 2009-07-14 22:56 2138011425.jpg
-rwx------ 1 jenkinbr root  1256049 2008-02-12 07:55 21424706.JPG
-rwx------ 1 jenkinbr root   342431 2009-07-18 12:11 2173323870.jpg
-rwx------ 1 jenkinbr root   476071 2009-07-21 08:21 2198720374.jpg
-rwx------ 1 jenkinbr root   442380 2009-07-17 20:30 220528281.jpg
-rwx------ 1 jenkinbr root   772945 2009-07-21 08:16 22430438.jpg
-rwx------ 1 jenkinbr root   548474 2009-07-14 22:49 2243722589.jpg
-rwx------ 1 jenkinbr root   853836 2009-07-14 22:33 224815254.jpg
-rwx------ 1 jenkinbr root   723457 2008-08-03 17:12 225863797.JPG
-rwx------ 1 jenkinbr root   637062 2009-07-21 08:09 228218885.jpg
-rwx------ 1 jenkinbr root   515401 2009-07-17 21:01 228620565.jpg
-rwx------ 1 jenkinbr root  1505861 2008-09-01 09:19 2308611994.jpg
-rwx------ 1 jenkinbr root   524733 2009-07-17 14:20 231506398.jpg
-rwx------ 1 jenkinbr root   282178 2009-01-26 07:24 2351025857.jpg
-rwx------ 1 jenkinbr root   270642 2004-11-20 20:59 237716540.jpg
-rwx------ 1 jenkinbr root   532254 2009-07-14 23:03 2378027121.jpg
-rwx------ 1 jenkinbr root   438756 2009-07-21 07:42 23788182.jpg
-rwx------ 1 jenkinbr root   326932 2005-05-27 21:42 2465112224.jpg
-rwx------ 1 jenkinbr root   264381 2003-07-31 23:05 251822438.jpg
-rwx------ 1 jenkinbr root   443306 2009-07-17 14:52 251976514.jpg
-rwx------ 1 jenkinbr root   441140 2009-07-18 11:21 2522131636.jpg
-rwx------ 1 jenkinbr root   347680 2009-07-17 09:33 2531515308.jpg
-rwx------ 1 jenkinbr root   400067 2009-07-17 20:40 2539224752.jpg
-rwx------ 1 jenkinbr root   466988 2008-08-05 09:36 2541816374.jpg
-rwx------ 1 jenkinbr root   629433 2009-07-17 15:18 2559616941.jpg
-rwx------ 1 jenkinbr root   592406 2008-07-30 23:05 2561814608.jpg
-rwx------ 1 jenkinbr root   387372 2009-07-20 20:16 2572724255.jpg
-rwx------ 1 jenkinbr root   572641 2009-07-18 11:38 257488972.jpg
-rwx------ 1 jenkinbr root   517324 2008-07-30 23:13 2578722328.jpg
-rwx------ 1 jenkinbr root   481947 2004-05-08 22:44 2596816644.jpg
-rwx------ 1 jenkinbr root   465904 2003-01-01 01:22 262941697.JPG
-rwx------ 1 jenkinbr root   322854 2005-05-27 19:23 2632411605.jpg
-rwx------ 1 jenkinbr root   327392 2005-05-27 21:34 2665422648.jpg
-rwx------ 1 jenkinbr root   702439 2009-07-21 08:03 2692128898.jpg
-rwx------ 1 jenkinbr root   506847 2009-07-18 11:23 2711318450.jpg
-rwx------ 1 jenkinbr root   758817 2009-07-20 20:11 2715425217.jpg
-rwx------ 1 jenkinbr root   656889 2009-07-21 08:06 2733310010.jpg
-rwx------ 1 jenkinbr root   725303 2009-07-21 21:50 2737327980.jpg
-rwx------ 1 jenkinbr root   682533 2009-07-21 08:02 2753114300.jpg
-rwx------ 1 jenkinbr root   595838 2008-07-30 23:00 2756420391.jpg
-rwx------ 1 jenkinbr root   743410 2008-07-30 23:01 275963346.jpg
-rwx------ 1 jenkinbr root   555009 2008-07-30 22:57 278421101.jpg
-rwx------ 1 jenkinbr root   484603 2009-07-21 08:20 2790314422.jpg
-rwx------ 1 jenkinbr root   405188 2009-07-17 20:15 282937142.jpg
-rwx------ 1 jenkinbr root   310426 2009-07-20 17:19 28316142.jpg
-rwx------ 1 jenkinbr root   519764 2009-07-21 08:01 284938211.jpg
-rwx------ 1 jenkinbr root   251816 2009-07-21 08:09 28512380.jpg
-rwx------ 1 jenkinbr root   381115 2009-07-17 10:13 288221643.jpg
-rwx------ 1 jenkinbr root   529362 2009-07-21 07:46 2888323591.jpg
-rwx------ 1 jenkinbr root    38792 2000-07-18 20:45 2906926980.jpg
-rwx------ 1 jenkinbr root   515302 2009-07-21 08:15 290956734.jpg
-rwx------ 1 jenkinbr root   502438 2009-07-21 07:45 2918119704.jpg
-rwx------ 1 jenkinbr root   352717 2009-07-21 08:14 2925312108.jpg
-rwx------ 1 jenkinbr root   889269 2008-08-05 09:30 292812293.jpg
-rwx------ 1 jenkinbr root   247997 2009-07-20 19:45 2965819897.jpg
-rwx------ 1 jenkinbr root  1151692 2009-07-18 20:37 297238743.jpg
-rwx------ 1 jenkinbr root   525120 2009-07-21 08:19 3020015990.jpg
-rwx------ 1 jenkinbr root   642733 2009-07-21 07:39 3024315770.jpg
-rwx------ 1 jenkinbr root    31810 2008-08-07 10:20 302987630.jpg
-rwx------ 1 jenkinbr root   596582 2009-07-17 14:21 3075018463.jpg
-rwx------ 1 jenkinbr root   322298 2009-07-20 20:09 3080523374.jpg
-rwx------ 1 jenkinbr root   637991 2008-07-30 23:12 3091723128.jpg
-rwx------ 1 jenkinbr root   529754 2009-07-21 21:52 3115321456.jpg
-rwx------ 1 jenkinbr root   560314 2009-07-21 08:14 3121415974.jpg
-rwx------ 1 jenkinbr root  1022410 2009-07-21 08:02 31254755.jpg
-rwx------ 1 jenkinbr root   469524 2009-07-17 14:53 3131618045.jpg
-rwx------ 1 jenkinbr root   745253 2009-07-18 12:04 3151511854.jpg
-rwx------ 1 jenkinbr root   597226 2008-07-30 23:03 315715459.jpg
-rwx------ 1 jenkinbr root   381884 2007-05-18 19:28 3169124644.jpg
-rwx------ 1 jenkinbr root   511588 2008-07-30 23:03 3214321296.jpg
-rwx------ 1 jenkinbr root   647489 2008-07-30 23:04 323447209.jpg
-rwx------ 1 jenkinbr root   647123 2009-07-20 16:13 34809477.jpg
-rwx------ 1 jenkinbr root    46582 2008-08-07 10:20 365910266.jpg
-rwx------ 1 jenkinbr root   279394 2009-01-26 07:24 369716854.jpg
-rwx------ 1 jenkinbr root   600974 2008-07-30 22:57 371211110.jpg
-rwx------ 1 jenkinbr root   583867 2009-07-20 19:22 37911491.jpg
-rwx------ 1 jenkinbr root   145184 2009-07-18 13:05 385012131.jpg
-rwx------ 1 jenkinbr root   599619 2009-07-14 22:22 411416125.jpg
-rwx------ 1 jenkinbr root   506104 2008-07-30 22:55 425414784.jpg
-rwx------ 1 jenkinbr root   529646 2009-07-14 21:27 430126095.jpg
-rwx------ 1 jenkinbr root   461223 2004-10-14 20:18 4381263.JPG
-rwx------ 1 jenkinbr root   434272 2009-07-14 22:26 4479270.jpg
-rwx------ 1 jenkinbr root   443031 2009-07-21 07:43 455927827.jpg
-rwx------ 1 jenkinbr root    22439 2006-10-03 16:13 45829905.jpg
-rwx------ 1 jenkinbr root   679882 2008-07-30 23:12 51632143.jpg
-rwx------ 1 jenkinbr root   674000 2009-07-21 08:12 54029380.jpg
-rwx------ 1 jenkinbr root   337363 2009-07-18 12:12 546022137.jpg
-rwx------ 1 jenkinbr root    43244 2008-08-08 07:09 5532536.jpg
-rwx------ 1 jenkinbr root   484301 2009-07-14 22:58 565927345.jpg
-rwx------ 1 jenkinbr root   665742 2009-07-18 20:48 597927219.jpg
-rwx------ 1 jenkinbr root   523824 2009-07-14 23:05 606916883.jpg
-rwx------ 1 jenkinbr root   327251 2009-07-18 20:40 607030108.jpg
-rwx------ 1 jenkinbr root   397702 2009-07-18 10:37 63773284.jpg
-rwx------ 1 jenkinbr root   513424 2009-07-14 21:29 66159625.jpg
-rwx------ 1 jenkinbr root   494841 2009-07-14 22:55 66581112.jpg
-rwx------ 1 jenkinbr root   544947 2009-07-21 08:05 67828240.jpg
-rwx------ 1 jenkinbr root   407476 2009-07-17 20:42 6795169.jpg
-rwx------ 1 jenkinbr root   243367 2006-04-16 13:05 69943797.jpg
-rwx------ 1 jenkinbr root   526675 2004-05-08 22:44 70207362.jpg
-rwx------ 1 jenkinbr root   339914 2003-08-02 08:44 709713784.jpg
-rwx------ 1 jenkinbr root   384678 2009-07-18 10:40 76769464.jpg
-rwx------ 1 jenkinbr root   564646 2008-07-30 23:00 78672167.jpg
-rwx------ 1 jenkinbr root   335673 2005-07-12 20:06 811722701.jpg
-rwx------ 1 jenkinbr root   663410 2008-07-30 22:59 81253654.jpg
-rwx------ 1 jenkinbr root   406979 2009-07-14 20:58 819123568.jpg
-rwx------ 1 jenkinbr root   276228 2005-05-20 14:06 83729180.jpg
-rwx------ 1 jenkinbr root   884153 2009-01-12 14:41 87586725.JPG
-rwx------ 1 jenkinbr root   456101 2009-07-17 20:41 88693717.jpg
-rwx------ 1 jenkinbr root   573210 2008-07-30 22:56 890416317.jpg
-rwx------ 1 jenkinbr root   654840 2009-07-17 15:16 934821454.jpg
-rwx------ 1 jenkinbr root  1100645 2008-08-03 19:14 970418435.jpg
-rwx------ 1 jenkinbr root  1315241 2008-06-03 20:09 hfagdgas.JPG
-rwx------ 1 jenkinbr root   420022 2003-05-26 01:29 easter3.JPG
-rwx------ 1 jenkinbr root  1305616 2008-03-05 22:34 Family1.JPG
-rwx------ 1 jenkinbr root  3686454 2004-01-15 17:50 kids xmas-03A.BMP
-rwx------ 1 jenkinbr root  3686454 2004-01-15 17:51 kids xmas-03e.BMP
-rwx------ 1 jenkinbr root 12412923 2004-10-08 11:23 ddddd.psd
-rwx------ 1 jenkinbr root  3686454 2004-01-15 17:52 dkdkd xmas-03b.BMP
-rwx------ 1 jenkinbr root  1240390 2009-01-03 12:14 MEX118.JPG
-rwx------ 1 jenkinbr root   466996 2003-01-01 00:10 MEX163.JPG
-rwx------ 1 jenkinbr root  1616477 2009-01-06 05:49 MEX326a.JPG
-rwx------ 1 jenkinbr root  1375198 2009-01-06 09:26 MEX329a.JPG
-rwx------ 1 jenkinbr root  1403739 2009-01-07 11:39 MEX363.JPG
-rwx------ 1 jenkinbr root   980658 2009-01-12 13:14 MEX409.JPG
-rwx------ 1 jenkinbr root   951610 2009-01-12 13:15 MEX414.JPG
-rwx------ 1 jenkinbr root  1249079 2009-01-03 05:39 MEX63.JPG
-rwx------ 1 jenkinbr root  2506113 2009-01-03 05:47 MEX65.JPG
-rwx------ 1 jenkinbr root  1240799 2009-01-03 11:18 MEX99a.JPG
-rwx------ 1 jenkinbr root  1183559 2009-01-03 11:18 MEX99.JPG
-rwx------ 1 jenkinbr root  1196228 2008-06-03 20:08 fskdafja.JPG
-rwx------ 1 jenkinbr root 20683822 2004-10-08 11:25 p17.psd
-rwx------ 1 jenkinbr root 33150104 2004-10-08 11:29 p18.psd
-rwx------ 1 jenkinbr root 23810993 2004-10-08 11:31 p19.psd
-rwx------ 1 jenkinbr root  3686456 2004-03-08 20:42 p24.BMP
-rwx------ 1 jenkinbr root   341863 2007-08-15 19:19 p4.JPG
-rwx------ 1 jenkinbr root  1194461 2008-02-12 11:30 p6.JPG
-rwx------ 1 jenkinbr root  1504506 2009-07-21 21:54 PICT0261a.JPG
-rwx------ 1 jenkinbr root  3686454 2003-05-18 22:53 blah.BMP
drwx------ 2 jenkinbr root    32768 2009-07-22 20:07 wedding

[COLOR="Blue"]jenkinbr@jenkinbr:/media/TRAVELDRIVE$ randrename[/COLOR]
mv: cannot move `Dale&Mick.JPG' to `918731199.JPG': No space left on device
mv: cannot move `easter3.JPG' to `212618234.JPG': No space left on device
mv: cannot move `Family1.JPG' to `302986111.JPG': No space left on device
mv: cannot move `MEX118.JPG' to `319391399.JPG': No space left on device
mv: cannot move `MEX163.JPG' to `2483919321.JPG': No space left on device
mv: cannot move `MEX326a.JPG' to `596931570.JPG': No space left on device
mv: cannot move `MEX329a.JPG' to `2431831315.JPG': No space left on device
mv: cannot move `MEX363.JPG' to `1744814554.JPG': No space left on device
mv: cannot move `MEX409.JPG' to `2644522930.JPG': No space left on device
mv: cannot move `MEX414.JPG' to `112417632.JPG': No space left on device
mv: cannot move `MEX63.JPG' to `3021329046.JPG': No space left on device
mv: cannot move `MEX65.JPG' to `2199011513.JPG': No space left on device
mv: cannot move `MEX99a.JPG' to `317491826.JPG': No space left on device
mv: cannot move `MEX99.JPG' to `656212960.JPG': No space left on device
mv: cannot move `dafsdfa.JPG' to `2836011693.JPG': No space left on device
mv: cannot move `p4.JPG' to `1424829599.JPG': No space left on device
mv: cannot move `p6.JPG' to `2952914694.JPG': No space left on device
mv: cannot move `PICT0261a.JPG' to `175694188.JPG': No space left on device

```

command run is in [COLOR="Blue"]BLUE[/COLOR]
Command output is in WHITE
df and ll /media output pertaining to the effected device is in [COLOR="Cyan"]CYAN[/COLOR]

This one has me baffeled.


EDIT: A reboot does NOT help.

---

### Post by michy99 on 2009-07-22
Maybe there is a hidden trash file on the drive.```
ls -la /media/TRAVELDRIVE
```

---

### Post by jenkinbr on 2009-07-22
> **michy99 said:**
> Maybe there is a hidden trash file on the drive.```
ls -la /media/TRAVELDRIVE
```
Nope

---

### Post by michy99 on 2009-07-22
What does the drive look like in gparted?

---

