---
title: "Problems synching Garmin 305 in pytrainer"
date: 2011-01-08
forum: General Help
---

### Post by Peter Sixsmith on 2011-01-08
Hi All

I have recently installed Ubuntu so i am completely new to this operating system. 

I have installed pytrainer and wish to synchronise my Forerunner 305.

When I connect the 305 pytrainer does not seem to see it.

When I try to import using GPSBabel I get the following error - *Must be using 1.3.5 of GPSBabel for this plug in. *

When I try to import using Garmin tools I get the following error - *Cannot find gamintools binaries*.

Please can somebody help or point me in the right direction. Simple instructions best as I am a complete beginner! :D

Peter - A Ubuntu learner

---

### Post by meijer.o on 2011-01-08
Dear linux user,

For fixing permissions see this post [http://www.gpspassion.com/forumsen/topic.asp?topic_id=121878](http://www.gpspassion.com/forumsen/topic.asp?topic_id=121878) - not so easy for a beginner. (rule included in zipfile)

Install the files included as a attachment. gpsbabel has an nice interface now. It is a complex but good application.

Start gpsbabel: press Alt-F2 (run) and type gpsbabelfe

I own a garmin gpsmap60csx. It works well with linux and with pyTrainer (I did not know this application)

Good luck,

Otto

---

### Post by Peter Sixsmith on 2011-01-09
Thanks for the help Otto

I have installed GPSBabel and it appears to sync with the 305 OK. 

It creates a .gpx file on my desktop.

However when I try to import this into pytrainer no data is visible.

Any ideas?

---

### Post by meijer.o on 2011-01-09
Dear linux user,

I also found some difficulties. Check the .gpx file, may-be the time stamp of the coordinates are missing.

I don't no if the gps can be attached to your computer as a usb-mass storage device? If so, try tis to obtain the tracks.

Best regards,

Otto

---

### Post by waldzinator on 2011-04-14
Hello,

Showing up late to the party, but hopefully I can help.  I'm not sure what garmintools is, but I highly recommend you look into the garmin-forerunner-tools google code project page.  You can download the source code in a tar.gz format, compile on your computer, and a binary is placed in /usr/bin.  It has functions for pulling the data off your Forerunner and writing it to gpx.

As for the gpsbabel, I learned this the hard way recently.  The latest version, with a lot of patches, is not on Synaptic.  Go to [www.gpsbabel.org](www.gpsbabel.org), download the source, and compile it.  You'll get a binary (called gpsbabel) in whatever folder you compiled it in, which you can then sudo mv to /usr/bin so it's available to you.  

I user my forerunner 305 all the time, and I've actually integrated garmin-forerunner-tools into a python gtk program I developed that downloads the run data, allows me to add some info, and then writes the data to MySQL.

Good luck.

---

