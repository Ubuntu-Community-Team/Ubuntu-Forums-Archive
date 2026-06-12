---
title: "QGIS 1.6 on 10.10 Maverick MrSid files"
date: 2010-12-31
forum: General Help
---

### Post by BigBaka on 2010-12-31
So here we go again, 

Another Ubuntu distro, another QGIS version, but still the same hassles of trying to get QGIS in Ubuntu to take MrSid raster file formats. I just did a fresh install of 10.10 and added the unstable qgis ppa to my software sources as follows.

deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) maverick main 

However, the same problem as before, we need to add gdal, and the MrSid plugin in order to be able to use sid file formats. 

Alas, no tutorial seem to be up yet explaining how to do this in 10.10. The previous tutorial at [http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid](http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid) is using a different sdk version from [http://www.lizardtech.com/developer](http://www.lizardtech.com/developer) . Now lizardtech has released a version 8 sdk, and no explanation of how it should be installed. Alas I'm not geek enough to be able to work out how to do this myself.

If anyone can shed some light into how to set up the new sdk and add the mrsid plugin, it would be most appreciated.

Regards,
BigBaka

---

### Post by jvc26 on 2010-12-31
Is it not simply exactly the same as the tutorial above, but with the version numbers changed appropriately? So for example, 

```
sudo gdal-build-mrsid $HOME/Geo_DSDK-7.0.0.2167
```

would read:

```
sudo gdal-build-mrsid $HOME/Geo_DSDK-VERSIONNUMBER
```

J

---

### Post by BigBaka on 2010-12-31
yeah, I thought about doing something like this, but the way in which the new sdk works means that it isn't so straight forward. Previously after unpacking there was one folder with the number string so it was obvious what should be done regarding the dpkg. However, with SDK 8 when you unpack the downloaded tar.gz file to give you three different folders: Lidar_DSDK, Raster_DSDK, and examples. So I wasn't really sure what to do.

If you try and use the same command it comes up with this

```
jvc@CF2:~$ cd Downloads
jvc@CF2:~/Downloads$ tar -zxvf Lidar_DSDK
tar (child): Lidar_DSDK: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvc@CF2:~/Downloads$ tar -zxvf Raster_DSDK
tar (child): Raster_DSDK: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvc@CF2:~/Downloads$ 
```



BB

---

### Post by BigBaka on 2010-12-31
Hey,

I just took a guess and tried to adapt the previous tutorial to the new folders and came up with the following

```
jvc@CF2:~$ sudo gdal-mrsid-build $HOME/Lidar_DSDK
grep: /home/jvc/Lidar_DSDK/include/support/lt_base.h: No such file or directory
grep: /home/jvc/Lidar_DSDK/include/lt_base.h: No such file or directory
/home/jvc/Lidar_DSDK seems not containing an GeoExpress SDK 4.0+
jvc@CF2:~$ sudo gdal-mrsid-build $HOME/Raster_DSDK
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
using /usr/lib/gdal17plugins as GDAL shared library autoload directory
checking for lt_base.h in /home/jvc/Raster_DSDK/include/support... not found.
checking for lt_base.h in /home/jvc/Raster_DSDK/include... found MrSID DSDK version 7.x or newer.
checking for MG3ImageWriter.h in /home/jvc/Raster_DSDK/include/mrsid_writers... no encoding support.
checking for MrSID JPEG2000 support... configure: error: MrSID JPEG2000 support requested, but libltikdu.a not found.
```

Seems like the second folder started to work, but then crashed somewhere along the way. Still can't get Sid running in qgis.

BB

---

### Post by unclemush on 2011-01-08
FWIW I took the expedient approach and simply rebuilt GDAL with the LizardTech 7.0 SDK.  It loaded into QGIS and the MrSID files displayed.

Looking at the gdal-mrsid-build script it's clear that the only module it knows how to, or will, build is the MrSID module.  If you want to build with the 8.0 SDK you might want to try:

$ gdal-mrsid-build /usr/local/src/Geo_8.0-SDK/Raster_DSDK

or whatever the appropriate path to the Raster SDK is for your installation.

---

### Post by BigBaka on 2011-01-08
Hi Unclemush,

Yeah I also considered building GDAL with the LizardTech 7.0 SDK, however, I couldn't find a copy of the 7.0 SDK anywhere on the LizardTech site. It seems they only have the 8.0 SDK for download. Do you know where it can be downloaded from?

I previously tried to build with the 8.0 SDK using the Raster_DSK folder and got the following errors.

```
jvc@CF2:~$ sudo gdal-mrsid-build $HOME/Raster_DSDK
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
using /usr/lib/gdal17plugins as GDAL shared library autoload directory
checking for lt_base.h in /home/jvc/Raster_DSDK/include/support... not found.
checking for lt_base.h in /home/jvc/Raster_DSDK/include... found MrSID DSDK version 7.x or newer.
checking for MG3ImageWriter.h in /home/jvc/Raster_DSDK/include/mrsid_writers... no encoding support.
checking for MrSID JPEG2000 support... configure: error: MrSID JPEG2000 support requested, but libltikdu.a not found.
```

---

### Post by unclemush on 2011-01-09
I haven't tried to build v8.0 of the LizardTech SDK, but I may play with it later.  The missing library may just be a path problem during linking.

I still have the 7.0 SDK if you would like a copy?

---

### Post by unclemush on 2011-01-10
Digging deeply into the 8.0 SDK the 3rd-party library (libltikdu) needed for jpeg2000 support is missing.  I copied the missing files over from the older 7.0 SDK and the JPEG2000 error went away.  A new error appeared complaining the "libgeotiff" is required.  I do have the libgeotiff development files on my system, but configure seems unable to find them.  Another mystery to investigate.

Right now I'm rummaging around in the gdal-mrsid-build and config script files to see if I can figure out what's going wrong.

It certainly looks like there's a problem with Geo_DSDK-8.0 distribution package missing files.

---

### Post by alegeott on 2011-01-11
> **unclemush said:**
> Digging deeply into the 8.0 SDK the 3rd-party library (libltikdu) needed for jpeg2000 support is missing.  I copied the missing files over from the older 7.0 SDK and the JPEG2000 error went away.  A new error appeared complaining the "libgeotiff" is required.  I do have the libgeotiff development files on my system, but configure seems unable to find them.  Another mystery to investigate.

Right now I'm rummaging around in the gdal-mrsid-build and config script files to see if I can figure out what's going wrong.

It certainly looks like there's a problem with Geo_DSDK-8.0 distribution package missing files.

I have the same problem (on debian squeeze and gdal 1.6).
You shoud send a bug segnalation to the mantainer of the script ([gdal-mrsid, or libgdal-mrsid]("https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable/+packages?field.name_filter=mrsid&field.status_filter=&field.series_filter=")). I can't because i couldn't install Apport and, for this, I can't generate the bug report.

In addiction, how I can obtain the old version (7.0) of SDK?
Thank you

---

### Post by chipko on 2011-01-13
The problem is not that there is something wrong with the new version of the SDK but that the package structure and libraries have changed so that it will not work with gdal-1.7.  Gdal-1.8 is being redone to work with the new SDK, see [this]("http://osgeo-org.1803224.n2.nabble.com/gdal-dev-mrsid-nmake-opt-td5909268.html#a5910702") gdal-dev thread for more information.  In order to get mrsid with the current version of gdal, or qgis, you need an older version of the SDK and, unfortunately, only the 8.0 is currently on the lizardtech site.

---

### Post by jurgenachilles on 2011-03-19
> **unclemush said:**
> I haven't tried to build v8.0 of the LizardTech SDK, but I may play with it later.  The missing library may just be a path problem during linking.

I still have the 7.0 SDK if you would like a copy?
I would like a copy please, seems to me the only way to get it working.

---

### Post by BigBaka on 2011-05-16
So this morning I ran an automatic update on my lucid 10.04 comp, and noticed that a new gdal was being installed along with several other version updates for qgis. O oh, this is going to me trouble for my Mr Sid files I thought, and sure enough, upon opening up qgis post update I discovered that I was no longer able to load in Mr Sid raster files into qgis.

So I'm going back to the lizard tech site and presently downloading the SDK 8.0 ( Redhat Enterprise Linux 5 x86 gcc 4.1 ). Lets see if we can get it running this time. I'll also try and get it up and running on my 10.10 comp when I get to the office. Will keep you posted.

BB

---

### Post by BigBaka on 2011-05-16
Alas, no success!

As I had previously tried back in January, I tried a similar build approach that was listed for the 7.0 SDK.

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
jvc@CF1:~$ sudo gdal-mrsid-build $HOME/Lidar_DSDK
grep: /home/jvc/Lidar_DSDK/include/support/lt_base.h: No such file or directory
grep: /home/jvc/Lidar_DSDK/include/lt_base.h: No such file or directory
/home/jvc/Lidar_DSDK seems not containing an GeoExpress SDK 4.0+
```

Still no luck.

I noticed in the readme files in the 8.0 SDK that it says

INSTALLATION:

  No specific installation is required to use the LiDAR SDK beyond
  copying the SDK contents to your local machine.

  After installing, we suggest building and running the example program
  to assure correct installation and behaviour.

Is this true? Where exactly should we copy the contents to then?

As always, all help is greatly appreciated!

Regards
BB

---

### Post by comeisl on 2011-08-18
I've tried also using gdal 1.8.0 Ubuntu 11.04 and SDK 8.0, without success, any idea?

Thanks!

---

### Post by JamesCEddy on 2011-10-05
Here's how I compiled the MRSID plugin for gdal1.7 on ubuntu 10.10:

Follow step #2 from:
[http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid]("http://trac.osgeo.org/ubuntugis/wiki/TutorialMrSid")

webcrawl this site to get the DSDK 7, unfortunately lizard techs 8.0 SDK does not work with gdal 1.7 (from what I read):
[http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41]("http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41")/

Once you get all the files run:
```

sudo gdal-mrsid-build <your local dir>/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41
#verify with
gdalinfo --formats |grep -i sid

```

If you run into the dreaded

```

checking for MrSID JPEG2000 support... configure: error: MrSID JPEG2000 support requested, but libltikdu.a not found.

```


It means you're missing Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41/3rd-party/lib/Release/liblt_kakadu.a

Note how libltikdu.a != libtl_kakadu.a, the configure script will take either. The Nasa site from above has libtl_kakadu.a and should work if you put in the right place.

Enjoy!

---

### Post by BigBaka on 2011-10-05
Hi, Thanks for the info.

A quick question. When you say
> 
webcrawl this site to get the DSDK 7, unfortunately lizard techs 8.0 SDK does not work with gdal 1.7 (from what I read):
[http://worldwind31.arc.nasa.gov/svn/...x.x86-32.gcc41/](http://worldwind31.arc.nasa.gov/svn/...x.x86-32.gcc41/)

Do you mean we have to manually go through and download every file and put into appropriate subfolders as per the folder structure on the website. Isn't there a quicker way to download all these files at once?

Regards,

BB

---

### Post by Roy_RS on 2011-10-06
Isn't it available for 11.04?, I followed that step two wich says:

> In a terminal, type:

sudo apt-get update
sudo apt-get install libgdal-mrsid-src 
sudo apt-get install gdal-bin

But I got this:


> E: No se ha podido localizar el paquete libgdal-mrsid-src

which means: "could not locate package libgdal-mrsid-src" or something like that.

---

### Post by jywarren on 2012-03-21
BigBaka, it's been a while, but for the record, you can download the entire repository from the NASA site with:

```
svn co http://worldwind31.arc.nasa.gov/svn/trunk/GDAL/GDAL-1.7.2/MrSID/linux/Geo_DSDK-7.0.0.2167.linux.x86-32.gcc41/
```

---

