---
title: "Guide for using garmin Forerunner 205/305 GPS unit with Ubuntu"
date: 2010-04-09
forum: General Help
---

### Post by pabc on 2010-04-09
I run a lot. Under WinXP I recorded my running locally with Sporttracks and remotely with Fetcheveryone.com. I also used the Garmin provided software (Traing Center) to create routes on the GPS running watch that I could follow when I ran in an area I didn't know.

Recreating these abilities has been an issue under Ubuntu but I'm there. Hopefully anyone else searching these forums will stumble upon this post and it might help them.

This was all done on 10.04 (B1).

Locally - Sporttracks.

The latest sporttracks works fine under Mono with the winforms libraries.

follow the instructions here;
[http://www.zonefivesoftware.com/SportTracks/Downloads/linux.php](http://www.zonefivesoftware.com/SportTracks/Downloads/linux.php)

I'm assuming you unpacked to ~/Sporttracks

and install the winforms.
```
sudo apt-get install libmono-winforms2.0-cil
```To import runs you need the Linux import plugin which relies on forerunner-tools.
```
sudo apt-get install garmin-forerunner-tools
```Grab the import plugin from;
[http://code.google.com/p/linuxgarminimport/](http://code.google.com/p/linuxgarminimport/)

the file is a .st2plugin but it is just an archive. Extract it to ~/Sporttracks/Plugins (you may have to create the Plugins folder first)

from a terminal start Sporttracks with

```
cd ~/Sporttracks
mono SportTracks.exe
```Plug in the Forerunner and import your runs!


remotely - [www.fetcheveryone.com]("http://www.fetcheveryone.com")
The garmin communicator plugin is windows only. And Although you can run the plugin under Wine with firefox and it reports to be functioning properly it cannot detect the garmin. This is likely to be due to lack of support at the browser level for window.external.

However, [http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/) will have very shortly a .deb which adds a native plugin for ubuntu. I say will have as it's not online yet but I know it exists as I've been testing it for him.

The stock scripts for websites to use the plugin all require a windows user agent - so install the 'user agent switcher' plugin and set it to IE8 then visit your favorite running log website.


Uploading routes to the unit.

In this case I created the routes in MemoryMap under Wine and saved them as .gpx - but as long as you have the correct input format this works. ie you could create a route on a running website which allows it to be saved as .tcx (fetcheveryone.com + many others) for example and use that file to upload to the unit.

to do the unit upload gpsbabel is required

```
sudo apt-get install gpsbabel
```then from a terminal type

(for gpx);
```
gpsbabel -i gpx -f ~/mygpx.gpx -x simplify,count=100 -r -o garmin -F USB:
```(for tcx)
```
gpsbabel -i gtrnctr -f ~/mytcx.tcx -x simplify,count=100 -x transform,rte=trk -r -o garmin -F USB:
```Finally - gpsbabel doesn't yet support uploading courses to units (although a patch has been submitted but it'll require a compile to get it working - or wait)

You can see all the different input file formats and the code to add after the -i in the gpsbabel command here;
[http://www.gpsbabel.org/htmldoc-1.3.6/The_Formats.html](http://www.gpsbabel.org/htmldoc-1.3.6/The_Formats.html)

Hopefully this will help somebody out.

---

### Post by nickmcg on 2010-04-10
Thanks for the guide. Unfortunately I've fallen at the first hurdle.
When I try to unpack sporttracks-2.1.3478.tar.gz, I get ```
gzip: stdin: invalid compressed data--crc error
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

```
Any advice?

Thanks

Nick

Fixed: Renamed sporttracks-2.1.3478.tar.gz to sporttracks-2.1.3478.tar.zip, then archive manager worked (Ubuntu 10.04)

---

### Post by Richard Mathie on 2010-08-21
use pytrainer instead as you don't have to mess about with mono, and its quite good

can you link to the gpsbable patch/ discussion on courses, they have been really slow with this. I tried to get my head around [http://code.google.com/p/garmintools/](http://code.google.com/p/garmintools/) but I am not experienced enough to write my own,

---

### Post by Richard Mathie on 2010-08-21
The latest gpsbabel now works for uploading gps tracks to the watch as a course! apparently a guy called Martin Buck is responsible for getting it to work, well done him!

download the latest release
[http://www.gpsbabel.org/download.html](http://www.gpsbabel.org/download.html)

make sure you have build essentials and libusb-dev

```
sudo apt-get build-essentials libusb-dev
```


navigate in a terminal to the downloaded file and do the usual

```
tar -xvf gpsbabel.tar.gz
cd gpsbabel*
./configure
make
sudo make install
```


and now i can upload courses with

```
gpsbabel -i gpx -f 1.gpx -t -o garmin -F usb:
```

---

### Post by somhi on 2010-08-24
I can not compile gpsbabel under ubuntu 10.04 due to an error, 
something like "ld: cannot find -lexpat"


Anyway, this post is fantastic, many thanks to all of you, but I found left something: Is there a way in Linux to delete/rename tracks and waypoints from my Forerunner?

Cheers

---

### Post by Peter Sixsmith on 2011-01-08
Hi All

I have recently installed Ubuntu so i am completely new to this operating system.

I have installed pytrainer and wish to synchronise my Forerunner 305.

When I connect the 305 pytrainer does not seem to see it.

When I try to import using GPSBabel I get the following error - *Must be using 1.3.5 of GPSBabel for this plug in. *

When I try to import using Garmin tools I get the following error - *Cannot find gamintools binaries*.

Please can somebody help or point me in the right direction.

Peter - A Ubuntu learner

---

### Post by pabc on 2011-01-09
you have installed gpsbabel and garmintools? I'm in 10.04 and the latest version is 1.3.6

open a terminal and type

```
sudo apt-get install gpsbabel garmin-forerunner-tools
```

then type in your password (you wont see it on the screen) - the apps will install. once done type

```
gpsbabel -V
```

and it will report the version you are using. Then try again with pytrainer.

However - I would recommend taking the effort to use sporttracks as it is much more powerful (but a little more complicated to set up on ubuntu)

---

### Post by Richard Mathie on 2011-04-02
gpsbabel 1.4.1 and later support uploading tracks and coerces, as the latest isn't in the repository you have to download and install the latest from here: [http://www.gpsbabel.org/download.html]("http://www.gpsbabel.org/download.htm")

1.3.6 doesn't upload cources.

that error message means you don't have one of the required libraries, you can search for it, and each error which comes up, expat is an XML Parser, so install the expatlib and dev files to compile

```
sodo apt-get install libexpat1 libexpat1-dev
```

alternatively installing the gpsbabel from the repositorys should resolve the dependencies, you just need to make sure you use your gpsbabel you made is the one being called on the command line. here
```
whereis gpsbabel
```
and
```
PATH/gpsbabel -V
```

can be used to see if the right binary is being used. If the version dose not match the version you compiled try overwriting it for example with

```
sudo cp /usr/local/bin/gpsbabel /usr/bin/gpsbabel 
```

also if you know how you could modify your search path to pick up the correct binary.

---

### Post by mjaga on 2011-05-25
I have written a short HOWTO on how to use R to plot your tracks from a Garmin Forerunner 205, including support for Google maps. In short I am using the garmin_forerunner_tools to retrieve the data from the Garmin device and store them in an sqlite database, from where I can read and analyze the data in R using the ODBC database access package. The R version that comes with Ubuntu 10.10 has support for retrieving Google maps and plotting tracks on them. See

 [Using the Garmin Forerunner 205 with R on Ubuntu 10.10]("http://www.olberg.se/?q=node/25")

---

### Post by MetapostAddict on 2011-08-10
> **mjaga said:**
> I have written a short HOWTO on how to use R to plot your tracks from a Garmin Forerunner 205, including support for Google maps. In short I am using the garmin_forerunner_tools to retrieve the data from the Garmin device and store them in an sqlite database, from where I can read and analyze the data in R using the ODBC database access package. The R version that comes with Ubuntu 10.10 has support for retrieving Google maps and plotting tracks on them. See

 [Using the Garmin Forerunner 205 with R on Ubuntu 10.10]("http://www.olberg.se/?q=node/25")

that's awesome.  I'm definitely going to have to try this...

---

### Post by jakobb on 2012-05-01
> **mjaga said:**
> I have written a short HOWTO on how to use R to plot your tracks from a Garmin Forerunner 205, including support for Google maps. In short I am using the garmin_forerunner_tools to retrieve the data from the Garmin device and store them in an sqlite database, from where I can read and analyze the data in R using the ODBC database access package. The R version that comes with Ubuntu 10.10 has support for retrieving Google maps and plotting tracks on them. See

 [Using the Garmin Forerunner 205 with R on Ubuntu 10.10]("http://www.olberg.se/?q=node/25")

That is sooo cool !!!!
Recently just learned R, Cannot wait to receive my 910xt so I can try this out !!!!

---

### Post by oldos2er on 2012-05-01
Old thread closed.

---

