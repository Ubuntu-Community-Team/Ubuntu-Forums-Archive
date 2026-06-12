---
title: "QGIS 1.7 in 10.04 Lucid MrSid ... (AGAIN AGAIN)"
date: 2011-06-18
forum: General Help
---

### Post by BigBaka on 2011-06-18
It what appears to be a continuing state of deja vu, I'm once again posting a request for assistance in getting Mr Sid files working in QGIS, albeit with updated versions of the same program... 

This morning QGIS updated to version 1.7.0 on Lucid LTS. Although I could never get Mr Sid files up and running on my [previous version update]("http://ubuntuforums.org/showthread.php?t=1656579&highlight=QGIS&page=2") I thought this might be a timely reminder to revisit the question.

If anyone is able to get Mr Sid files running on QGIS 1.7 in Ubuntu, please post your solution here.

My attempts using the GDAL build 1.8 are recorded below.

```
jvc@CF1:~$ sudo gdal-mrsid-build $HOME/Raster_DSDK
[sudo] password for jvc: 
grep: /home/jvc/Raster_DSDK/include/support/lt_base.h: No such file or directory
Extracting GDAL/MrSID tarball
Building GDAL/MrSID plugin
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ranlib... ranlib
checking for g++ -shared ... yes
checking for gdal-config... /usr/bin/gdal-config
using /usr/lib/gdalplugins/1.8 as GDAL shared library autoload directory
checking for lt_base.h in /home/jvc/Raster_DSDK/include/support... not found.
checking for lt_base.h in /home/jvc/Raster_DSDK/include... found MrSID DSDK version 7.x or newer.
checking for MG3ImageWriter.h in /home/jvc/Raster_DSDK/include/mrsid_writers... no encoding support.
checking for MrSID JPEG2000 support... configure: error: MrSID JPEG2000 support requested, but libltikdu.a not found.
jvc@CF1:~$ 
```

```
jvc@CF1:~$ sudo gdal-mrsid-build $HOME/Lidar_DSDK
grep: /home/jvc/Lidar_DSDK/include/support/lt_base.h: No such file or directory
grep: /home/jvc/Lidar_DSDK/include/lt_base.h: No such file or directory
/home/jvc/Lidar_DSDK seems not containing an GeoExpress SDK 4.0+
jvc@CF1:~$ 
```

Many thanks
BB

---

### Post by BigBaka on 2011-07-15
Hello....

Still no ideas anyone?

---

### Post by comeisl on 2011-08-09
Same problem with Ubuntu 11.04, and Lizardtech-DSDK 8.0. mistake seems to be on Raster and Lidar structure, is not recongnized by gdal on building. I've checked the gcc 3.4 and 4.1 without success.

If somebody has any idea...

---

