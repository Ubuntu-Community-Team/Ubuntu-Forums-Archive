---
title: "K3B &amp; Brasero refusing to burn DVD properly"
date: 2010-02-27
forum: General Help
---

### Post by BastardNamban on 2010-02-27
Using 8.04.

I created a system backup ISO with remastersys that's about 3.4 GB, and I've repeatedly had failure and about 4 coasters now with both K3b and Brasero trying to burn it. I even ditched the original ISO and made another- same problem.

I have always had problems burning discs in both programs, and of all the times I've tried to burn anything with either, I've gotten errors near the end of the data check stage, in verifying the data burned. I'm really tired of this, and I need this ISO perfect to reinstall my OS on a new laptop harddrive.

This time it's K3b. It burned successfully, but I get errors in the data verification stage. Here's what I got: ```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-27-generic
Devices
-----------------------
SONY DVD+-RW DW-D56A PDS7 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD+R

K3bDataTrackReader
-----------------------
reading sectors 0 to 1786914 with sector size 2048. Length: 1786915 sectors, 3659601920 bytes.
using buffer size of 64 blocks.
Problem while reading. Retrying from sector 1424896.
Problem while reading. Retrying from sector 1455872.
Problem while reading. Retrying from sector 1726144.
Read error in sector 1726192.
Read a total of 1726144 sectors (3535142912 bytes)

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 2.5x1352KBps.
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3659601920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    4030464/3659601920 ( 0.1%) @0.9x, remaining 423:15 RBU  99.8% UBU  81.0%
   15138816/3659601920 ( 0.4%) @2.4x, remaining 128:23 RBU 100.0% UBU  98.4%
   26279936/3659601920 ( 0.7%) @2.4x, remaining 80:38 RBU  97.9% UBU  98.4%
   37421056/3659601920 ( 1.0%) @2.4x, remaining 61:18 RBU 100.0% UBU  98.7%
   48529408/3659601920 ( 1.3%) @2.4x, remaining 52:05 RBU  99.6% UBU  98.4%
   59670528/3659601920 ( 1.6%) @2.4x, remaining 45:14 RBU 100.0% UBU  98.2%
   70811648/3659601920 ( 1.9%) @2.4x, remaining 40:32 RBU 100.0% UBU  98.2%
   81952768/3659601920 ( 2.2%) @2.4x, remaining 37:50 RBU 100.0% UBU  98.2%
   93093888/3659601920 ( 2.5%) @2.4x, remaining 35:07 RBU 100.0% UBU  98.2%
  104267776/3659601920 ( 2.8%) @2.4x, remaining 32:57 RBU 100.0% UBU  98.5%
  115408896/3659601920 ( 3.2%) @2.4x, remaining 31:44 RBU 100.0% UBU  98.4%
  126582784/3659601920 ( 3.5%) @2.4x, remaining 30:14 RBU 100.0% UBU  98.2%
  137756672/3659601920 ( 3.8%) @2.4x, remaining 28:58 RBU 100.0% UBU  98.2%
  148897792/3659601920 ( 4.1%) @2.4x, remaining 28:17 RBU 100.0% UBU  98.4%
  160071680/3659601920 ( 4.4%) @2.4x, remaining 27:19 RBU 100.0% UBU  97.3%
  171245568/3659601920 ( 4.7%) @2.4x, remaining 26:28 RBU 100.0% UBU  98.2%
  182419456/3659601920 ( 5.0%) @2.4x, remaining 26:03 RBU 100.0% UBU  98.4%
  193593344/3659601920 ( 5.3%) @2.4x, remaining 25:21 RBU 100.0% UBU  98.4%
  204800000/3659601920 ( 5.6%) @2.4x, remaining 24:44 RBU 100.0% UBU  98.4%
  215973888/3659601920 ( 5.9%) @2.4x, remaining 24:26 RBU 100.0% UBU  98.5%
  227180544/3659601920 ( 6.2%) @2.4x, remaining 23:55 RBU 100.0% UBU  98.4%
  238354432/3659601920 ( 6.5%) @2.4x, remaining 23:26 RBU 100.0% UBU  98.2%
  249561088/3659601920 ( 6.8%) @2.4x, remaining 23:13 RBU 100.0% UBU  98.5%
  260767744/3659601920 ( 7.1%) @2.4x, remaining 22:48 RBU 100.0% UBU  98.2%
  271974400/3659601920 ( 7.4%) @2.4x, remaining 22:25 RBU 100.0% UBU  98.7%
  283181056/3659601920 ( 7.7%) @2.4x, remaining 22:15 RBU 100.0% UBU  98.2%
  294387712/3659601920 ( 8.0%) @2.4x, remaining 21:54 RBU 100.0% UBU  98.4%
  305594368/3659601920 ( 8.4%) @2.4x, remaining 21:35 RBU 100.0% UBU  98.2%
  316801024/3659601920 ( 8.7%) @2.4x, remaining 21:27 RBU 100.0% UBU  98.4%
  328040448/3659601920 ( 9.0%) @2.4x, remaining 21:09 RBU 100.0% UBU  98.4%
  339247104/3659601920 ( 9.3%) @2.4x, remaining 20:52 RBU 100.0% UBU  98.2%
  350453760/3659601920 ( 9.6%) @2.4x, remaining 20:46 RBU 100.0% UBU  98.2%
  361693184/3659601920 ( 9.9%) @2.4x, remaining 20:30 RBU 100.0% UBU  98.2%
  372932608/3659601920 (10.2%) @2.4x, remaining 20:16 RBU 100.0% UBU  98.4%
  384139264/3659601920 (10.5%) @2.4x, remaining 20:10 RBU 100.0% UBU  98.4%
  395378688/3659601920 (10.8%) @2.4x, remaining 19:57 RBU 100.0% UBU  98.2%
  406618112/3659601920 (11.1%) @2.4x, remaining 19:52 RBU 100.0% UBU  98.2%
  417857536/3659601920 (11.4%) @2.4x, remaining 19:39 RBU 100.0% UBU  98.2%
  429096960/3659601920 (11.7%) @2.4x, remaining 19:26 RBU 100.0% UBU  98.2%
  440336384/3659601920 (12.0%) @2.4x, remaining 19:22 RBU 100.0% UBU  98.2%
  451575808/3659601920 (12.3%) @2.4x, remaining 19:10 RBU 100.0% UBU  98.2%
  462815232/3659601920 (12.6%) @2.4x, remaining 18:59 RBU 100.0% UBU  98.2%
  474087424/3659601920 (13.0%) @2.4x, remaining 18:55 RBU 100.0% UBU  98.2%
  485326848/3659601920 (13.3%) @2.4x, remaining 18:44 RBU 100.0% UBU  98.7%
  496599040/3659601920 (13.6%) @2.4x, remaining 18:34 RBU 100.0% UBU  98.2%
  507838464/3659601920 (13.9%) @2.4x, remaining 18:30 RBU 100.0% UBU  98.7%
  519110656/3659601920 (14.2%) @2.4x, remaining 18:21 RBU 100.0% UBU  99.0%
  530350080/3659601920 (14.5%) @2.4x, remaining 18:11 RBU 100.0% UBU  98.7%
  541622272/3659601920 (14.8%) @2.4x, remaining 18:08 RBU 100.0% UBU  98.4%
  552894464/3659601920 (15.1%) @2.4x, remaining 17:58 RBU 100.0% UBU  98.2%
  564133888/3659601920 (15.4%) @2.4x, remaining 17:49 RBU 100.0% UBU  98.2%
  575406080/3659601920 (15.7%) @2.4x, remaining 17:46 RBU 100.0% UBU  98.4%
  586678272/3659601920 (16.0%) @2.4x, remaining 17:38 RBU 100.0% UBU  98.8%
  597950464/3659601920 (16.3%) @2.4x, remaining 17:29 RBU 100.0% UBU  98.5%
  609222656/3659601920 (16.6%) @2.4x, remaining 17:26 RBU 100.0% UBU  98.4%
  620494848/3659601920 (17.0%) @2.4x, remaining 17:18 RBU 100.0% UBU  98.2%
  631767040/3659601920 (17.3%) @2.4x, remaining 17:10 RBU 100.0% UBU  98.2%
  643039232/3659601920 (17.6%) @2.4x, remaining 17:07 RBU 100.0% UBU  98.2%
  654311424/3659601920 (17.9%) @2.4x, remaining 16:59 RBU 100.1% UBU  98.2%
  665616384/3659601920 (18.2%) @2.4x, remaining 16:52 RBU 100.0% UBU  98.4%
  676888576/3659601920 (18.5%) @2.4x, remaining 16:49 RBU 100.0% UBU  98.4%
  688160768/3659601920 (18.8%) @2.4x, remaining 16:41 RBU 100.0% UBU  98.4%
  699465728/3659601920 (19.1%) @2.4x, remaining 16:34 RBU 100.0% UBU  98.2%
  710737920/3659601920 (19.4%) @2.4x, remaining 16:31 RBU  99.9% UBU  98.2%
  722042880/3659601920 (19.7%) @2.4x, remaining 16:24 RBU  99.3% UBU  98.4%
  733347840/3659601920 (20.0%) @2.4x, remaining 16:17 RBU 100.0% UBU  97.9%
  744620032/3659601920 (20.3%) @2.4x, remaining 16:14 RBU  99.7% UBU  98.2%
  755924992/3659601920 (20.7%) @2.4x, remaining 16:07 RBU 100.0% UBU  98.4%
  767197184/3659601920 (21.0%) @2.4x, remaining 16:01 RBU 100.0% UBU  98.4%
  778502144/3659601920 (21.3%) @2.4x, remaining 15:58 RBU  99.9% UBU  97.8%
  789807104/3659601920 (21.6%) @2.4x, remaining 15:51 RBU  99.8% UBU  98.2%
  801112064/3659601920 (21.9%) @2.4x, remaining 15:45 RBU 100.0% UBU  98.4%
  812417024/3659601920 (22.2%) @2.4x, remaining 15:42 RBU 100.0% UBU  98.2%
  823721984/3659601920 (22.5%) @2.4x, remaining 15:36 RBU  99.5% UBU  98.1%
  835026944/3659601920 (22.8%) @2.4x, remaining 15:30 RBU 100.0% UBU  98.4%
  846299136/3659601920 (23.1%) @2.4x, remaining 15:27 RBU 100.0% UBU  98.2%
  857636864/3659601920 (23.4%) @2.5x, remaining 15:21 RBU  99.9% UBU  98.5%
  868941824/3659601920 (23.7%) @2.4x, remaining 15:15 RBU 100.0% UBU  98.5%
  880246784/3659601920 (24.1%) @2.4x, remaining 15:12 RBU  99.9% UBU  98.8%
  891551744/3659601920 (24.4%) @2.4x, remaining 15:06 RBU 100.0% UBU  98.2%
  902856704/3659601920 (24.7%) @2.4x, remaining 15:00 RBU 100.0% UBU  98.2%
  914161664/3659601920 (25.0%) @2.4x, remaining 14:57 RBU 100.0% UBU  98.4%
  925499392/3659601920 (25.3%) @2.5x, remaining 14:52 RBU 100.0% UBU  98.2%
  936804352/3659601920 (25.6%) @2.4x, remaining 14:46 RBU 100.0% UBU  98.2%
  948109312/3659601920 (25.9%) @2.4x, remaining 14:43 RBU 100.0% UBU  98.2%
  959447040/3659601920 (26.2%) @2.5x, remaining 14:38 RBU 100.0% UBU  98.2%
  970752000/3659601920 (26.5%) @2.4x, remaining 14:32 RBU 100.0% UBU  98.2%
  982056960/3659601920 (26.8%) @2.4x, remaining 14:29 RBU 100.0% UBU  98.4%
  993394688/3659601920 (27.1%) @2.5x, remaining 14:24 RBU 100.0% UBU  98.5%
 1004699648/3659601920 (27.5%) @2.4x, remaining 14:18 RBU 100.0% UBU  98.2%
 1016037376/3659601920 (27.8%) @2.5x, remaining 14:16 RBU 100.0% UBU  98.2%
 1027375104/3659601920 (28.1%) @2.5x, remaining 14:10 RBU 100.0% UBU  99.0%
 1038680064/3659601920 (28.4%) @2.4x, remaining 14:05 RBU  99.9% UBU  98.2%
 1050017792/3659601920 (28.7%) @2.5x, remaining 14:02 RBU 100.0% UBU  98.2%
 1061322752/3659601920 (29.0%) @2.4x, remaining 13:57 RBU  99.6% UBU  98.5%
 1072660480/3659601920 (29.3%) @2.5x, remaining 13:52 RBU 100.0% UBU  98.2%
 1083998208/3659601920 (29.6%) @2.5x, remaining 13:49 RBU 100.0% UBU  98.4%
 1095335936/3659601920 (29.9%) @2.5x, remaining 13:44 RBU 100.0% UBU  98.7%
 1106673664/3659601920 (30.2%) @2.5x, remaining 13:38 RBU 100.0% UBU  98.4%
 1118011392/3659601920 (30.6%) @2.5x, remaining 13:36 RBU 100.0% UBU  98.1%
 1129349120/3659601920 (30.9%) @2.5x, remaining 13:31 RBU 100.0% UBU  98.1%
 1140686848/3659601920 (31.2%) @2.5x, remaining 13:26 RBU 100.0% UBU  98.4%
 1151991808/3659601920 (31.5%) @2.4x, remaining 13:23 RBU 100.0% UBU  98.1%
 1163329536/3659601920 (31.8%) @2.5x, remaining 13:18 RBU 100.0% UBU  98.4%
 1174700032/3659601920 (32.1%) @2.5x, remaining 13:13 RBU 100.0% UBU  98.2%
 1186004992/3659601920 (32.4%) @2.4x, remaining 13:10 RBU 100.0% UBU  98.5%
 1197375488/3659601920 (32.7%) @2.5x, remaining 13:05 RBU 100.0% UBU  98.4%
 1208713216/3659601920 (33.0%) @2.5x, remaining 13:00 RBU 100.0% UBU  98.2%
 1220050944/3659601920 (33.3%) @2.5x, remaining 12:57 RBU 100.0% UBU  98.5%
 1231388672/3659601920 (33.6%) @2.5x, remaining 12:52 RBU 100.0% UBU  98.2%
 1242726400/3659601920 (34.0%) @2.5x, remaining 12:48 RBU 100.0% UBU  97.6%
 1254064128/3659601920 (34.3%) @2.5x, remaining 12:45 RBU  99.0% UBU  98.2%
 1265434624/3659601920 (34.6%) @2.5x, remaining 12:40 RBU  99.9% UBU  98.2%
 1276772352/3659601920 (34.9%) @2.5x, remaining 12:35 RBU 100.0% UBU  98.4%
 1288110080/3659601920 (35.2%) @2.5x, remaining 12:32 RBU 100.0% UBU  98.2%
 1299480576/3659601920 (35.5%) @2.5x, remaining 12:28 RBU 100.0% UBU  98.2%
 1310818304/3659601920 (35.8%) @2.5x, remaining 12:23 RBU 100.0% UBU  98.2%
 1322156032/3659601920 (36.1%) @2.5x, remaining 12:20 RBU 100.0% UBU  98.4%
 1333526528/3659601920 (36.4%) @2.5x, remaining 12:16 RBU 100.0% UBU  98.4%
 1344864256/3659601920 (36.7%) @2.5x, remaining 12:11 RBU 100.0% UBU  98.2%
 1356234752/3659601920 (37.1%) @2.5x, remaining 12:08 RBU 100.0% UBU  98.2%
 1367572480/3659601920 (37.4%) @2.5x, remaining 12:04 RBU 100.0% UBU  98.4%
 1378942976/3659601920 (37.7%) @2.5x, remaining 11:59 RBU 100.0% UBU  98.2%
 1390280704/3659601920 (38.0%) @2.5x, remaining 11:56 RBU 100.0% UBU  98.4%
 1401651200/3659601920 (38.3%) @2.5x, remaining 11:52 RBU 100.0% UBU  98.2%
 1413021696/3659601920 (38.6%) @2.5x, remaining 11:47 RBU 100.0% UBU  98.4%
 1424359424/3659601920 (38.9%) @2.5x, remaining 11:44 RBU 100.0% UBU  98.4%
 1435729920/3659601920 (39.2%) @2.5x, remaining 11:40 RBU 100.0% UBU  98.5%
 1447067648/3659601920 (39.5%) @2.5x, remaining 11:35 RBU 100.0% UBU  98.2%
 1458438144/3659601920 (39.9%) @2.5x, remaining 11:32 RBU 100.0% UBU  98.2%
 1469808640/3659601920 (40.2%) @2.5x, remaining 11:28 RBU 100.0% UBU  98.2%
 1481146368/3659601920 (40.5%) @2.5x, remaining 11:23 RBU 100.0% UBU  98.4%
 1492516864/3659601920 (40.8%) @2.5x, remaining 11:20 RBU  99.8% UBU  98.2%
 1503887360/3659601920 (41.1%) @2.5x, remaining 11:16 RBU  99.8% UBU  98.5%
 1515257856/3659601920 (41.4%) @2.5x, remaining 11:12 RBU 100.0% UBU  98.5%
 1526595584/3659601920 (41.7%) @2.5x, remaining 11:09 RBU 100.0% UBU  98.8%
 1537998848/3659601920 (42.0%) @2.5x, remaining 11:04 RBU 100.0% UBU  98.2%
 1549336576/3659601920 (42.3%) @2.5x, remaining 11:00 RBU 100.0% UBU  98.5%
 1560707072/3659601920 (42.6%) @2.5x, remaining 10:57 RBU 100.0% UBU  98.2%
 1572077568/3659601920 (43.0%) @2.5x, remaining 10:53 RBU 100.0% UBU  98.7%
 1583448064/3659601920 (43.3%) @2.5x, remaining 10:49 RBU 100.0% UBU  98.8%
 1594818560/3659601920 (43.6%) @2.5x, remaining 10:46 RBU 100.0% UBU  98.2%
 1606189056/3659601920 (43.9%) @2.5x, remaining 10:41 RBU 100.0% UBU  98.4%
 1617559552/3659601920 (44.2%) @2.5x, remaining 10:37 RBU 100.0% UBU  98.2%
 1628930048/3659601920 (44.5%) @2.5x, remaining 10:34 RBU 100.0% UBU  98.4%
 1640300544/3659601920 (44.8%) @2.5x, remaining 10:30 RBU 100.0% UBU  98.2%
 1651671040/3659601920 (45.1%) @2.5x, remaining 10:26 RBU 100.0% UBU  98.2%
 1663041536/3659601920 (45.4%) @2.5x, remaining 10:23 RBU 100.0% UBU  98.4%
 1674412032/3659601920 (45.8%) @2.5x, remaining 10:18 RBU 100.0% UBU  98.2%
 1685782528/3659601920 (46.1%) @2.5x, remaining 10:14 RBU 100.0% UBU  98.4%
 1697153024/3659601920 (46.4%) @2.5x, remaining 10:11 RBU 100.0% UBU  98.2%
 1708523520/3659601920 (46.7%) @2.5x, remaining 10:07 RBU 100.0% UBU  98.2%
 1719926784/3659601920 (47.0%) @2.5x, remaining 10:03 RBU 100.0% UBU  98.4%
 1731297280/3659601920 (47.3%) @2.5x, remaining 10:00 RBU 100.0% UBU  98.2%
 1742667776/3659601920 (47.6%) @2.5x, remaining 9:56 RBU 100.0% UBU  98.2%
 1754038272/3659601920 (47.9%) @2.5x, remaining 9:52 RBU 100.0% UBU  98.4%
 1765408768/3659601920 (48.2%) @2.5x, remaining 9:49 RBU 100.0% UBU  98.2%
 1776812032/3659601920 (48.6%) @2.5x, remaining 9:44 RBU 100.0% UBU  98.1%
 1788182528/3659601920 (48.9%) @2.5x, remaining 9:40 RBU 100.0% UBU  98.1%
 1799553024/3659601920 (49.2%) @2.5x, remaining 9:37 RBU 100.0% UBU  98.2%
 1810923520/3659601920 (49.5%) @2.5x, remaining 9:33 RBU 100.0% UBU  98.4%
 1822326784/3659601920 (49.8%) @2.5x, remaining 9:30 RBU 100.0% UBU  98.4%
 1833697280/3659601920 (50.1%) @2.5x, remaining 9:26 RBU 100.0% UBU  98.4%
 1845067776/3659601920 (50.4%) @2.5x, remaining 9:22 RBU 100.0% UBU  98.2%
 1856471040/3659601920 (50.7%) @2.5x, remaining 9:19 RBU 100.0% UBU  98.2%
 1867841536/3659601920 (51.0%) @2.5x, remaining 9:15 RBU 100.0% UBU  98.2%
 1879244800/3659601920 (51.4%) @2.5x, remaining 9:11 RBU 100.0% UBU  98.2%
 1890615296/3659601920 (51.7%) @2.5x, remaining 9:08 RBU 100.0% UBU  98.4%
 1901985792/3659601920 (52.0%) @2.5x, remaining 9:04 RBU 100.0% UBU  98.4%
 1913389056/3659601920 (52.3%) @2.5x, remaining 9:00 RBU 100.0% UBU  98.2%
 1924759552/3659601920 (52.6%) @2.5x, remaining 8:57 RBU 100.0% UBU  98.2%
 1936162816/3659601920 (52.9%) @2.5x, remaining 8:53 RBU 100.0% UBU  98.4%
 1947533312/3659601920 (53.2%) @2.5x, remaining 8:49 RBU 100.0% UBU  98.2%
 1958936576/3659601920 (53.5%) @2.5x, remaining 8:46 RBU 100.0% UBU  98.4%
 1970339840/3659601920 (53.8%) @2.5x, remaining 8:42 RBU 100.0% UBU  98.2%
 1981710336/3659601920 (54.2%) @2.5x, remaining 8:38 RBU 100.0% UBU  98.2%
 1993113600/3659601920 (54.5%) @2.5x, remaining 8:35 RBU 100.0% UBU  98.4%
 2004484096/3659601920 (54.8%) @2.5x, remaining 8:31 RBU 100.0% UBU  98.4%
 2015887360/3659601920 (55.1%) @2.5x, remaining 8:27 RBU 100.0% UBU  98.2%
 2027290624/3659601920 (55.4%) @2.5x, remaining 8:24 RBU 100.0% UBU  98.4%
 2038661120/3659601920 (55.7%) @2.5x, remaining 8:20 RBU 100.0% UBU  98.1%
 2050064384/3659601920 (56.0%) @2.5x, remaining 8:16 RBU 100.0% UBU  98.2%
 2061467648/3659601920 (56.3%) @2.5x, remaining 8:13 RBU 100.0% UBU  98.2%
 2072838144/3659601920 (56.6%) @2.5x, remaining 8:09 RBU 100.0% UBU  98.2%
 2084241408/3659601920 (57.0%) @2.5x, remaining 8:05 RBU 100.0% UBU  98.2%
 2095644672/3659601920 (57.3%) @2.5x, remaining 8:02 RBU 100.0% UBU  98.2%
 2107015168/3659601920 (57.6%) @2.5x, remaining 7:58 RBU 100.0% UBU  98.4%
 2118418432/3659601920 (57.9%) @2.5x, remaining 7:54 RBU 100.0% UBU  98.4%
 2129821696/3659601920 (58.2%) @2.5x, remaining 7:51 RBU 100.0% UBU  98.2%
 2141192192/3659601920 (58.5%) @2.5x, remaining 7:47 RBU 100.0% UBU  98.4%
 2152628224/3659601920 (58.8%) @2.5x, remaining 7:43 RBU 100.0% UBU  98.2%
 2163998720/3659601920 (59.1%) @2.5x, remaining 7:40 RBU 100.0% UBU  98.2%
 2175401984/3659601920 (59.4%) @2.5x, remaining 7:36 RBU 100.0% UBU  98.4%
 2186805248/3659601920 (59.8%) @2.5x, remaining 7:32 RBU 100.0% UBU  98.2%
 2198208512/3659601920 (60.1%) @2.5x, remaining 7:29 RBU 100.0% UBU  98.2%
 2209611776/3659601920 (60.4%) @2.5x, remaining 7:25 RBU 100.0% UBU  98.2%
 2220982272/3659601920 (60.7%) @2.5x, remaining 7:21 RBU 100.0% UBU  98.2%
 2232385536/3659601920 (61.0%) @2.5x, remaining 7:18 RBU 100.0% UBU  98.4%
 2243788800/3659601920 (61.3%) @2.5x, remaining 7:14 RBU 100.0% UBU  98.2%
 2255192064/3659601920 (61.6%) @2.5x, remaining 7:10 RBU 100.0% UBU  98.2%
 2266595328/3659601920 (61.9%) @2.5x, remaining 7:07 RBU 100.0% UBU  98.2%
 2277998592/3659601920 (62.2%) @2.5x, remaining 7:03 RBU  99.8% UBU  98.2%
 2289401856/3659601920 (62.6%) @2.5x, remaining 7:00 RBU 100.0% UBU  98.4%
 2300805120/3659601920 (62.9%) @2.5x, remaining 6:56 RBU 100.0% UBU  98.2%
 2312208384/3659601920 (63.2%) @2.5x, remaining 6:53 RBU 100.0% UBU  98.4%
 2323611648/3659601920 (63.5%) @2.5x, remaining 6:49 RBU 100.0% UBU  98.2%
 2335014912/3659601920 (63.8%) @2.5x, remaining 6:46 RBU 100.0% UBU  98.1%
 2346418176/3659601920 (64.1%) @2.5x, remaining 6:42 RBU 100.0% UBU  98.8%
 2357821440/3659601920 (64.4%) @2.5x, remaining 6:38 RBU 100.0% UBU  98.2%
 2369257472/3659601920 (64.7%) @2.5x, remaining 6:35 RBU 100.0% UBU  98.2%
 2380660736/3659601920 (65.1%) @2.5x, remaining 6:31 RBU 100.0% UBU  98.2%
 2392064000/3659601920 (65.4%) @2.5x, remaining 6:27 RBU 100.0% UBU  98.4%
 2403467264/3659601920 (65.7%) @2.5x, remaining 6:24 RBU 100.0% UBU  98.2%
 2414870528/3659601920 (66.0%) @2.5x, remaining 6:20 RBU 100.0% UBU  98.2%
 2426273792/3659601920 (66.3%) @2.5x, remaining 6:17 RBU 100.0% UBU  98.2%
 2437677056/3659601920 (66.6%) @2.5x, remaining 6:13 RBU 100.0% UBU  97.6%
 2449080320/3659601920 (66.9%) @2.5x, remaining 6:10 RBU 100.0% UBU  98.2%
 2460483584/3659601920 (67.2%) @2.5x, remaining 6:06 RBU 100.0% UBU  98.1%
 2471886848/3659601920 (67.5%) @2.5x, remaining 6:03 RBU 100.0% UBU  98.2%
 2483322880/3659601920 (67.9%) @2.5x, remaining 5:59 RBU 100.0% UBU  98.2%
 2494726144/3659601920 (68.2%) @2.5x, remaining 5:55 RBU 100.0% UBU  98.4%
 2506129408/3659601920 (68.5%) @2.5x, remaining 5:52 RBU 100.0% UBU  98.5%
 2517532672/3659601920 (68.8%) @2.5x, remaining 5:48 RBU 100.0% UBU  98.7%
 2528935936/3659601920 (69.1%) @2.5x, remaining 5:45 RBU 100.0% UBU  98.2%
 2540371968/3659601920 (69.4%) @2.5x, remaining 5:41 RBU 100.0% UBU  98.4%
 2551775232/3659601920 (69.7%) @2.5x, remaining 5:38 RBU 100.0% UBU  98.7%
 2563178496/3659601920 (70.0%) @2.5x, remaining 5:34 RBU 100.0% UBU  98.8%
 2574614528/3659601920 (70.4%) @2.5x, remaining 5:31 RBU 100.0% UBU  98.2%
 2586017792/3659601920 (70.7%) @2.5x, remaining 5:27 RBU 100.0% UBU  98.4%
 2597421056/3659601920 (71.0%) @2.5x, remaining 5:23 RBU 100.0% UBU  98.5%
 2608824320/3659601920 (71.3%) @2.5x, remaining 5:20 RBU 100.0% UBU  98.7%
 2620260352/3659601920 (71.6%) @2.5x, remaining 5:16 RBU 100.0% UBU  98.7%
 2631663616/3659601920 (71.9%) @2.5x, remaining 5:13 RBU 100.0% UBU  98.7%
 2643099648/3659601920 (72.2%) @2.5x, remaining 5:09 RBU 100.0% UBU  98.8%
 2654502912/3659601920 (72.5%) @2.5x, remaining 5:06 RBU 100.0% UBU  98.2%
 2665906176/3659601920 (72.8%) @2.5x, remaining 5:02 RBU 100.0% UBU  98.5%
 2677342208/3659601920 (73.2%) @2.5x, remaining 4:59 RBU 100.0% UBU  98.7%
 2688745472/3659601920 (73.5%) @2.5x, remaining 4:55 RBU 100.0% UBU  98.8%
 2700181504/3659601920 (73.8%) @2.5x, remaining 4:52 RBU 100.0% UBU  98.2%
 2711584768/3659601920 (74.1%) @2.5x, remaining 4:48 RBU 100.0% UBU  98.5%
 2722988032/3659601920 (74.4%) @2.5x, remaining 4:45 RBU 100.0% UBU  98.2%
 2734424064/3659601920 (74.7%) @2.5x, remaining 4:41 RBU 100.0% UBU  98.8%
 2745827328/3659601920 (75.0%) @2.5x, remaining 4:38 RBU 100.0% UBU  98.2%
 2757263360/3659601920 (75.3%) @2.5x, remaining 4:34 RBU 100.0% UBU  98.1%
 2768666624/3659601920 (75.7%) @2.5x, remaining 4:30 RBU 100.0% UBU  98.2%
 2780102656/3659601920 (76.0%) @2.5x, remaining 4:27 RBU 100.0% UBU  98.2%
 2791505920/3659601920 (76.3%) @2.5x, remaining 4:24 RBU 100.0% UBU  98.5%
 2802909184/3659601920 (76.6%) @2.5x, remaining 4:20 RBU 100.0% UBU  98.2%
 2814345216/3659601920 (76.9%) @2.5x, remaining 4:17 RBU 100.0% UBU  98.4%
 2825781248/3659601920 (77.2%) @2.5x, remaining 4:13 RBU 100.0% UBU  98.7%
 2837184512/3659601920 (77.5%) @2.5x, remaining 4:09 RBU 100.0% UBU  98.5%
 2848620544/3659601920 (77.8%) @2.5x, remaining 4:06 RBU 100.0% UBU  98.2%
 2860023808/3659601920 (78.2%) @2.5x, remaining 4:02 RBU 100.0% UBU  98.2%
 2871459840/3659601920 (78.5%) @2.5x, remaining 3:59 RBU 100.0% UBU  98.5%
 2882895872/3659601920 (78.8%) @2.5x, remaining 3:56 RBU 100.0% UBU  98.2%
 2894299136/3659601920 (79.1%) @2.5x, remaining 3:52 RBU  99.9% UBU  98.2%
 2905702400/3659601920 (79.4%) @2.5x, remaining 3:48 RBU 100.0% UBU  98.2%
 2917138432/3659601920 (79.7%) @2.5x, remaining 3:45 RBU 100.0% UBU  98.4%
 2928574464/3659601920 (80.0%) @2.5x, remaining 3:41 RBU  99.9% UBU  98.2%
 2939977728/3659601920 (80.3%) @2.5x, remaining 3:38 RBU 100.0% UBU  97.9%
 2951413760/3659601920 (80.6%) @2.5x, remaining 3:34 RBU 100.0% UBU  98.2%
 2962817024/3659601920 (81.0%) @2.5x, remaining 3:31 RBU 100.0% UBU  98.1%
 2974253056/3659601920 (81.3%) @2.5x, remaining 3:27 RBU 100.0% UBU  98.2%
 2985689088/3659601920 (81.6%) @2.5x, remaining 3:24 RBU 100.0% UBU  98.4%
 2997092352/3659601920 (81.9%) @2.5x, remaining 3:20 RBU 100.0% UBU  98.4%
 3008528384/3659601920 (82.2%) @2.5x, remaining 3:17 RBU 100.0% UBU  97.3%
 3019931648/3659601920 (82.5%) @2.5x, remaining 3:14 RBU 100.0% UBU  98.2%
 3031367680/3659601920 (82.8%) @2.5x, remaining 3:10 RBU 100.0% UBU  98.2%
 3042803712/3659601920 (83.1%) @2.5x, remaining 3:06 RBU 100.0% UBU  98.2%
 3054239744/3659601920 (83.5%) @2.5x, remaining 3:03 RBU 100.0% UBU  98.4%
 3065643008/3659601920 (83.8%) @2.5x, remaining 2:59 RBU 100.0% UBU  98.2%
 3077079040/3659601920 (84.1%) @2.5x, remaining 2:56 RBU 100.0% UBU  98.2%
 3088482304/3659601920 (84.4%) @2.5x, remaining 2:53 RBU 100.0% UBU  98.2%
 3099918336/3659601920 (84.7%) @2.5x, remaining 2:49 RBU 100.0% UBU  98.4%
 3111354368/3659601920 (85.0%) @2.5x, remaining 2:45 RBU 100.0% UBU  98.1%
 3122790400/3659601920 (85.3%) @2.5x, remaining 2:42 RBU 100.0% UBU  98.2%
 3134193664/3659601920 (85.6%) @2.5x, remaining 2:39 RBU 100.0% UBU  98.1%
 3145629696/3659601920 (86.0%) @2.5x, remaining 2:35 RBU 100.0% UBU  98.2%
 3157065728/3659601920 (86.3%) @2.5x, remaining 2:32 RBU 100.0% UBU  98.2%
 3168501760/3659601920 (86.6%) @2.5x, remaining 2:28 RBU 100.0% UBU  98.7%
 3179905024/3659601920 (86.9%) @2.5x, remaining 2:25 RBU 100.0% UBU  98.2%
 3191341056/3659601920 (87.2%) @2.5x, remaining 2:21 RBU 100.0% UBU  98.2%
 3202777088/3659601920 (87.5%) @2.5x, remaining 2:18 RBU 100.0% UBU  98.1%
 3214213120/3659601920 (87.8%) @2.5x, remaining 2:14 RBU 100.0% UBU  98.2%
 3225616384/3659601920 (88.1%) @2.5x, remaining 2:11 RBU 100.0% UBU  98.2%
 3237052416/3659601920 (88.5%) @2.5x, remaining 2:07 RBU 100.0% UBU  97.8%
 3248488448/3659601920 (88.8%) @2.5x, remaining 2:04 RBU 100.0% UBU  98.2%
 3259924480/3659601920 (89.1%) @2.5x, remaining 2:00 RBU 100.0% UBU  98.2%
 3271327744/3659601920 (89.4%) @2.5x, remaining 1:57 RBU 100.0% UBU  98.2%
 3282763776/3659601920 (89.7%) @2.5x, remaining 1:53 RBU 100.0% UBU  98.2%
 3294199808/3659601920 (90.0%) @2.5x, remaining 1:50 RBU 100.0% UBU  98.2%
 3305635840/3659601920 (90.3%) @2.5x, remaining 1:46 RBU 100.0% UBU  98.2%
 3317071872/3659601920 (90.6%) @2.5x, remaining 1:43 RBU 100.0% UBU  98.2%
 3328507904/3659601920 (91.0%) @2.5x, remaining 1:40 RBU  99.9% UBU  98.2%
 3339911168/3659601920 (91.3%) @2.5x, remaining 1:36 RBU 100.0% UBU  98.2%
 3351347200/3659601920 (91.6%) @2.5x, remaining 1:33 RBU 100.0% UBU  98.2%
 3362783232/3659601920 (91.9%) @2.5x, remaining 1:29 RBU 100.0% UBU  98.2%
 3374219264/3659601920 (92.2%) @2.5x, remaining 1:26 RBU 100.0% UBU  98.2%
 3385655296/3659601920 (92.5%) @2.5x, remaining 1:22 RBU 100.0% UBU  98.2%
 3397091328/3659601920 (92.8%) @2.5x, remaining 1:19 RBU 100.0% UBU  98.2%
 3408527360/3659601920 (93.1%) @2.5x, remaining 1:15 RBU 100.0% UBU  98.2%
 3419963392/3659601920 (93.5%) @2.5x, remaining 1:12 RBU 100.0% UBU  98.2%
 3431366656/3659601920 (93.8%) @2.5x, remaining 1:08 RBU 100.0% UBU  98.2%
 3442802688/3659601920 (94.1%) @2.5x, remaining 1:05 RBU 100.0% UBU  98.2%
 3454238720/3659601920 (94.4%) @2.5x, remaining 1:02 RBU 100.0% UBU  98.2%
 3465674752/3659601920 (94.7%) @2.5x, remaining 0:58 RBU 100.0% UBU  98.2%
 3477110784/3659601920 (95.0%) @2.5x, remaining 0:55 RBU 100.0% UBU  98.2%
 3488546816/3659601920 (95.3%) @2.5x, remaining 0:51 RBU 100.0% UBU  98.2%
 3499982848/3659601920 (95.6%) @2.5x, remaining 0:48 RBU 100.0% UBU  98.2%
 3511418880/3659601920 (96.0%) @2.5x, remaining 0:44 RBU 100.0% UBU  98.1%
 3522854912/3659601920 (96.3%) @2.5x, remaining 0:41 RBU 100.0% UBU  98.1%
 3534290944/3659601920 (96.6%) @2.5x, remaining 0:37 RBU 100.0% UBU  98.1%
 3545726976/3659601920 (96.9%) @2.5x, remaining 0:34 RBU 100.0% UBU  98.4%
 3557163008/3659601920 (97.2%) @2.5x, remaining 0:30 RBU 100.0% UBU  98.2%
 3568599040/3659601920 (97.5%) @2.5x, remaining 0:27 RBU 100.0% UBU  98.2%
 3580035072/3659601920 (97.8%) @2.5x, remaining 0:23 RBU 100.0% UBU  98.1%
 3591438336/3659601920 (98.1%) @2.5x, remaining 0:20 RBU 100.0% UBU  98.2%
 3602874368/3659601920 (98.4%) @2.5x, remaining 0:17 RBU 100.0% UBU  98.2%
 3614310400/3659601920 (98.8%) @2.5x, remaining 0:13 RBU 100.0% UBU  98.2%
 3625779200/3659601920 (99.1%) @2.5x, remaining 0:10 RBU 100.0% UBU  98.4%
 3637215232/3659601920 (99.4%) @2.5x, remaining 0:06 RBU  66.8% UBU  98.2%
 3648651264/3659601920 (99.7%) @2.5x, remaining 0:03 RBU  32.7% UBU  98.2%
/dev/scd0: flushing cache
/dev/scd0: closing track
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1786915 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m 


```

I am even burning at the slowest speed for my drive- 2.4x. This is ridiculous!

Can anyone make sense of why I keep having this problem? I'm afraid to use an install disk for an OS when I can't verify the data, and I'm tired of making coasters every time I want to burn a disk!

Thanks.

---

### Post by bill516 on 2010-02-27
remastersys aside, have you been able to burn any iso successfully with that drive?  Have you got an Ubuntu iso handy and can you burn it?

The fact that both k3b and brasero are failing and at very low speeds causes me to be suspicious of the hardware involved.

In some fashion I think we need first to establish that your cd/dvd drive is in good working order.  Then we can turn to the software issues.

---

### Post by BastardNamban on 2010-02-28
I've been able to burn some things successfully, but it's touch and go. I never considered a mechanical flaw with the drive itself. How do you even test for that?

I can burn fine, it seems, but the errors always show up in md5 checksum verification stages. I just booted from the dvd iso I made, and things work as far as I can tell- some programs don't load, but it just says "gpl is not supported for this" or something.

I'll wait to hear more advice, but I may just try installing from the disk anyway. If things don't work, I'll just reinstall everything. The timing sucks here- I'm trying to put in a new HDD now, with the next LTS release only a month away. I need Autodesk Inventor LT working in an XP partition now to do schoolwork, and my current drive is too small to handle it.

---

### Post by ubunterooster on 2010-02-28
+1 hardware problem [get a differrent cd burning program from synaptic or ubuntu software center, just in case]

+1 trying to install anyway...

[I'm still up for getting a usb backup drive (or a friends old sata drive as you have an enclosure), copying os to that drive and then from that to new drive]

---

### Post by gordintoronto on 2010-12-29
How fast is your computer? How much memory? What else do you have running? Do you have a screensaver enabled? In the extreme case, I would even disconnect from the Internet to get a good burn, but that was on an old Windows system.

---

