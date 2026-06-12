---
title: "moving /home directory - Can't figure it out"
date: 2010-07-16
forum: General Help
---

### Post by Ezrie on 2010-07-16
Hi,

I am trying to move my home directory from my install partition to a new partition.  I cloned my installation from a previous ~78 gb HD using g4l to a new 250 GB drive.  Now that I am using the new drive i created a new partition to used for files called "files".  New partition is sda3 and the boot partition is sd1.  I am trying to follow this guide [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")  but i am having no success.  The output of: ```
find . -depth -print0 | cpio --null --sparse -pvd /media/sda3

``` is ```

pio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1381.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1336.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1387.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1497.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1360.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1504.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1561.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1479.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1368.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1378.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1250.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1459.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1303.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1366.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1492.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1458.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1416.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1520.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1428.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1559.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1379.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1350.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1405.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1377.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1511.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1519.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1374.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1516.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1326.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1532.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1424.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1395.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1333.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1327.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1562.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1274.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1474.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1393.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1278.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1371.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1324.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1495.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1403.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1410.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1493.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1314.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1406.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1420.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1533.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1432.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1272.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1275.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1550.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1460.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1277.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1477.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1329.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1373.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1509.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1391.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1426.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1382.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/bd14ad3337336b1363abb695dc12bb38-backup.db: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1546.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1491.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1570.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/80e00fbadb8210e68414bfd0638fa88d-backup.db: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1480.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1465.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1542.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1407.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1464.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1353.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1451.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1463.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1547.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1380.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1290.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1306.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1392.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1389.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1415.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1385.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1543.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1435.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1445.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1322.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1447.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1408.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1444.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1489.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1293.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1339.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1553.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1490.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1287.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1308.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1304.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1538.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1436.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1527.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1296.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1323.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1565.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1439.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1438.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1548.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1452.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/bd14ad3337336b1363abb695dc12bb38-backup.db-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1503.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1313.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1294.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1443.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1425.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1355.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1535.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cache.db: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1468.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1417.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1388.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1433.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1467.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1362.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1359.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1485.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1544.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1248.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1299.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1496.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1513.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1289.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1281.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1518.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1354.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1319.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1568.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1413.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1356.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1466.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1252.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1478.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1461.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1342.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1351.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1567.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1430.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1454.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1419.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1386.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1394.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1557.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-713.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1401.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1343.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1469.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1409.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1312.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1280.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1348.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1526.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1522.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1525.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1344.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1288.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1449.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1370.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1534.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1300.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1301.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1337.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1383.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1505.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1328.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cache.db-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1448.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1484.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1335.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1481.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1298.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1253.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1488.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1457.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1399.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1450.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1429.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1440.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1402.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1487.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1283.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1285.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1341.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1501.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1307.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1331.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1517.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1291.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1500.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1471.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1357.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1551.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1560.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1506.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1321.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1352.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1364.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1309.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1273.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1297.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1390.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1549.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1455.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1441.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1276.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1292.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1569.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1255.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1537.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1400.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1302.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1510.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1508.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1558.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1476.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1414.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1418.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1369.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1499.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1422.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1552.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1521.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1498.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1442.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-725.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1315.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1361.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1311.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1345.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1446.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1363.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1263.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1502.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1566.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1347.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1404.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1545.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1421.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1358.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1260.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1462.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1384.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1185.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1251.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1434.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1486.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1338.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1330.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1334.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1483.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1411.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1346.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1472.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1431.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1423.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1305.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/80e00fbadb8210e68414bfd0638fa88d-backup.db-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1284.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1529.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1295.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1316.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1398.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1564.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1375.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1470.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1524.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1515.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1556.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1539.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1427.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1541.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1456.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1286.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1531.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1554.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1372.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1540.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1310.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1555.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1320.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files/cf-1282.tmp: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us/Files: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache/jd2-a114b643324c576f1c36e3f17a9043f4-us: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/cache: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/junglediskmonitor-settings.xml: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk/jungledisk-settings.xml: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.jungledisk: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.esd_auth: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.ssh/authorized_keys2: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.ssh: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/ubuntu-tweak/ubuntu-tweak.log: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/ubuntu-tweak/appcenter: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/ubuntu-tweak: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/user-dirs.locale: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/autostart/plasma-desktop.desktop: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/autostart/plasma-netbook.desktop: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/autostart: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/kde4-applications-merged/cxmenu-cxoffice-d8129a63-dcca-4cef-831c-e7d388de8b52.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/kde4-applications-merged: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/settings.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/wine-Programs-Broderbund-Mavis Beacon Teaches Typing Platinum 20-Uninstall Mavis Beacon Teaches Typing Platinum 20.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/cxmenu-cxoffice-d8129a63-dcca-4cef-831c-e7d388de8b52.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/wine-Programs-Broderbund-Mavis Beacon Teaches Typing Platinum 20-Mavis Beacon Teaches Typing Platinum 20.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/wine-Programs-Broderbund-Mavis Beacon Teaches Typing Platinum 20-View Readme.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/wine-Programs-Broderbund-Mavis Beacon Teaches Typing Platinum 20-View Mavis Beacon Teaches Typing User Guide.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged/wine-Programs-Broderbund-Mavis Beacon Teaches Typing Platinum 20-Register Mavis Beacon Teaches Typing Platinum 20.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications-merged: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus/applications.menu: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/menus: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/vlc/vlc-qt-interface.conf: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/vlc/vlcrc: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/vlc: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/Google/GoogleEarthPlus.conf: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/Google: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/gtk-2.0/gtkfilechooser.ini: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/gtk-2.0: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Visited Links: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Thumbnails-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Last Tabs: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/History-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Current Tabs: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Last Session: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/History: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Current Session: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Thumbnails: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/firsttimesync.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/xmarks-global.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/foxmarks-nodes.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/_locales/en/messages.json: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/_locales/en: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/_locales: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/browseraction.html~: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/background.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/foxmarks-command.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/serp.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/syncprofile.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/authdialog.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/foxmarks-utils.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/foxmarks-network.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/popupdialog.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/setupwizardinsert.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-bg-selected.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-32.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/status-active.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-icons.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-macosx-bg-sel.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-discovery.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-general.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-active.ico: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-good.ico: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/loading.gif: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-bg-hover.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-advanced.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/status-good.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-macosx-bg.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-restore.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-16.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/status-error.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-bg.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-48.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/computer.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/browser_firefox.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-types.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/browser_chrome.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-error.ico: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/loading-bar.gif: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/pane-selector-profiles_TEMP.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-browseraction.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/generic-favicon.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-128.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks-dirty.ico: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/browser_safari.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/xmarks_bug.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/status-dirty.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/status-none.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images/browser_ie.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/images: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/manifest.json: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/Base64.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/settings.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/xmarks-chromemarks.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/js/jquery-ui-1.8.custom.min.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/js/jquery-1.4.2.min.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/js: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/jquery-ui-1.8.custom.css: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_808080_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_eeeeee_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_inset-soft_15_2b2922_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-soft_25_67b021_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_glass_55_fcf0ba_1x400.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-hard_100_f5f3e5_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_8dc262_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_ffffff_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_cd0a0a_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-hard_15_459e00_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-hard_100_fafaf4_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-soft_95_ffedad_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_highlight-hard_95_cccccc_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-bg_gloss-wave_100_ece8da_500x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images/ui-icons_847e71_256x240.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street/images: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css/south-street: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery/css: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/jquery: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/browseraction.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10/foxmarks-core.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla/0.7.10: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/ajpgkpeckebdhofmmjfgcjjiiejpodla: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/icon_48_48.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/icon_19_19.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/background.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/icon_128_128.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/icon_32_32.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/sessions.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/manifest.json: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3/icon_16_16.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi/0.3: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/bbcnbpafconjjigibnhbfmmgdbbkcjfi: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/popup.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icon_play.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/flashblock.css: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icons/icon16.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icons/icon128.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icons/icon48.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icons/icon32.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icons: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/background.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/upgrade.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/chromelib.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/icon_play_sl.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/allowed.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/slblock.css: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/prefs.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/blocked.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/disabled.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/images/menuItemBGOver.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/images/separator.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/images/panelBG.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/images/menuItemBG.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/images: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/options.css: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/core.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/custom.css: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_highlight-soft_45_5f5964_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_highlight-soft_100_dcd9de_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_gloss-wave_30_3d3644_500x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_highlight-soft_25_30273a_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_flat_55_994d53_40x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_flat_55_fafafa_40x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_flat_0_aaaaaa_40x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_highlight-soft_100_eae6ea_1x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images/ui-bg_flat_0_eeeeee_40x100.png: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/images: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options/ui.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/options.html: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/manifest.json: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30/content.js: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl/0.9.30: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions/gofhjkjmkpinhpoiabjplobcaignabnl: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extensions: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Archived History: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Web Data: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Bookmarks: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/History Index 2010-07-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Extension Cookies: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Preferences: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/History Index 2010-07: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Cookies: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_www.hulu.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_revision3.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_maketecheasier.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_mashable.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_today.msnbc.msn.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_techcrunch.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/chrome-extension_ajpgkpeckebdhofmmjfgcjjiiejpodla_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/chrome-extension_bbcnbpafconjjigibnhbfmmgdbbkcjfi_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/http_www.howtoforge.com_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage/chrome-extension_gofhjkjmkpinhpoiabjplobcaignabnl_0.localstorage: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Local Storage: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Web Data-journal: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/databases/chrome-extension_ajpgkpeckebdhofmmjfgcjjiiejpodla_0/1: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/databases/chrome-extension_ajpgkpeckebdhofmmjfgcjjiiejpodla_0: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/databases/Databases.db: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/databases: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default/Bookmarks.bak: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Default: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: K-Laptop-1880: Cannot create symlink to `/dev/sda3//./.config/google-chrome/SingletonLock': Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Dictionaries/en-US-1-2.bdic: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Dictionaries: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/SingletonSocket: Cannot mknod: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Local State: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Safe Browsing Bloom Filter 2: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/Safe Browsing Bloom: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome/First Run: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/google-chrome: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/qtcurve/gtk-icons: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/qtcurve: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/Trolltech.conf: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/user-dirs.dirs: Cannot open: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/gnome-session/saved-session: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config/gnome-session: Cannot stat: Not a directory
cpio: `/dev/sda3' exists but is not a directory
cpio: /dev/sda3//./.config: Cannot stat: Not a directory
0 blocks

```

Sorry for the long post.  Can anyone help. A screenshot of the way gparted sees my partitions is attached.

---

### Post by pbrane on 2010-07-16
*/media/sda3* isn't a directory. How did you mount your new partition? I'm not sure but looking at your gparted screenie maybe you should cpio to /media/Files.

---

### Post by Ezrie on 2010-07-16
> **pbrane said:**
> */media/sda3* isn't a directory. How did you mount your new partition? I'm not sure but looking at your gparted screenie maybe you should cpio to /media/Files.

I mounted it using gparted and gave it the label "files".  AM answering the right question?

using /media/Files did it.

I used pysdm to remount the drive before proceeding.

Thanks

---

### Post by Ezrie on 2010-07-16
> **Ezrie said:**
> I mounted it using gparted and gave it the label "files".  AM answering the right question?

using /media/Files did it.

I used pysdm to remount the drive before proceeding.

Thanks

I actually hosed the system.  Reinstalling

---

### Post by dcstar on 2010-07-17
Do not use 5 year old HOWTOs with comments telling the author to fix basic errors in it (which still remain unfixed).

Search out up to date instructions that will have more chance of succeeding.

---

### Post by Ezrie on 2010-07-18
> **dcstar said:**
> Do not use 5 year old HOWTOs with comments telling the author to fix basic errors in it (which still remain unfixed).

Search out up to date instructions that will have more chance of succeeding.

Agreed.  But, this was the best one I found.  Could you point me in the direction of a better one please?  I would really appreciate it.

---

### Post by potat on 2010-07-18
I like this tutorial:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This might help too:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

