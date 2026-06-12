---
title: "Newish user: Installing Mrsid in Qgis"
date: 2011-01-12
forum: General Help
---

### Post by bnewb on 2011-01-12
It seems other folks have had similar problems...My specifics:
Trying to install MrSid support (8.0) in Qgis 1.6.0. I'm running Ubuntu 10.04.

I followed the tutorial at

[http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid](http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid)

When I get to Step 3: Building the Plugin

I entered 

sudo gdal-mrsid-build $HOME/Unified_DSDK_8.0_linux.x86-64.gcc41

I get back

grep: /home/brian/Unified_DSDK_8.0_linux.x86-64.gcc41/include/support/lt_base.h: No such file or directory
grep: /home/brian/Unified_DSDK_8.0_linux.x86-64.gcc41/include/lt_base.h: No such file or directory
/home/brian/Unified_DSDK_8.0_linux.x86-64.gcc41 seems not containing an GeoExpress SDK 4.0+


It seems that the files not found do exist but not at the specific path.
I'm not sure what to do...

Any help would be much appreciated.

---

### Post by jurgenachilles on 2011-03-19
I have the same problem!

---

### Post by jywarren on 2012-03-21
Same here. Perhaps the "unified SDK" is structured differently...

---

### Post by jywarren on 2012-03-21
I'm seeing a recommendation to download the older version from this svn repo:

[http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41/](http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41/)

using for example:

```
svn co http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41/
```

More in this thread: [http://ubuntuforums.org/showthread.php?p=11316499](http://ubuntuforums.org/showthread.php?p=11316499)

---

