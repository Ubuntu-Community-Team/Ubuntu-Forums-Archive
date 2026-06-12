---
title: "Waypoint manager for usb Garmin GPS units"
date: 2011-01-02
forum: General Help
---

### Post by BigBaka on 2011-01-02
Dear all,

I've been trying for a while now to find an effective track and waypoint manager on Ubuntu so that I can download tracks and waypoints via USB for my Garmin GPS-60 and GPS-60 CSX hand held GPS field units. 

Have tried a bunch of different programs, but still no luck. Has anyone been able to find a solution. I even tried to install dnrgarmin through wine, but that didn't work either.

Thanks
BB

---

### Post by BigBaka on 2011-01-16
Anyone?

---

### Post by tredegar on 2011-01-16
I like [tangogps]("http://www.tangogps.org/gps/cat/About")
It works perfectly with my USB GPS "mouse", saves tracks, shows the map from OSM etc.

---

### Post by BigBaka on 2011-01-17
Hi Tredegar,

I had a look at that Tanogps, but I couldn't see anything about it downloading waypoints and tracks that have been previously recorded on a garmin gps unit and then brought back to the office. Do you use the tangogps as a waypoint manager to actually download waypoints onto a computer?

BB

---

### Post by tredegar on 2011-01-17
I understand your question better now. I use tangogps to record and display data from my GPS receiver, and (optionally) show me where I am on the map.

For managing tracks and waypoint data I have collected, OSM ( [Their wiki is here]("http://wiki.openstreetmap.org/wiki/Beginners%27_Guide") ) is primarily an open-source _mapping_ project, but they inevitably have many excellent and awesome (linux) tools for managing geographical data. See also their [map]("http://www.openstreetmap.org/")

[JOSM]("http://wiki.openstreetmap.org/wiki/JOSM/Installation") is a 100% linux-compatible editor that'll download map data from the OSM database, you can then import/overlay your own data with, if you wish, photos automagically attached to the points where you took them). 

There are some good JOSM video tutorials [here]("http://showmedo.com/videotutorials/video?name=1800040&fromSeriesID=180") It is not difficult to use, and if you prefer you can save all data locally rather than upload it to OSM.

The OSM Wiki will lead you to many other applications like [**prune**]("http://wiki.openstreetmap.org/wiki/Prune") that help with managing GPS tracks & waypoints.

Hope this helps.

Best wishes.

---

### Post by BigBaka on 2011-01-23
After looking through the QGIS forums I've found the answer [here]("http://forum.qgis.org/viewtopic.php?p=6515#p6515").

I use QGIS for my GIS needs on Ubuntu and they have a GPS plugin available through the plugins manager, although I could never get it working with my Garmin USB unit. But after a little searching I found that actually it is quite easy...

In QGIS:

Start the GPS-Plugin, go on "download from GPS" and choose "Edit device".
Make a new device, call it whatever name you want (eg. "Garmin USB")

Then insert the following lines:

Waypoint download: 
```
%babel -w -i garmin -f usb: -o gpx -F %out

```
Waypoint upload:
```
%babel -w -i gpx -f %in -o garmin -F usb:
```
Route download:
```
%babel -r -i garmin -f usb: -o gpx -F %out
```
Route upload:
```
%babel -r -i gpx -f %in -o garmin -F usb:
```
Track download:
```
%babel -t -i garmin -f usb: -o gpx -F %out
```
Track upload:
```
%babel -t -i gpx -f %in -o garmin -F usb:
```
 Remember to press "update device" so that everything is saved.
And now it should work! Not very difficult...

I got this working with my Garmin GPS60 will try with the GPS60csx in the near future.

Many thanks to Pinquin on the QGIS forum for this.
Best
BB

---

### Post by BigBaka on 2011-02-13
It seems I spoke to soon, after closing QGIS and reopening I'm unable to get the downloads going. So this thread is still unsolved!

---

### Post by Herman on 2011-02-18
Hello BigBaka, I saw your thread here and it aroused my curiosity, I just had to try it.
I have a friend's Garmin GPSmap 76Cx and I plugged it into my computer by a USB cord.
I have Quantum GIS, Google Earth and also Prune installed in my Ubuntu Lucid Lynx in this computer. GPSPrune should be available from your 'Applications'->'Ubuntu Software Center'.

In Quantum GIS I just went 'Plugins'->'GPS'->'GPS Tools' and clicked the tab titled 'download from GPS'. Then I used the following settings,
Garmin Device: Garmin Serial - (seems to be the only choice available for this field)
Port: USB
Feature Type: Waypoints, Tracks or Routes - (I had to run through the process three times, one for each of these selections).
After I typed in a layer name and a name for the output file, my data appeared in Quantum GIS.

Prune was easier, I just went 'File'->'Load data from GPS', and viola! My data appeared in the Prune window. After taking a look at it, I decided to export it as a .kml file and open it in Google Earth, so I went 'File'->'Export as KML', provided a title for the data and clicked okay, then in the next window I and gave it a file name and clicked 'save', and then opened the file in Google Earth.

I hope something I have mentioned might be some help for you. I don't know how much difference there might be between your Garmin GPS-60 and GPS-60 CSX and the Garmin 76Cx I have the use of, but I hope you can do it. Keep on trying! :)

---

### Post by sea_dawg on 2011-04-23
If you are still looking for something try GPS Utility

[http://www.gpsu.co.uk/](http://www.gpsu.co.uk/)

It is a Windows application that is well behaved under Wine.

---

### Post by gaxi on 2012-07-14
> **BigBaka said:**
> Dear all,

I've been trying for a while now to find an effective track and waypoint manager on Ubuntu so that I can download tracks and waypoints via USB for my Garmin GPS-60 and GPS-60 CSX hand held GPS field units. 

Have tried a bunch of different programs, but still no luck. Has anyone been able to find a solution. I even tried to install dnrgarmin through wine, but that didn't work either.

Thanks
BB
I have just installed gpsprune, after starting as root via terminal
```
sudo gpsprune
```
is could communicate with my Garmin extrex venture Cx on "usb:" directly.

GaXi ;-)

---

### Post by overdrank on 2012-07-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

