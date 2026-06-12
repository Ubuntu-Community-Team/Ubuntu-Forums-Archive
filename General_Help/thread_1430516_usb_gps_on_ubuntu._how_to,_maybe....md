---
title: "usb gps on ubuntu. how to, maybe..."
date: 2010-03-15
forum: General Help
---

### Post by Directive 4 on 2010-03-15
so plug your gps in and it doen't work, me to, but i have found a way...


0. we need a program to look at the data. gpsdrive or tango gps seems to do the trick.

1. we get some problem after installing throu synaptic, error 1 something to do with gpsd. gpsd is a program that relates the usb gps to the gui, tango gps, etc.

2. gpsd is of doing it's thing, we need to stop it. type 
ps -C gpsd -fww
into the terminal

3. this will output some info about gpsd, we need the pid number. 
UID                  .....PID  PPID  C STIME TTY          TIME CMD
nobody 3993     1  0 17:16 ?        00:00:00 gpsd -N -n -D 2 /dev/ttyUSB0

4. we use this number to kill gpsd, type
sudo kill 3993

5. now we want to start it up again but runing under your login not nobody type
gpsd -N -n -D 2 /dev/ttyUSB0

6. this line seems to help.
sudo dpkg --configure --pending

7.lets get a fix. type
gpsprof -f cycle
and wait for 30s...60s...maybe 200s...

8. open tango gps

9. ?????????

10. profit!

hope this helps:popcorn:

---

### Post by Directive 4 on 2010-05-10
sudo pkill gpsd


gpsd -N -n -D 2 /dev/ttyUSB0

open tango gps

 ?????????

profit!

---

### Post by NDLunchbox on 2010-05-14
I used dpkg to reconfigure gpsd not to start automatically, then I use gpsd -nD 2 /dev/ttyUSB0 to start the server.  if you use -nND 2 you will see the GPS data stream in your terminal.

I recommend using xgps to check functionality.

---

### Post by Herman on 2010-07-08
:) Old thread but, ... I bought one of these, [Model CVGI-B07 GPS Receiver USB Adapter]("http://www.chinavasion.com/product_info.php/pName/gps-receiver-usb-adapter-for-computers-netbook-laptop-umpc/")[,]("http://www.onsources.com/products/GPS-Receiver-USB-Adapter-for-Computers-%28Netbook,-Laptop,-UMPC%29%252d-Transform-your-laptop-into-a-GPS-navigator.html") and I'm  extremely pleased with it.  I imagine most other  GPS recievers would probably also work well.

I installed [TangoGPS]("http://www.tangogps.org/gps/cat/News")  which is in the 'Applications'-->'Ubuntu Software Center' and it works perfectly well for me and does  everything I want, maybe I'm lucky. 
I love Tango GPS, and it's just plug and play  for me. As far as I'm aware, there's no need for any special commands to start and stop it. Maybe it's something that has been fixed since this thread was started. 

UPDATE: Tango GPS seems to have disappeared and Foxtrot GPS is now available in the Ubuntu Software Center instead.  Homepage: [Foxtrot GPS]("http://www.foxtrotgps.org/").

**Getting Started With**** Foxtrot GPS**
Foxtrot GPS downloads and stores at least five kinds of maps  automatically, the maps come from OSM, Maps-for-free.com, Opencyclemap,  Google Maps and Google Sat.
More map repositories can be added, but that's a subject for later.

Before we start, we need an internet connection because the maps will need to be downloaded from somewhere.
We would want to be collecting maps for our own area, not for the default location or some random location and luckily for me, my EeePC has wireless networking and it can reach my home router from out  in my back yard. 
I ran a power cord out doors and sat at a table outside  and started up my GPS and I waited until I was sure the GPS was working properly. To check and make sure the GPS was working I used a program called [xgps]("http://manpages.ubuntu.com/manpages/lucid/man1/cgps.1.html") which runs from the terminal. When xgps started to show satellites in its sky view and show satellite data I went over to foxtrot GPS. Then in page one of Foxtrot GPS's  right-hand side bar I could see my home coordinates.
If you can't go outside, (maybe it's raining or other bad weather), probably if your GPS receiver is close to a window it will work indoors, but where I live the weather's nice outdoors right now. 
 
Foxtrot GPS won't start downloading any maps without our permission, we need to enable that  function. 

[LIST=1]
[*] From the (i) icon, which is the first icon at the top of the left-hand  side bar, we get a new sidebar over on the right-hand side, and that  side bar has four pages which can be switched by either of the two arrow  icons at the top of the sidebar.
[*] If you go to the fourth page, and look about 1/2 way down under 'auto  download', you can place a check in the checkbox to enable automatic map downloading.
[*] Under that will be a drop-down menu for 'map types', where we can select  what kind of map we want.
[*]I clicked on the 'autocenter on' icon in the left-hand sidebar,  (which is third up from the bottom), to get Foxtrot GPS to center itself on my current location, and waited.
[*]Soon, maps began to appear, and I could see where I was, and by zooming to different zoom levels, (using the + and - icons in the left-hand sidebar), Foxtrot GPS soon collected the map tiles of my current location, which is a starting point at least.
[*]If you wait for some time and nothing happens, check your internet connection, and if that's okay, try changing map types and try a different zoom level and wait again.
[*]Once you have a few map tiles to get started with, it gets easier. All you need to do is spend time panning around your area at various zoom levels and Foxtrot GPS will collect all the map tiles you need automatically.
[*]The map tiles are stored for off-line use, and if you're planning a journey, you can collect the map tiles in advance of your journey by panning along your proposed route at various zoom levels and for the different map types you may want.
[/LIST]
 Foxtrot GPS is perfectly user friendly once a person gets started with it, and the controls for it are self explanatery. It's a lot of fun and an extremely useful program as well.


**Track Logging with Foxtrot** **GPS**
If we want Foxtrot GPS to record our journey, we can go to page 3 of 4 in the right-hand side bar and click 'enable track logging'.
As soon as we enable track logging, Foxtrot GPS will create a plain text file in the Maps directory with a name representing the date and time it was started and ending with the characters '.log'.
The 'Split' button stops the log that's being written, and starts a new .log file, useful for breaking up your journey's .logs into manageable segments.

A Foxtrot GPS .log file will list information in the following format,
```
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:43Z
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:43Z
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:44Z

```Where: My Y coordinate, or latitude, is -25.383333
Where: My X coordinate, or longitude is 131.083333
Where: My altitude is 319.9 meters above sea level.
(These numbers are fictitious and don't represent my real location).

If you have Google Earth installed, those coordinates, first two numbers, like '-25.383333,131.083333', can be copied and pasted into the search field in Google Earth and Google Earth will find that location for you.

**Converting track.log files to .csv files**
Foxtrot GPS's .log files can easily be converted into .csv files so they can be opened later in [Quantum GIS]("http://www.qgis.org/"), so you can use them for adding information to your more permanent maps.
All you really need to do is add a .csv 'header' to the top line of the .log file, like this, 
```
Y_Coords_WGS84,X_Coords_WGS84,Z_Coords,satinfo1,satinfo2,satinfo3,Date_Time
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:43Z
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:43Z
-25.383333,131.083333,319.9,0.0,0.0,4.4,2010-07-16T20:58:44Z
```Changing the filename extension from .log to .csv isn't really necessary, but is suggested for the sake of easier file sorting.

If we have a lot of .log files to convert to .csv files, we can use a script for doing all the work for us, which makes it a lot faster and easier,
```
#!/bin/bash
# a script for changing tango gps log files into csv files
# by Herman H Felderhof 
# just copy this script and paste in inside a directory full of foxtrot gps log files and run it

echo 'hello this is a script for changing tango gps log files into csv files'
sleep 2

# add the required header line to the top of all .log files in the current directory
#sed -i 'Y_Coords_WGS84,X_Coords_WGS84,Z_Coords,satinfo1,satinfo2,satinfo3,Date_Time' *.log
for fil in *.log; do sed -i '1iY_Coords_WGS84,X_Coords_WGS84,Z_Coords,satinfo1,satinfo2,satinfo3,Date_Time' $fil; done

# replace the .log file name extensions with the .csv filename extension
for f in *.log; do mv "$f" "${f%.log}.csv"; done


```It's interesting to be able to transfer our track log information to our map making software via the .csv file(s) because then we can see the shape of the road or trial we've just traveled and find out its relationship to other features shown on some kind of a map. [B]

How to install Quantum GIS,
[/B]```
sudo apt-get install python-software-properties
```
```
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
```
```
sudo apt-get update
```
```
sudo apt-get install qgis
```
```
sudo apt-get install python-qgis
```

[B] How to open your .csv files in Quantum GIS
[/B]1. Open Quantum GIS, 'Applications', 'Science', 'Quantum GIS'
2.' Plugins','Delimited Text', 'Add Delimited Text Layer'
3. (i) Field 1: Delimited text file, either type the path and name of your file, or use the browse button at the end of the field and navigate to your .csv file and select it.
    (ii) Field 2: automatically filled from the filename of your .csv or you may optionally change it as you like
   (iii) Field 3: type a comma in the box for 'Delimiter string', and select 'Plain Characters' if that's not already set
(iv) Field 4: 'Geometry', probably will be filled automatically to 'X_Coords_WGS84' in the X field and 'Y_Coords_WGS84' in the 'Y' field, but you can use the drop-down menus to change it if you want to for any reason.   
(v) Click 'Okay'
If all went well, a row of dots should appear in the Quantum GIS main pane, showing you your Foxtrot GPS track. Congratulations, you have successfully loaded your first .csv file in Quantum GIS and now you can see your path, it looks something like a trail of breadcrumbs.

**How To Make a Raster Image For Use in Quantum GIS**
Your tangoGPS tracks might not look very interesting or be of much use to you by themselves, just on a plain white background.
To make sense of your tracks you will need some digital maps of your location to compare your track with whatever features are marked in the map.
Digital maps are hard to get for free, but you might get one by searching the internet and downloading it or from a friend who is already using GIS applications. 
Digital maps can be found in many different formats and Quantum GIS can open just about any of them.
If you can't get a digital map you might need to make your own raster image to get started with.

You can use just about any paper map for a raster image. 
You may want a topographical map or a road map or a geological map, a sea  chart or just about any other kind of map for a raster image.
Just use a scanner and scan the paper map to a digital image file in your computer, but beware of copyright restrictions. 
Most maps are quite restricted, but providing you're only going to be using it yourself (temporarily) and not republishing and redistributing, probably it will be okay, (but I'm not a lawyer). Another problem with raster images are, they tend to use a lot of memory and slow your computer down, especially very large rasters.It doesn't matter if you save your raster as a .jpeg or a .png image or some other file type, I think Quantum GIS can handle most image file types, (if I remember correctly). I prefer .png myself, because they're nice an light, .tiff is also supposed to be pretty good for map rasters. 
[B]
How to Open a Raster Image in QuantumGIS[/B]
UPDATE: There have been changes to the georeferencing tool in QGUS since this section was written and has been made more sophisticated, and at the same time more complicated for users. It's now a subject that requires a more detailed explanation and users should google for a dedicated web page about it. The following only applies to older versions of QGIS.
 
1. First you need to pick out at least three or four objects which you  can see clearly in your raster file and also in the map you already have  open in Quantum GIS.
If you have no other map already open in Quantum GIS you can use google  earth instead, to get the coordinates for three or four distinct  landmarks which show in your raster file.
Another way to find the coordinates for your control points is to go and  visit those locations with a GPS unit and record the Y and X  coordinates yourself.

These three or four, (or more if you like) objects are called 'control  points', and it's best if they are close to the corners of your raster, one can be in the middle if you want,  as long as they are well spread out, not too close together if you want  good results.

You should try to choose things you know have not been moved, like a  mountain top. If you choose something like a bridge, be careful that the  bridge has not been rebuilt in another nearby spot since your raster file map  was made. That would put your map's alignment out.
3. in Quantum, click 'Plugins'-->'Georeferencer'-->'Georeferencer'

4. In the 'Georeferencer' dialog window, type or paste the path and name  of your file in the 'Raster File:'  field, or use the 'Find' button and navigate to your file and select it.

5. Your image should appear in the  'Reference Points' dialog window, and you can zoom in and pan around in  that image very easily and quickly to  find your control points. 
Find each of your control points one at a time and click on the 'Add  Point' button, (looks like a dice), and click on a control point.
The 'Enter Map Co-ordinates' dialog window appears and you can enter  your co-ordinates in the x and y fields, or else click the 'From Map  Canvas' button and locate your points on the map, (slow and tedious).

6. Repeat the above for at least two more control points, more is  better.

7. When done, click 'Create and Load Layer'.

8. In Quantum's 'Legend' pane, right-click on your new layer and click  'zoom to layer extent', to see what it looks like. Look around the edges  of your new layer and see if rivers and roads line up with the rivers  and roads in the control layer.

9. In Quantum's 'Legend' pane, right-click on your new layer and click  'Properties', and click the 'transparency' tab. Set the transparency to  around 50%. Hit 'Apply', and wait, then 'OK'.
Now, zoom in and pan around and see if your alignment is right or not.

10. If you are happy with your alignment, click the 'save' button in  Quantum.

If you can't find the georeferencer plugin in Quantum GIS, please refer to badaveil's excellent instructions in [post #5]("http://ubuntuforums.org/showpost.php?p=9230809&postcount=5") of [Ubuntu 10.4 LTS & Quantum GIS (QGIS) 1.4  (Ubuntu version]("http://ubuntuforums.org/showthread.php?t=1470575").

**Introducing the gpspipe Command**
If you tried out the ideas I just explained above, or even if you only read it and got the gist of it, you now know how to record a road, trail or track and add it to your map. 
What about the points of interest along the way?
We need to be able to collect other kinds of map data about locations, (points of interest) we might want to record in our maps.
For example, an ornothologist might want to mark the spot where a particular bird was sighted and record the details of that bird in the map data. For a fisherman, maybe recording what kinds of fish were caught at a certain date at a secret fishing spot, and how big they were, might be useful data to put in a map, (or 'chart' if you're working on the water).
Gathering data about road assets is part of my job at the moment, so I'm interested in collecting information such as the location, dimensions and condition of things like bridges, concrete culverts or pipes,  grids and floodways, basically any made of concrete that has to do with roads. 
Data like this is point data, or in other words it's data that can be tied to a particular coordinate in a map, as opposed to linear type data we used for recording a road, track or fenceline.
Point data is harder to record, usually there's a number of details like measurements we might want to make that normally require manual note taking such as writing things down on paper or typing the information to be recorded into a laptop. When I'm in the feild or on the road, I don't like having to spend very much time and effort writing things down or doing a lot of typing.
To make the data collection side of things easier, I wrote myself a collection of scripts which are  unique for the particular data I need to collect. 
In order to make  things more automatic and reduce human error, I wanted  a command to  read the gps coordinates so I can have them outputted to a  file before my other data. 

Here is the command I came up with,
```
gpspipe -w -n 5 | grep lat | cut -d ":" -f6,7,8,9 | cut -b   13-26,33-45
```When this command is used from the command line it  outputs the GPS  coordinates for my current position. 
In a script it only needs to be directed to a file and when combined   with an interactive series of data collection lines prompting for input   and outputting to the same file, we can turn our Ubuntu laptop into a   powerful and versatile geodata collection unit.
By playing the the cut command it can be expanded to include the    altitude and other data as well if a user desires.
I'll add more specific information about writing scripts for collecting GIS data later. - to be continued . - see 'Roll Your Own - Shell Scripts for GPS Data Collecting', further down in this post.

**Roll your own Shell Scripts**
I used the gospipe command to make my own shell scripts for recording details of objects I'm interested in and their details for my mapping purposes. 
[B]
Time Lapse Photos Geotagged in Real Time
[/B]If you have a webcam or better a camera capable of being controlled from Ubuntu, you can have Ubuntu take photos at any time interval you specify.
Time lapse photography is really cool! Just google 'time lapse  photography' and I'm sure you'll be impressed!
An excellent website about time lapse photography in Ubuntu is here, [A Webcam Server with Linux]("http://www.moreno.marzolla.name/software/camera_control/") and another page, [Do-it-yourself Time-Lapse Photos with gphoto2]("http://www.moreno.marzolla.name/software/time_lapse_movies/").
I think Professor Marzolla's site is super cool, and that inspired me to try something similar.

I wanted my photos to be geotagged as well, and not only that, I want them geotagged in real time, (as each photo is are taken, automatically, I don't want to have to waste time messing around with them later).
And, I want the coordinates printed on the bottom of each photo.
For the exif command to handle the geotagging, I found another great Ubuntu user's website here, [leoboiko's computing log]("http://namakajiri.net/complog/geotag-your-photos/").
You will need to install ImageMagic for this script, and here is a web page about how to label photos with ImageMagick, [http://www.imagemagick.org/Usage/text/ ]("http://www.imagemagick.org/Usage/text/")

Here's the script I made after combining some of the commands from both of those helpful websites, I named it uvccapture_0.9.sh and if you take a copy of it you'll need to name yours uvccapture_0.9.sh too for it to work properly. 
That's because the last line tells the script to run itself again, so if you change the name of it, it will only run once, unless you also edit the last line correspondingly. 
```
#!/bin/bash
# a script for taking photos with a webcam at specified intervals
# by Herman H Felderhof 
# requires imagemagick, uvccapture, exiftool, gpspipe

# get the date and time
now=$(date +"%y-%m-%d-%H-%M-%S")

# take one photo and name it after the time and date
uvccapture -d/dev/video1 -x640 -y480 -o"$now".jpeg

#get current gps coords
lat=$( gpspipe -w -n 5 | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 13-22 )
lon=$( gpspipe -w -n 5 | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 33-42 )
alt=$( gpspipe -w -n 5 | grep -m 1 lat | cut -d ":" -f6,7,8,9 | cut -b 53-59 )

# geotag the new photo
exiftool -overwrite_original -GPSLongitudeRef="E" -GPSLongitude="$lon" -GPSLatitudeRef="S" -GPSLatitude="$lat" "$now".jpeg

# print the coords on the front of the image
text=`identify -format "$lat, $lon, $alt" $now.jpeg` 
width=`identify -format %w $now.jpeg` 
convert "$now".jpeg -gravity southeast -pointsize 40 \
-stroke black -strokewidth 4 -annotate 0 "${text}" \
-stroke white -strokewidth 1 -fill white -annotate 0 "${text}" \
"$now.jpeg" 

# wait 
#sleep 1

# run this script again
./uvccapture_0.9.sh

```Where: My EeePC has its own inbuilt webcam, /dev/video0, plus another separate webcam I can mount on my car's dash, so it faces forwards for a view of the road in front of me, /dev/video1. (Some people may need to alter the script from /dev/video1 back to /dev/video0 if their computer only has one webcam.
Where: I just have a webcam so I used the uvccapture program for taking the pictures, some people might want to alter the script and use the gphoto command if they have a controllable camera, (that would be better).
Where: I want the script to run as fast as it can, if I wanted to slow it down I would remove the hash mark from the sleep command, and I could increase the number if I wanted the script to wait longer before taking another photo. 
NOTE 1: This script takes new picture about once every six seconds in my  EeePC  computer, but actually I would like to take pictures a little faster  than that, like maybe every two or three seconds.
Possibly I'm being limited by hardware capabilities, but the same hardware can take video using luvcview at about 7.5 frames per second, maybe it's the geotagging and image editing (writing the text at the bottom of the images), that's slowing things down, or maybe I can think of ways to improve my scripting to make it loop instead of repeating itself and see if that's faster.

NOTE 2: People in the northern hemisphere will need to change the 'S' for an 'N' in the exiftool command, and likewise for the 'E' to an 'W' for some people, depending on what part of the planet you happen to be on.
If you might be crossing the equator or the prime meridian while you're using this script, you will need to modify the script if you want that catered for automatically. In the page sub-linked from  [leoboiko's computing log]("http://namakajiri.net/complog/geotag-your-photos/"), you will find another script you may find useful.

TIP: I have the same problem as Prof. Marzolla with using the webcam outdoors. In bright daylight the photos are mostly overexposed. 
My workaround is to stick a lense from and old pair of sunglasses in front of my webcam, it reduces the problem somewhat.
Webcam pictures are not very good best quality, but they'll be better than nothing until I find the right kind of camera.

People studying or working in some field of science or engineering might  find geotagged photographs useful, as well as time lapse photography. Or sports  people too, or people just having fun with Ubuntu.

**Gnumeric Spreadsheet**
Gnumeric spreadsheet is a very useful spreadsheet program and one of the things I like most about it is that it has .csv files included in its 'save as' menu, and Gnumeric makes .csv files which are suitable for opening in Quantum GIS.
Gnumeric is very useful for viewing .csv files and editing them compared with a text editor because when the files are open in spreadsheet view it's easier to see which column is which, and it's also easy to select a column or range of cells and copy and paste the information somewhere else if needed. 
The other thing that makes gnumeric really indispensable is the fact that it can be used to open the .dbf files which come with the set of files that belong to every shapefile layer.
Gnumeric can't save changes to a .dbf file, but you can carry out any kind of editing including spreadsheet formula operations on your data and then save it as a csv again. From there you have the opportunity to open the .csv in QGIS and save as a shapefile again, either with a new file name or to overwrite your existing shapefile.


**Hardware Cost **
Equipment used: 

[LIST=1]
[*] EeePC 4g with added camera card for extra storage capacity, see also [Ubuntu NetBook  Install]("http://members.iinet.net/%7Eherman546/p28.html") for details about how I install Lucid Lynx in it, (if you're interested).
[*] Logitech Webcam C200, any webcam will do, but a camera would be better.
[*] USB GPS Receiver
[/LIST]
 
The USB receiver I'm using cost $40 au, the webcam cost $60 au and the EeePC is worth around $350 au probably at today's prices, so for a total of $450 au or so, I have a professional GPS/GIS setup capable of doing the work of other equipment some people might pay 10x the price for.  :D

---

### Post by Herman on 2010-08-01
:D Last week my new [Sony Cyber-shot® DSC-HX5V]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921666077169") Digital Camera arrived. 
It features GPS and a compass as well, and it automatically geotags all my photos with all the information I could ever wish for. 
I'm extremely pleased with it.

**How to View Your Geotagged Photos in Google Earth the Ubuntu Way** 
Not everybody has a camera that can geotag pictures yet, but as GPS receivers get smaller and more affordable and as the technology improves, more and more people will want to be able to take geotagged photos. Not everybody knows they need a geatagging camera yet, because the average person probably wouldn't know what to do with a geotagged photo anyway. Once it catches on it'll become a popular feature in cameras, at least I think so. 
I have read that a great number of mobile phones have the capability for taking geotagged photographs, maybe your mobile phone can do it but you're not aware of this feature, re-read your phone's documentation and find out.

Most of us are already familiar with Google Earth, and Picasa is another program from Google. Picasa is for managing digital photos.
I read we can use Picasa for displaying our geotagged photos in google earth and if we have photos that are not already geotagged, we can use Picasa for doing that too.
I tried installing Picasa for Linux in Ubuntu, but it's not in the repos. I had to go and get it from Google's Picasa for Linux website in the internet.
I was disappointed. The geotag feature doesn't work in Linux version of Picasa. By the looks of things I'm not the first Ubuntu user to find that out, [Program for geotagging photos/EXIF data?]("http://ubuntuforums.org/showthread.php?t=603606")

Fortunately though, Google Earth is a good, friendly open source software they even present a Google [KML Tutorial]("http://code.google.com/apis/kml/documentation/kml_tut.html")  to make it easy for us to learn how to do things for ourselves.
Here's a little script I wrote for creating a google earth .kml file in Ubuntu so all my geotagged photos will show up automatically in google earth, if you have a geotagging camera like I do then this script is for you,

kml-with-pictures.sh
```
#!/bin/sh
# a script for creating a kml file with geotagged photos
# by Herman H. Felderhof

# place this script inside a directory containing geotagged digital photographs and run it.
# The photographs need to have the filename extension .JPG for this script to work.
# If your photos are named with the .jpg filename extension I have another script to fix that.
# The file names themselves can only be eight characters long otherwise the script will need minor editing.
# The script will work in Australia and New Zealand but may (probably) need a little minor editing for most other parts of the world.
# Dependancies - you will need mkpasswd (sudo apt-get install makepasswd)
# Dependancies - you will need imagemagick (sudo apt-get install imagemagick)
# To Do: minor improvements like add proper date and time in kml, etc

###-if no processed file directory exists create one ###
if test -f ./myplaces.kml; then 
echo " 
      The myplaces.kml file already exists 
     "
else
##########- Start a new kml file with this header-#######################
echo '<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://www.opengis.net/kml/2.2" xmlns:gx="http://www.google.com/kml/ext/2.2" xmlns:kml="http://www.opengis.net/kml/2.2" xmlns:atom="http://www.w3.org/2005/Atom">
<Document>
    <name>default_my_places</name>
    <open>1</open>
    <Folder>
        <name>My Places</name>
        <open>1</open>
        <Style>
            <ListStyle>
                <listItemType>check</listItemType>
                <ItemIcon>
                    <state>open</state>
                    <href>:/mysavedplaces_open.png</href>
                </ItemIcon>
                <ItemIcon>
                    <state>closed</state>
                    <href>:/mysavedplaces_closed.png</href>
                </ItemIcon>
                <bgColor>00ffffff</bgColor>
                <maxSnippetLines>2</maxSnippetLines>
            </ListStyle>
        </Style>' >> ./myplaces.kml
fi
##############################################################

######-make a list of all JPG files in the current directory-####
ls -1 *.JPG > files_list

######- count the number of entries in the list-############
wc=`wc -l ./files_list | cut -d" " -f1`

######- if no files left in the in list, all done, so clean up and exit
if [ "$wc" = 0 ]; then
  echo "    </Folder>
</Document>
</kml>
       " >> ./myplaces.kml
  echo " 
        All Done ! 
       "
  sleep 1
  rm ./files_list
  now=$(date +"%y-%m-%d-%H-%M")
  echo "
        Cleaning up

        Creating directories and files for "$now"_processed
       "
mkdir ./"$now"_processed
mv *.kml ./"$now"_processed
mv image0* ./"$now"_processed
for f in *.jpg; do mv "$f" "${f%.jpg}.JPG"; done
  echo " 
        Thanks for using this script, bye-bye until next time.
       "
  sleep 4
  exit

######- if there are more files in the list say how many left to do ############
else
  echo " 
       "$wc" photos left to process
       "

######- get the name of the top file from the list and call it 'file.JPG'-############
file=`head -n 1 ./files_list | cut -b 1-8`
echo " 
       Currently working on: "$file".JPG
     " 
sleep 1

#########- read the GPS Coords from 'file.JPG'-############################
lat=`identify -format "%[EXIF:GPSLatitude]" $file.JPG`
echo $lat > tmp
sdeg=`cat tmp | cut -d"," -f1 | bc`
smin=`cat tmp | cut -d"," -f2 | bc`
ssec=`cat tmp | cut -d"," -f3 | bc -l | cut -b 1-7`

lon=`identify -format "%[EXIF:GPSLongitude]" $file.JPG`
echo $lon > tmp
edeg=`cat tmp | cut -d"," -f1 | bc`
emin=`cat tmp | cut -d"," -f2 | bc`
esec=`cat tmp | cut -d"," -f3 | bc -l | cut -b 1-7`
rm ./tmp

alt=`identify -format "%[EXIF:GPSAltitude]" $file.JPG | bc`

brg=`identify -format "%[EXIF:GPSImgDirection]" $file.JPG | bc`

echo " 
       Latitude $sdeg $smin $ssec S   Longitude $edeg $emin $esec E  Altitude $alt meters   Bearing $brg degrees magnetic  
     "
sleep 1

# echo $deg + $min/60 + $sec/3600 | bc -l
sdem=$(echo "$sdeg + $smin/60 + $ssec/3600" | bc -l | cut -b 1-9)
edem=$(echo "$edeg + $emin/60 + $esec/3600" | bc -l | cut -b 1-10)
echo "
       -$sdem, $edem
     " 
sleep 1

cp $file.JPG ./image0_roll_$wc.jpg
cp $file.JPG ./image0_thumb_$wc.jpg

mogrify -resize 144x109 ./image0_roll_$wc.jpg
mogrify -resize 400x300 ./image0_thumb_$wc.jpg

fileno=$(makepasswd --char=15)
echo "
       $fileno
     "
sleep 1
################- add the entry for the photo to the .kml file -################################
echo '        <Document>
            <name>My Picasa Pictures</name>
            <Style id="picasaDisplayNormal_'$fileno'">
                <IconStyle>
                    <Icon>
                        <href>image0_roll_'$wc'.jpg</href>
                    </Icon>
                </IconStyle>
                <LabelStyle>
                    <scale>0</scale>
                </LabelStyle>
                <BalloonStyle>
                    <text>$[description]</text>
                </BalloonStyle>
            </Style>
            <Style id="picasaDisplayHighlight_'$fileno'">
                <IconStyle>
                    <scale>2</scale>
                    <Icon>
                        <href>image0_roll_'$wc'.jpg</href>
                    </Icon>
                </IconStyle>
                <BalloonStyle>
                    <text>$[description]</text>
                </BalloonStyle>
            </Style>
            <StyleMap id="picasaDisplayStyleMap_'$fileno'">
                <Pair>
                    <key>normal</key>
                    <styleUrl>#picasaDisplayNormal_'$fileno'</styleUrl>
                </Pair>
                <Pair>
                    <key>highlight</key>
                    <styleUrl>#picasaDisplayHighlight_'$fileno'</styleUrl>
                </Pair>
            </StyleMap>
            <Folder>
                <name>Picasa - Saturday, 31 July 2010</name>
                <open>1</open>
                <Snippet maxLines="2">10.07.31-hx5v</Snippet>
                <description>Generated Saturday, 31 July 20103:27:09 PM</description>
                <Placemark>
                    <name>'$file'</name>
                    <Snippet maxLines="0"></Snippet>
                    <description><![CDATA[<table width="400">          
            <tr>
              <td>
                <img src="image0_thumb_'$wc'.jpg" width="400" height="300" >
                <br />
              </td>
            </tr>
            <tr><td>&nbsp;</td></tr>
            <tr>
              <td></td>
            </tr>
            <tr><td>&nbsp;</td></tr>
            <tr>
              <td>
                <em>Date : 31/07/2010 12:08:21 PM</em>
              </td>
            </tr>
            <tr>
              <td align="right">
                <hr />
                <a href="http://picasa.google.com/index.html"><img width="150" height="25" src="http://picasa.google.com/assets/logo_kmz.gif"></a>
              </td>
            </tr>
          </table>]]></description>
                    <LookAt>
                        <longitude>'$edem'</longitude>
                        <latitude>-'$sdem'</latitude>
                        <altitude>0</altitude>
                        <heading>0</heading>
                        <tilt>0</tilt>
                        <range>364.600288</range>
                    </LookAt>
                    <styleUrl>#picasaDisplayStyleMap_'$fileno'</styleUrl>
                    <Point>
                        <coordinates>'$edem',-'$sdem',0</coordinates>
                    </Point>
                </Placemark>
            </Folder>
        </Document>' >> ./myplaces.kml

##################################################################################################
 mv ./$file.JPG ./$file.jpg
 echo "
        Done !
 Next Please ... 

     "
  sleep 1
 ./kml-with-pictures.sh
fi

```NOTES:
This script depends on makepasswd, so you'll need to install 'makepasswd', (sudo apt-get install makepasswd).
This script must be named 'kml-with-pictures.sh', in order for it to  work properly.
The script will work without any editing in Australia and New Zealand, but it might require one or two minor edits to get it working properly in the northern hemisphere or where the number of characters in the coordinates is different.
Photos must have file names with eight characters and end in .JPG, (upper case), for this script to work properly. 
It works for me and my camera, and most people can easily be edit it to suit themselves. When I get more time I might improve it a little to make it more universal so it won't require editing for use in other parts of the world in case not everyone knows how. In the meantime if you need help, don't be afraid to ask and I'll do my best to help.

This script can be dropped into a directory full of geotagged photos and started. 
It doesn't matter how many photos you have in the directory, it  will read each photo's geotag and one at a time add them to a new .kml file and in a few minutes it can do a hundred or more photos.
You can do as many photos as you want and it gets the job done really fast!
Being free to be able to do this kind of thing is just another example of why it's best to use only open source operating systems and software and not bother wasting our time with proprietary programs.  :D

---

### Post by Herman on 2010-08-05
**A Fast Way to Turn your Foxtrot GPS .log files into GoogleEarth Paths**
Whenever we're traveling with our Ubuntu computers running Foxtrot GPS with our USB GPS receiver plugged in and we click 'enable track logging', a .log file will be created in our Maps directory.

It's easy in Ubuntu to write a script to read our Foxtrot GPS .log files and create .kml files to open with Google Earth to show our paths.

log-to-kml.sh
```
#!/bin/bash
# a script for reading tango gps log files and adding the track data to google earth kml files
# by Herman H Felderhof 
# just copy this script and paste in inside a directory full of Foxtrot gps log files and run it

###############################################################################################
ls -1 *.log > files_list
wc=`wc -l ./files_list | cut -d" " -f1`
if [ "$wc" = 0 ]; then
  echo " All Done ! "
  sleep 1
  rm ./files_list
  now=$(date +"%y-%m-%d-%H-%M")
  echo "
        Cleaning up

        Creating directories and files for "$now"_processed
       "
sleep 3
mkdir ./"$now"_processed
mv *.kml ./"$now"_processed
for f in *.LOG; do mv "$f" "${f%.LOG}.log"; done
  echo " 
        Thanks for using this script, bye-bye until next time.
       "
  sleep 4
  exit

#############################################################################################
else
  echo " "$wc" log files left to process"
file=`head -n 1 ./files_list | cut -b 1-15`
echo " Currently working on: "$file".log" 
sleep 1

#############################################################################################

cat $file.log | cut -d"," -f2 >> testfile-a
cat $file.log | cut -d"," -f1 >> testfile-b
paste -d',' testfile-a testfile-b >> testfile-c
rm testfile-a
rm testfile-b
sed -i '''s/$/,0/' testfile-c

echo '<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://www.opengis.net/kml/2.2" xmlns:gx="http://www.google.com/kml/ext/2.2" xmlns:kml="http://www.opengis.net/kml/2.2" xmlns:atom="http://www.w3.org/2005/Atom">
<Document>
    <name>default_my_places</name>
    <open>1</open>
    <Style id="sn_ylw-pushpin">
        <LineStyle>
            <width>3</width>
        </LineStyle>
    </Style>
    <StyleMap id="msn_ylw-pushpin">
        <Pair>
            <key>normal</key>
            <styleUrl>#sn_ylw-pushpin</styleUrl>
        </Pair>
        <Pair>
            <key>highlight</key>
            <styleUrl>#sh_ylw-pushpin</styleUrl>
        </Pair>
    </StyleMap>
    <Style id="sh_ylw-pushpin">
        <IconStyle>
            <scale>1.2</scale>
        </IconStyle>
        <LineStyle>
            <width>6</width>
        </LineStyle>
    </Style>
    <Folder>
        <name>My Places</name>
        <open>1</open>
        <Style>
            <ListStyle>
                <listItemType>check</listItemType>
                <ItemIcon>
                    <state>open</state>
                    <href>/usr/lib32/googleearth/resources/mysavedplaces_open.png</href>
                </ItemIcon>
                <ItemIcon>
                    <state>closed</state>
                    <href>/usr/lib32/googleearth/resources/mysavedplaces_closed.png</href>
                </ItemIcon>
                <bgColor>00ffffff</bgColor>
                <maxSnippetLines>2</maxSnippetLines>
            </ListStyle>
        </Style>
        <Placemark>
            <name>Untitled Path</name>
            <styleUrl>#msn_ylw-pushpin</styleUrl>
            <LineString>
                <tessellate>1</tessellate>
                <coordinates>' >> $file.kml

cat testfile-c >> $file.kml
rm testfile-c
echo ' </coordinates>
            </LineString>
        </Placemark>
    </Folder>
</Document>
</kml> ' >> $file.kml

 mv ./$file.log ./$file.LOG
 echo " Done !
 Next Please ... 

     "
  sleep 1
 ./log-to-kml.sh
fi

```This script needs to be named 'log-to-kml.sh', in order for it to run repeatedly until it processes all the .log files in a directory.

Have fun with Ubuntu and your USB GPS! :D

---

### Post by Herman on 2011-05-03
The GPS Tracker tool in Quantum GIS is really cool, and it works great with my USB GPS dongle. There's already a pretty good web tutorial about how to use it, here is a link
[GPS Tracker tool in QGIS trunk]("http://linfiniti.com/2010/01/gps-tracker-tool-in-qgis-trunk/").

It's well worth practicing with this, GIS is a subject that not everyone seems to be clued into yet. The advantage of using a GIS is that we are able to use the built in database in each ESRI Shapefile layer collect and store mappable data including any relevant details about whatever project we're working on at the time. Using QGIS's new GPS Tracker tool makes it easy for anyone to enter their data directly into their GIS on the fly, as it is captured. The only trick we need to know is how to set up the layer's database at the time we create the layer, ( or it can also be edited later).

---

### Post by Herman on 2011-06-05
After you returned from that 4wd, horse or bike ride or hike, did you ever want to know how far you rode or walked? 
How often do you travel in perfectly straight lines?
Do you want to be able to compare different routes? 
Did you find that making the number of measurements on a path with curves and corners using a map measuring tool designed for straight lines a tedious process? 
Would you like to be able to tell your friends exactly how far along a road or trail they'll see some point of interest if they don't have a GPS so map coordinates won't help them?
Do you need distance measurements along a road for engineering related calculations such as how long is the gravel section to work out how much to pay the grader contractor or how much will it cost to pave and seal that bad part of the road? 

The following python script will read a Foxtrot GPS log file and output a new .csv file that follows exactly the same path as your original Foxtrot GPS log but with your GPS track divided into even 20m intervals.
When you load this .csv in Quantum GIS you can have Quantum GIS display the distances, the forward or back azimuths, elevation or percent grade for each point.
Distance measurements use vincenty's inverse formula so are about as accurate as can be, and you can change to your own county's CRS if needed.
Distance correction for slopes or grades is built in, giving as close as possible to the actual ground measurements. 
The Z values themselves and percent grade results are subject to the accuracy of the input, and most GPSs struggle a bit with the Z values. Grades and elevations are important for hikers and cyclists and almost everyone so it is important they be included and they should average out okay. 

I run mine in IDLE, the python GUI, (install by apt-get or Ubuntu Software Center). To get it to work, you just need to replace the file name of the Foxtrot GPS '20110502_081415.log'  in line 57 with the name of your own particular Foxtrot GPS log. It's easiest if a copy of the script is located in the same directory as your Foxtrot GPS logs unless you prefer to type a file path before the file name.

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

###   This program is for creating regular divisions in a non-straight line,
###   such as a road, path or trail represented as a GPS track log.
###    Copyright (C) 2011  Herman H Felderhof
###    email herman546(at)iinet.net.au

###    This program is free software: you can redistribute it and/or modify
###    it under the terms of the GNU General Public License as published by
###    the Free Software Foundation, either version 3 of the License, or
###    (at your option) any later version.

###    This program is distributed in the hope that it will be useful,
###    but WITHOUT ANY WARRANTY; without even the implied warranty of
###    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
###    GNU General Public License for more details.

###    You should have received a copy of the GNU General Public License
###    along with this program.  If not, see <http://www.gnu.org/licenses/>.

###     +===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+
## This program is for dividing up a non-straight line (such as a road) into equal distances.
## It's also good for cleaning up a GPS track or similar list of coordinates such as a list
## of vertices from a line in a GIS map. The output gives you new coordinates which will fall exactly along
## the original line, but with apexes spaced at regular intervals. You can specify the distance between
## apexes as your 'chain = x' (metres) variable. The program also counts the distances progressively and 
## gives you a column of chainages which you can use for measuring with. These can be made to appear as 
## labels in Quantum GIS when you want to see how far along the non-straight line an item of interest is.
###     +===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+

### we will need the math module later, lets get it ready now

import math
import csv
import numpy as NX

# You can change the number below to set how far apart you want your new points to be
chain = 20

# you can make it start counting from a non-zero chainage by editing the number below
accum = 0

# open the text file and read it all into memory
# to open a different text file, edit filename in the line fh = open ( "<filename>");
log = []

with open('20110502_081415.log', 'rb') as f:
    reader = csv.reader(f)
    for row in reader:
        log.append (row)
#log = log[::-2]  # Reverses the sequence
#log.pop(0)       # uncomment only if top line is header

f=open('chainmaker_output.csv','a')
f.write('chain,X_Coords_WGS84,Y_Coords_WGS84,Z_Coords,grade,fwd_azimuth,rev_azimuth,telltale\n')
f.close()

excess = 0
shortfall = 0
cos_sq_alpha = 0
cos_ii_sigma_m = 0
cos_sigma = 0
sigma = 0
pos_ii = 0

### enough preliminaries, let the main loop begin

#for i in log:
counter = 0
while counter <(len(log)-2):
         
    ### read the first two lines of the text file back from memory and grab the coords out
    pos_i = log[0]
    pos_ii = log[1]
   
    # TangoGPS.log files Y,X,Z cols 0,1,2
    # Ricoh .LOG files Y,X,Z cols 1,0,2
    # STR0000.CSV files Y,X cols 3,4
    y1 = pos_i[0]   
    y1 = float (y1)
    x1 = pos_i[1] 
    x1 = float (x1)
    z1 = pos_i[2]
    z1 = float (z1)
       
    y2 = pos_ii[0]
    y2 = float (y2)
    x2 = pos_ii[1]
    x2 = float (x2)
    z2 = pos_ii[2]
    z2 = float (z2)

    phi1=math.radians(y1)
    lembda1=math.radians(x1)
    phi2=math.radians(y2)
    lembda2=math.radians(x2)

    if phi1 != phi2 and lembda1 != lembda2:
            
    ### WGS-84__________| a = 6378137 m (±2 m)_| b &#8776; 6356752.314245 m__| f &#8776; 1/298.257223563
    ### GRS-80__________| a = 6378137 m________| b &#8776; 6356752.314140 m__| f = 1/298.257222101
    ### Airy 1830_______| a = 6377563.396 m____| b = 6356256.910 m_____| f &#8776; 1/299.3249646
    ### Int_nat&#8217;l 1924__| a = 6 378 388 m______| b &#8776; 6356911.946 m_____| f = 1/297
    ### Clarke mod.1880_| a = 6 378 249.145 m__| b &#8776; 6356514.86955 m___| f = 1/293.465
    ### GRS-67__________| a = 6 378 160 m______| b &#8776; 6356774.719 m_____| f = 1/298.247167

    ### GRS-80 ellipsoid params
    ### a = major semiaxis of the ellipsoid
    ### b = minor semiaxis of the ellipsoid 
    ### f = flattening (a&#8722;b)/a      
        a = 6378137
        b = 6356752.314140
        f = 1/298.257222101
        
    ##########################################################################################
    ########################## START of Vincenty's Inverse Formulae ##########################
    # from: http://www.koders.com/python/fid0A930D7924AE856342437CA1F5A9A3EC0CAEACE2.aspx
    # --------------------------------------------------------------------- 
    # |                                                                    |
    # |     geodetic.py -  a collection of geodetic functions              |
    # |                                                                    |
    # --------------------------------------------------------------------- 
    # 
    # 
    # ----------------------------------------------------------------------
    # | Algrothims from Geocentric Datum of Australia Technical Manual      |
    # |                                                                     |
    # | http://www.anzlic.org.au/icsm/gdatum/chapter4.html                  |
    # |                                                                     |
    # | This page last updated 11 May 1999                                  |
    # |                                                                     |
    # | Computations on the Ellipsoid                                       |
    # |                                                                     |
    # | There are a number of formulae that are available                   |
    # | to calculate accurate geodetic positions,                           |
    # | azimuths and distances on the ellipsoid.                            |
    # |                                                                     |
    # | Vincenty's formulae (Vincenty, 1975) may be used                    |
    # | for lines ranging from a few cm to nearly 20,000 km,                |
    # | with millimetre accuracy.                                           |
    # | The formulae have been extensively tested                           |
    # | for the Australian region, by comparison with results               |
    # | from other formulae (Rainsford, 1955 & Sodano, 1965).               |
    # |                                                                     |
    # | * Inverse problem: azimuth and distance from known                  |
    # |                     latitudes and longitudes                        |
    # | * Direct problem: Latitude and longitude from known                 |
    # |                     position, azimuth and distance.                 |
    # | * Sample data                                                       |
    # | * Excel spreadsheet                                                 |
    # |                                                                     |
    # | Vincenty's Inverse formulae                                         |
    # | Given: latitude and longitude of two points                         |
    # |                     (phi1, lembda1 and phi2, lembda2),              |
    # | Calculate: the ellipsoidal distance (s) and                         |
    # | forward and reverse azimuths between the points (alpha12, alpha21). |
    # |                                                                     |
    # ---------------------------------------------------------------------- 

        two_pi = 2.0*math.pi

        b = a * (1.0 - f)

        TanU1 = (1-f) * math.tan( phi1 )
        TanU2 = (1-f) * math.tan( phi2 )
        
        U1 = math.atan(TanU1)
        U2 = math.atan(TanU2)

        lembda = lembda2 - lembda1
        last_lembda = -4000000.0                # an impossibe value
        omega = lembda

        # Iterate the following equations, 
        #  until there is no significant change in lembda
        
        while ( last_lembda < -3000000.0 or lembda != 0 and abs( (last_lembda - lembda)/lembda) > 1.0e-9 ) :

            sqr_sin_sigma = pow( math.cos(U2) * math.sin(lembda), 2) + \
                pow( (math.cos(U1) * math.sin(U2) - \
                math.sin(U1) *  math.cos(U2) * math.cos(lembda) ), 2 )
            
            Sin_sigma = math.sqrt( sqr_sin_sigma )
            
            if (Sin_sigma == 0):
                break
            
            Cos_sigma= math.sin(U1) * math.sin(U2) + math.cos(U1) * math.cos(U2) * math.cos(lembda)
                      
            sigma = math.atan2( Sin_sigma, Cos_sigma )
            
            Sin_alpha = math.cos(U1) * math.cos(U2) * math.sin(lembda) / math.sin(sigma)
            alpha = math.asin( Sin_alpha )
                      
            Cos2sigma_m = math.cos(sigma) - (2 * math.sin(U1) * math.sin(U2) / pow(math.cos(alpha), 2) )
          
            C = (f/16) * pow(math.cos(alpha), 2) * (4 + f * (4 - 3 * pow(math.cos(alpha), 2)))
          
            last_lembda = lembda
          
            lembda = omega + (1-C) * f * math.sin(alpha) * (sigma + C * math.sin(sigma) * \
                    (Cos2sigma_m + C * math.cos(sigma) * (-1 + 2 * pow(Cos2sigma_m, 2) )))
        

        u2 = pow(math.cos(alpha),2) * (a*a-b*b) / (b*b)
        
        A = 1 + (u2/16384) * (4096 + u2 * (-768 + u2 * (320 - 175 * u2)))
        
        B = (u2/1024) * (256 + u2 * (-128+ u2 * (74 - 47 * u2)))
        
        delta_sigma = B * Sin_sigma * (Cos2sigma_m + (B/4) * \
                (Cos_sigma * (-1 + 2 * pow(Cos2sigma_m, 2) ) - \
                (B/6) * Cos2sigma_m * (-3 + 4 * sqr_sin_sigma) * \
                (-3 + 4 * pow(Cos2sigma_m,2 ) )))
        
        s = b * A * (sigma - delta_sigma)

        ### the azimuths (aka bearings, headings or directions) ###
        ### alpha12 will be the forwards azimuth and alpha21 will be the back azimuth ###
              
        alpha12 = math.atan2( (math.cos(U2) * math.sin(lembda)), \
                math.cos(U1) * math.sin(U2) - math.sin(U1) * math.cos(U2) * math.cos(lembda))
        
        alpha21 = math.atan2( (math.cos(U1) * math.sin(lembda)), \
                (-math.sin(U1) * math.cos(U2) + math.cos(U1) * math.sin(U2) * math.cos(lembda)))

        if ( alpha12 < 0.0 ) : 
                alpha12 =  alpha12 + two_pi
        if ( alpha12 > two_pi ) : 
                alpha12 = alpha12 - two_pi

        alpha21 = alpha21 + two_pi / 2.0
        if ( alpha21 < 0.0 ) : 
                alpha21 = alpha21 + two_pi
        if ( alpha21 > two_pi ) : 
                alpha21 = alpha21 - two_pi

        alpha12 = int(round(math.degrees(alpha12),0))
        alpha21 = int(round(math.degrees(alpha21),0))

        
        ###################### END of Vincenty's Inverse formulae ###########################
        #####################################################################################

        d_metres=math.sqrt(((z2-z1)*(z2-z1))+(s*s))       
        #d_metres = s

        # difference in latitudes between points a and b
        # difference in longitudes between points a and b
        bigdelta_y = y2 - y1
        bigdelta_x = x2 - x1
        bigdelta_z = z2 - z1

        perct_gr = 100*(bigdelta_z/s)
        
        # If the coordinates are less than the specified distance, forget 2nd line and grab a new 2nd line
        if d_metres < chain:
            log.pop(1)
        
        else:
            if excess == 0:
            ## Work out how many divisions will be required for the distance / chainages
                hops_deci = d_metres / chain
                num_hops = math.floor (hops_deci)
                shortfall = d_metres % chain
                excess = chain - shortfall
            ##stop when you get to the nearest even multiple
                stop = num_hops * chain
                  
                count = 0
                while count < stop:
                    sml_delta_y = bigdelta_y / hops_deci
                    sml_delta_x = bigdelta_x / hops_deci
                    sml_delta_z = bigdelta_z / hops_deci
                    newlat = y1 + sml_delta_y  
                    newlon = x1 + sml_delta_x
                    new_elev = z1 + sml_delta_z
                    accum = accum + chain
                    print `accum`+','+ `newlon`+','+`newlat`+','+`int(new_elev)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 0'
                    value = (`accum`+','+ `newlon`+','+`newlat`+','+`int(new_elev)`+','+`int(perct_gr)`+','+ `alpha12`+','+`alpha21`+', 0'+'\n')
                    s = str(value)
                    f=open('chainmaker_output.csv','a')
                    f.write(s)
                    f.close()
                    count = count + chain
                    y1 = newlat
                    x1 = newlon
                    z1 = new_elev
                                        
            else:
                ### Now work out how many divisions will be required for the distance / chainages
                hop_ex = d_metres / excess
                sml_delta_y = bigdelta_y / hop_ex
                sml_delta_x = bigdelta_x / hop_ex
                sml_delta_z = bigdelta_z / hop_ex
                newlat_i = y1 + sml_delta_y  
                newlon_i = x1 + sml_delta_x
                new_elev_i = z1 + sml_delta_z
                accum = accum + chain
                print `accum`+','+`newlon_i`+','+`newlat_i`+','+`int(new_elev_i)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 1'
                value = (`accum`+','+ `newlon_i`+','+`newlat_i`+','+`int(new_elev_i)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 1'+'\n')
                s = str(value)
                f=open('chainmaker_output.csv','a')
                f.write(s)
                f.close()
                        
                b_metres = d_metres - excess
                hops_deci_i = b_metres / chain
                num_hops = math.floor (hops_deci_i)
                ## stop when you get to the nearest even multiple
                stop = num_hops * chain
                excess = ((chain * num_hops)+ chain) - b_metres
                shortfall = b_metres % chain

                bigdelta_y = y2 - newlat_i
                bigdelta_x = x2 - newlon_i
          
                count = 0
                while count < stop:
                    sml_delta_y = bigdelta_y / hops_deci_i
                    sml_delta_x = bigdelta_x / hops_deci_i
                    sml_delta_z = bigdelta_z / hops_deci_i
                    newlat_ii = newlat_i + sml_delta_y  
                    newlon_ii = newlon_i + sml_delta_x
                    new_elev_iii = new_elev_i + sml_delta_z 
                    accum = accum + chain
                    print `accum`+','+`newlon_ii`+','+`newlat_ii`+','+`int(new_elev_iii)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 8'
                    value = (`accum`+','+ `newlon_ii`+','+`newlat_ii`+','+`int(new_elev_iii)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 8'+'\n')
                    s = str(value)
                    f=open('chainmaker_output.csv','a')
                    f.write(s)
                    f.close()
                    count = count + chain
                    newlat_i = newlat_ii
                    newlon_i = newlon_ii
                    y1 = newlat_i
                    x1 = newlon_i
                    z1 = new_elev_iii
            log.pop(0)
    else:
        log.pop(1)
counter = counter +1
total_dist=accum+excess
print `total_dist`
```This one does exactly the same thing but it creates a .kml file for opening in Google Earth,
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

###   This program is for creating regular divisions in a non-straight line,
###   such as a road, path or trail represented as a GPS track log.
###    Copyright (C) 2011  Herman H Felderhof
###    email herman546(at)iinet.net.au

###    This program is free software: you can redistribute it and/or modify
###    it under the terms of the GNU General Public License as published by
###    the Free Software Foundation, either version 3 of the License, or
###    (at your option) any later version.

###    This program is distributed in the hope that it will be useful,
###    but WITHOUT ANY WARRANTY; without even the implied warranty of
###    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
###    GNU General Public License for more details.

###    You should have received a copy of the GNU General Public License
###    along with this program.  If not, see <http://www.gnu.org/licenses/>.

###     +===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+
## This program is for dividing up a non-straight line (such as a road) into equal distances.
## It's also good for cleaning up a GPS track or similar list of coordinates such as a list
## of vertices from a line in a GIS map. The output gives you new coordinates which will fall exactly along
## the original line, but with apexes spaced at regular intervals. You can specify the distance between
## apexes as your 'chain = x' (metres) variable. The program also counts the distances progressively and 
## gives you a column of chainages which you can use for measuring with. 
##
###     +===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+===+

### we will need the math module later, lets get it ready now

import math
import csv
import numpy as NX

# You can change the number below to set how far apart you want your new points to be
chain = 20

# you can make it start counting from a non-zero chainage by editing the number below
accum = 0

# open the text file and read it all into memory
# to open a different text file, edit filename in the line fh = open ( "<filename>");
log = []

with open('20110529_134743.log', 'rb') as f:
    reader = csv.reader(f)
    for row in reader:
        log.append (row)
#log = log[::-2]  # Reverses the sequence
#log.pop(0)       # uncomment only if top line is header

f=open('chainmaker_output.kml','a')
f.write('<?xml version="1.0" encoding="UTF-8"?>\n'+
'<kml xmlns="http://www.opengis.net/kml/2.2" xmlns:gx="http://www.google.com/kml/ext/2.2"'+
' xmlns:kml="http://www.opengis.net/kml/2.2" xmlns:atom="http://www.w3.org/2005/Atom">\n'+
'<Document>\n')
f.close()

excess = 0
shortfall = 0
cos_sq_alpha = 0
cos_ii_sigma_m = 0
cos_sigma = 0
sigma = 0
pos_ii = 0

### enough preliminaries, let the main loop begin

#for i in log:
counter = 0
while counter <(len(log)-2):
         
    ### read the first two lines of the text file back from memory and grab the coords out
    pos_i = log[0]
    pos_ii = log[1]
   
    # TangoGPS.log files Y,X,Z cols 0,1,2
    # Ricoh .LOG files Y,X,Z cols 1,0,2
    # STR0000.CSV files Y,X cols 3,4
    y1 = pos_i[0]   
    y1 = float (y1)
    x1 = pos_i[1] 
    x1 = float (x1)
    z1 = pos_i[2]
    z1 = float (z1)
       
    y2 = pos_ii[0]
    y2 = float (y2)
    x2 = pos_ii[1]
    x2 = float (x2)
    z2 = pos_ii[2]
    z2 = float (z2)

    phi1=math.radians(y1)
    lembda1=math.radians(x1)
    phi2=math.radians(y2)
    lembda2=math.radians(x2)

    if phi1 != phi2 and lembda1 != lembda2:
            
    ### WGS-84__________| a = 6378137 m (±2 m)_| b &#8776; 6356752.314245 m__| f &#8776; 1/298.257223563
    ### GRS-80__________| a = 6378137 m________| b &#8776; 6356752.314140 m__| f = 1/298.257222101
    ### Airy 1830_______| a = 6377563.396 m____| b = 6356256.910 m_____| f &#8776; 1/299.3249646
    ### Int_nat&#8217;l 1924__| a = 6 378 388 m______| b &#8776; 6356911.946 m_____| f = 1/297
    ### Clarke mod.1880_| a = 6 378 249.145 m__| b &#8776; 6356514.86955 m___| f = 1/293.465
    ### GRS-67__________| a = 6 378 160 m______| b &#8776; 6356774.719 m_____| f = 1/298.247167

    ### GRS-80 ellipsoid params
    ### a = major semiaxis of the ellipsoid
    ### b = minor semiaxis of the ellipsoid 
    ### f = flattening (a&#8722;b)/a      
        #a = 6378137.0
        #b = 6356752.314140
        #f = 1/298.257222101
        a = 6378137.0
        b = 6356752.3142
        f = (a-b)/a
        
    ##########################################################################################
    ########################## START of Vincenty's Inverse Formulae ##########################
    # from: http://www.koders.com/python/fid0A930D7924AE856342437CA1F5A9A3EC0CAEACE2.aspx
    # --------------------------------------------------------------------- 
    # |                                                                    |
    # |     geodetic.py -  a collection of geodetic functions              |
    # |                                                                    |
    # --------------------------------------------------------------------- 
    # 
    # 
    # ----------------------------------------------------------------------
    # | Algrothims from Geocentric Datum of Australia Technical Manual      |
    # |                                                                     |
    # | http://www.anzlic.org.au/icsm/gdatum/chapter4.html                  |
    # |                                                                     |
    # | This page last updated 11 May 1999                                  |
    # |                                                                     |
    # | Computations on the Ellipsoid                                       |
    # |                                                                     |
    # | There are a number of formulae that are available                   |
    # | to calculate accurate geodetic positions,                           |
    # | azimuths and distances on the ellipsoid.                            |
    # |                                                                     |
    # | Vincenty's formulae (Vincenty, 1975) may be used                    |
    # | for lines ranging from a few cm to nearly 20,000 km,                |
    # | with millimetre accuracy.                                           |
    # | The formulae have been extensively tested                           |
    # | for the Australian region, by comparison with results               |
    # | from other formulae (Rainsford, 1955 & Sodano, 1965).               |
    # |                                                                     |
    # | * Inverse problem: azimuth and distance from known                  |
    # |                     latitudes and longitudes                        |
    # | * Direct problem: Latitude and longitude from known                 |
    # |                     position, azimuth and distance.                 |
    # | * Sample data                                                       |
    # | * Excel spreadsheet                                                 |
    # |                                                                     |
    # | Vincenty's Inverse formulae                                         |
    # | Given: latitude and longitude of two points                         |
    # |                     (phi1, lembda1 and phi2, lembda2),              |
    # | Calculate: the ellipsoidal distance (s) and                         |
    # | forward and reverse azimuths between the points (alpha12, alpha21). |
    # |                                                                     |
    # ---------------------------------------------------------------------- 

        two_pi = 2.0*math.pi

        b = a * (1.0 - f)

        TanU1 = (1-f) * math.tan( phi1 )
        TanU2 = (1-f) * math.tan( phi2 )
        
        U1 = math.atan(TanU1)
        U2 = math.atan(TanU2)

        lembda = lembda2 - lembda1
        last_lembda = -4000000.0                # an impossibe value
        omega = lembda

        # Iterate the following equations, 
        #  until there is no significant change in lembda
        
        while ( last_lembda < -3000000.0 or lembda != 0 and abs( (last_lembda - lembda)/lembda) > 1.0e-9 ) :

            sqr_sin_sigma = pow( math.cos(U2) * math.sin(lembda), 2) + \
                pow( (math.cos(U1) * math.sin(U2) - \
                math.sin(U1) *  math.cos(U2) * math.cos(lembda) ), 2 )
            
            Sin_sigma = math.sqrt( sqr_sin_sigma )
            
            if (Sin_sigma == 0):
                break
            
            Cos_sigma= math.sin(U1) * math.sin(U2) + math.cos(U1) * math.cos(U2) * math.cos(lembda)
                      
            sigma = math.atan2( Sin_sigma, Cos_sigma )
            
            Sin_alpha = math.cos(U1) * math.cos(U2) * math.sin(lembda) / math.sin(sigma)
            alpha = math.asin( Sin_alpha )
                      
            Cos2sigma_m = math.cos(sigma) - (2 * math.sin(U1) * math.sin(U2) / pow(math.cos(alpha), 2) )
          
            C = (f/16) * pow(math.cos(alpha), 2) * (4 + f * (4 - 3 * pow(math.cos(alpha), 2)))
          
            last_lembda = lembda
          
            lembda = omega + (1-C) * f * math.sin(alpha) * (sigma + C * math.sin(sigma) * \
                    (Cos2sigma_m + C * math.cos(sigma) * (-1 + 2 * pow(Cos2sigma_m, 2) )))
        

        u2 = pow(math.cos(alpha),2) * (a*a-b*b) / (b*b)
        
        A = 1 + (u2/16384) * (4096 + u2 * (-768 + u2 * (320 - 175 * u2)))
        
        B = (u2/1024) * (256 + u2 * (-128+ u2 * (74 - 47 * u2)))
        
        delta_sigma = B * Sin_sigma * (Cos2sigma_m + (B/4) * \
                (Cos_sigma * (-1 + 2 * pow(Cos2sigma_m, 2) ) - \
                (B/6) * Cos2sigma_m * (-3 + 4 * sqr_sin_sigma) * \
                (-3 + 4 * pow(Cos2sigma_m,2 ) )))
        
        s = b * A * (sigma - delta_sigma)

        ### the azimuths (aka bearings, headings or directions) ###
        ### alpha12 will be the forwards azimuth and alpha21 will be the back azimuth ###
              
        alpha12 = math.atan2( (math.cos(U2) * math.sin(lembda)), \
                math.cos(U1) * math.sin(U2) - math.sin(U1) * math.cos(U2) * math.cos(lembda))
        
        alpha21 = math.atan2( (math.cos(U1) * math.sin(lembda)), \
                (-math.sin(U1) * math.cos(U2) + math.cos(U1) * math.sin(U2) * math.cos(lembda)))

        if ( alpha12 < 0.0 ) : 
                alpha12 =  alpha12 + two_pi
        if ( alpha12 > two_pi ) : 
                alpha12 = alpha12 - two_pi

        alpha21 = alpha21 + two_pi / 2.0
        if ( alpha21 < 0.0 ) : 
                alpha21 = alpha21 + two_pi
        if ( alpha21 > two_pi ) : 
                alpha21 = alpha21 - two_pi

        alpha12 = int(round(math.degrees(alpha12),0))
        alpha21 = int(round(math.degrees(alpha21),0))

        
        ###################### END of Vincenty's Inverse formulae ###########################
        #####################################################################################

        d_metres=math.sqrt(((z2-z1)*(z2-z1))+(s*s))       
        #d_metres = s

        # difference in latitudes between points a and b
        # difference in longitudes between points a and b
        bigdelta_y = y2 - y1
        bigdelta_x = x2 - x1
        bigdelta_z = z2 - z1

        perct_gr = 100*(bigdelta_z/s)
        
        # If the coordinates are less than the specified distance, forget 2nd line and grab a new 2nd line
        if d_metres < chain:
            log.pop(1)
        
        else:
            if excess == 0:
            ## Work out how many divisions will be required for the distance / chainages
                hops_deci = d_metres / chain
                num_hops = math.floor (hops_deci)
                shortfall = d_metres % chain
                excess = chain - shortfall
            ##stop when you get to the nearest even multiple
                stop = num_hops * chain
                  
                count = 0
                while count < stop:
                    sml_delta_y = bigdelta_y / hops_deci
                    sml_delta_x = bigdelta_x / hops_deci
                    sml_delta_z = bigdelta_z / hops_deci
                    newlat = y1 + sml_delta_y  
                    newlon = x1 + sml_delta_x
                    new_elev = z1 + sml_delta_z
                    accum = accum + chain
                    print `accum`+','+ `newlon`+','+`newlat`+','+`int(new_elev)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 0'
                    value = (
'        <name>chainage.kml</name>\n'+
'        <Style id="sn_shaded_dot">/n'+
'                <IconStyle>\n'+
'                        <scale>0.3</scale>\n'+
'                        <Icon>\n'+
'                                <href>http://maps.google.com/mapfiles/kml/shapes/shaded_dot.png</href>\n'+
'                        </Icon>\n'+
'                </IconStyle>\n'+
'                <ListStyle>\n'+
'                </ListStyle>\n'+
'        </Style>\n'+
'        <Placemark>\n'+
'                <name>'+`accum`+'</name>\n'+
'                <description>chainage: '+`accum`+'\n'+
'elevation: '+`int(new_elev)`+'\n'+
'percent grade: '+`int(perct_gr)`+'\n'+
'forward azimuth : '+`alpha12`+'\n'+
'backward azimuth: '+`alpha21`+'</description>\n'+
'                <LookAt>\n'+
'                        <longitude>'+`newlon`+'</longitude>\n'+
'                        <latitude>'+`newlat`+'</latitude>\n'+
'                        <altitude>0</altitude>\n'+
'                        <heading>2.821165660590745</heading>\n'+
'                        <tilt>0</tilt>\n'+
'                        <range>275.175070801221</range>\n'+
'                        <altitudeMode>relativeToGround</altitudeMode>\n'+
'                        <gx:altitudeMode>relativeToSeaFloor</gx:altitudeMode>\n'+
'                </LookAt>\n'+
'                <styleUrl>#sn_shaded_dot</styleUrl>\n'+
'                <Point>\n'+
'                        <coordinates>'+`newlon`+','+`newlat`+',0</coordinates>\n'+
'                </Point>\n'+
'        </Placemark>\n')
                    s = str(value)
                    f=open('chainmaker_output.kml','a')
                    f.write(s)
                    f.close()
                    count = count + chain
                    y1 = newlat
                    x1 = newlon
                    z1 = new_elev
            

            else:
                ### Now work out how many divisions will be required for the distance / chainages
                hop_ex = d_metres / excess
                sml_delta_y = bigdelta_y / hop_ex
                sml_delta_x = bigdelta_x / hop_ex
                sml_delta_z = bigdelta_z / hop_ex
                newlat_i = y1 + sml_delta_y  
                newlon_i = x1 + sml_delta_x
                new_elev_i = z1 + sml_delta_z
                accum = accum + chain
                print `accum`+','+`newlon_i`+','+`newlat_i`+','+`int(new_elev_i)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 1'
                value = (
'                    <name>one.kml</name>\n'+
'    <Style id="sn_shaded_dot">/n'+
'        <IconStyle>\n'+
'            <scale>0.3</scale>\n'+
'            <Icon>\n'+
'                <href>http://maps.google.com/mapfiles/kml/shapes/shaded_dot.png</href>\n'+
'            </Icon>\n'+
'        </IconStyle>\n'+
'        <ListStyle>\n'+
'        </ListStyle>\n'+
'    </Style>\n'+
'    <Placemark>\n'+
'        <name>'+`accum`+'</name>\n'+
'        <description>chainage: '+`accum`+'\n'+
'elevation: '+`int(new_elev_i)`+'\n'+
'percent grade: '+`int(perct_gr)`+'\n'+
'forward azimuth : '+`alpha12`+'\n'+
'backward azimuth: '+`alpha21`+'</description>\n'+
'        <LookAt>\n'+
'            <longitude>'+`newlon_i`+'</longitude>\n'+
'            <latitude>'+`newlat_i`+'</latitude>\n'+
'            <altitude>0</altitude>\n'+
'            <heading>2.821165660590745</heading>\n'+
'            <tilt>0</tilt>\n'+
'            <range>275.175070801221</range>\n'+
'            <altitudeMode>relativeToGround</altitudeMode>\n'+
'            <gx:altitudeMode>relativeToSeaFloor</gx:altitudeMode>\n'+
'        </LookAt>\n'+
'        <styleUrl>#sn_shaded_dot</styleUrl>\n'+
'        <Point>\n'+
'            <coordinates>'+`newlon_i`+','+`newlat_i`+',0</coordinates>\n'+
'        </Point>\n'+
'    </Placemark>\n')
                s = str(value)
                f=open('chainmaker_output.kml','a')
                f.write(s)
                f.close()
                        
                b_metres = d_metres - excess
                hops_deci_i = b_metres / chain
                num_hops = math.floor (hops_deci_i)
                ## stop when you get to the nearest even multiple
                stop = num_hops * chain
                excess = ((chain * num_hops)+ chain) - b_metres
                shortfall = b_metres % chain

                bigdelta_y = y2 - newlat_i
                bigdelta_x = x2 - newlon_i
          
                count = 0
                while count < stop:
                    sml_delta_y = bigdelta_y / hops_deci_i
                    sml_delta_x = bigdelta_x / hops_deci_i
                    sml_delta_z = bigdelta_z / hops_deci_i
                    newlat_ii = newlat_i + sml_delta_y  
                    newlon_ii = newlon_i + sml_delta_x
                    new_elev_iii = new_elev_i + sml_delta_z 
                    accum = accum + chain
                    print `accum`+','+`newlon_ii`+','+`newlat_ii`+','+`int(new_elev_iii)`+','+`int(perct_gr)`+','+`alpha12`+','+`alpha21`+', 8'
                    value = (
'                    <name>one.kml</name>\n'+
'    <Style id="sn_shaded_dot">/n'+
'        <IconStyle>\n'+
'            <scale>0.3</scale>\n'+
'            <Icon>\n'+
'                <href>http://maps.google.com/mapfiles/kml/shapes/shaded_dot.png</href>\n'+
'            </Icon>\n'+
'        </IconStyle>\n'+
'        <ListStyle>\n'+
'        </ListStyle>\n'+
'    </Style>\n'+
'    <Placemark>\n'+
'        <name>'+`accum`+'</name>\n'+
'        <description>chainage: '+`accum`+'\n'+
'elevation: '+`int(new_elev_iii)`+'\n'+
'percent grade: '+`int(perct_gr)`+'\n'+
'forward azimuth : '+`alpha12`+'\n'+
'backward azimuth: '+`alpha21`+'</description>\n'+
'        <LookAt>\n'+
'            <longitude>'+`newlon_ii`+'</longitude>\n'+
'            <latitude>'+`newlat_ii`+'</latitude>\n'+
'            <altitude>0</altitude>\n'+
'            <heading>2.821165660590745</heading>\n'+
'            <tilt>0</tilt>\n'+
'            <range>275.175070801221</range>\n'+
'            <altitudeMode>relativeToGround</altitudeMode>\n'+
'            <gx:altitudeMode>relativeToSeaFloor</gx:altitudeMode>\n'+
'        </LookAt>\n'+
'        <styleUrl>#sn_shaded_dot</styleUrl>\n'+
'        <Point>\n'+
'            <coordinates>'+`newlon_ii`+','+`newlat_ii`+',0</coordinates>\n'+
'        </Point>\n'+
'    </Placemark>\n')
                    s = str(value)
                    f=open('chainmaker_output.kml','a')
                    f.write(s)
                    f.close()
                    count = count + chain
                    newlat_i = newlat_ii
                    newlon_i = newlon_ii
                    y1 = newlat_i
                    x1 = newlon_i
                    z1 = new_elev_iii
            log.pop(0)
    else:
        log.pop(1)
counter = counter +1
value = ('</Document>\n'+
         '</kml>\n')
s = str(value)
f=open('chainmaker_output.kml','a')
f.write(s)
f.close()        
total_dist=accum+excess
print `total_dist`
```

---

### Post by KB8NO on 2011-09-13
I'm flipping back a bit to discussing how to get a USB dongle working with gpsd.  I use Ubuntu 11.04 and wanted to finally figure out how to use my DeLorme Earthmate GPS LT-20 USB GPS dongle I bought some time ago mainly because it was inexpensive and bundled with obsolete Windows mapping software.  I installed gpsd (Linux GPS daemon), gpsd-clients (axillary tools and clients for gpsd), and foxtroggps (a GPS mapping client that uses gpsd) using Synaptic.  
 

 I plugged in the USB GPS device after rebooting.  I used the terminal and I entered “dmesg | tail” which told me that the USB dongle I just plugged in was a serial device called /dev/ttyUSB0 and was recognized by Linux.  (Please note that ttyUSB0 is case sensitive.)  I then used the gspd-clients tool by typing "gpsmon /dev/ttyUSB0" in the terminal.  This talks directly to the GPS device without gpsd and it returned GPS data telling me that my connected dongle is reading GPS data, speaks “generic NMEA”, and talks at 115200 Baud.  
 

 I then used the Linux “process status” command in the terminal "ps -C gpsd -fww" which returned data and told me that gpsd daemon was working.  I then used the gspd-clients GPS program or client called xgps in the terminal by typing xgps.  This is a useful test client that uses the gpsd server and which returns a map of satellites, coordinates, and information about the GPS fix.    This program needs the gpsd server to talk to the GPS unit but no data came up to display.  Therefore, both the gpsd daemon and USB dongle were working but programs weren't talking through gpsd to USB dongle.
 

 Lots of Googling and reading led me to find that the gpsd server daemon only needed to be configured.  However, I would have figured it out easier if I had read the comments at the top of the gpsd configuration file /etc/default/gpsd.  I used "sudo dpkg-reconfigure gpsd" to reconfigure gpsd which modifies the configuration file.   It took a lot of time to find this simple trick and even the syntax wasn't easy to get right.   
 

 The “dpkg-reconfigure gpsd” is a terminal configuration tool program that walks you through configuring gpsd.  It listens for your GPS and identifies the port of the GPS unit as /dev/ttyUSB0.  It asks you if you want to accept this port and you say “YES”.  Also say YES to both start gpsd automatically (start gpsd at boot) and handle attached USB GPS receivers automatically (autostart “DEVICES”).  Leave the other options or arguments blank as they are not needed.  You need unplug the GPS dongle and reboot.

After rebooting, plug in the GPS dongle and it will autostart.  Bingo, it works.  I brought up xgps tool client again and it returned gps data from the GPS dongle unit meaning that gpsd was now talking to the GPS dongle.  I then brought up the FoxtrotGPS client and it worked also.   My GPS dongle needs to have a fix before the maping clients show a GPS connect so don't get spooked and think it is not working.  Watch what is happening with the gpsd tool xgps and be sure you have a fix.  The GPS can get a fix in seconds but it can also take many minutes and you need a good view of the sky.
 

 If you plug the GPS dongle in after it has rebooted it autostarts.  If you unplug the GPS dongle there is an obligatory 15 minute time out for security reasons before it will re-start.  My GPS dongle also starts with it plugged in at boot if you use the -N argument but this defeats some security precautions so I did not ultimately use it.
 

 I studied the functionality of my DeLorme GPS unit by trial and error.  My unit has an LED which can be red, yellow, or green.  As it is turning on it is briefly red continuously.   Then it starts to flash a short red every 2 seconds as it initializes.  When it changes to flashing a long red every second it is ready for a GPS client to attempt to connect through gpsd.  When it flashes a long flash yellow every second it means that it has a 2 D fix and a long flash of green every second it means it has 3 D fix.  Other GPS units will have a variation on this theme.  
 

 Then I started figuring out how to use the new world of Linux mapping software and maps at my fingertips.  Hope this is helpful.

---

### Post by Herman on 2011-09-13
:) Hello there KB8NO, it's nice to have some company at last! :)

---

### Post by gosling1 on 2011-09-26
Ok guys-

I've used a program called OpenCPN for navigation on my boat. Previous to installing Ubuntu, I used SeaClear on Windows.

I use a GT3731 gps puck which worked perfectly in the windows environment but I can't find a way to get ubuntu to recognize and pass the gps data along to OpenCPN.

Please understand that while I have a lot of computer experience, I'm pretty new to ubuntu so will need some very specific, clear suggestions written especially for a newbie.

I'll be very grateful if someone can point me in the right direction so that I can get gps position into the navigation program.

With my thanks,

Mike Robinson

---

### Post by Herman on 2011-10-20
You probably need to find Ubuntu Software Center somewhere in the Ubuntu you're using. In the newest version of Ubuntu, (at this time 11.10 Oneric Ocelot), the  Ubuntu Software Center icon can be found about half way up the  side-bar. If they are not already installed, make sure you install gpsd, (the linux gps daemon), and gpsd-clients, like KB8NO just mentioned in post#9.

Then go outside somewhere where you have a good view of the sky and with your GPS plugged in, try to test if you can receive any GPS signals by opening up a terminal in Ubuntu and typing the letters 'xgps' into your terminal and press 'enter'. A new window should open showing you a view of the sky and after a few minutes you might see some dots on it representing satellites.
When you can see a graphical representation of where some satellites are located in the sky you should also be able to see your position and other data in the fields below.
If not then just wait a few minutes longer, it could take some time to get satellite lock.

When you are able to receive satellite data in xgps then you know your computer is able to read your GPS and that's a good first step, after that your programs should be able to read your GPS too, if not you probably only need to adjust a few settings in the programs themselves.

I was lucky and managed to purchase a USB GSP which is designed to be compatible and easily readable by most gps software, so mine is just plug and play. A web page I googled about your GT3731 says it is only able to be used with the supplied software on the CD that comes with it (only for Windows I presume). However, that doesn't mean you cannot use it in Linux, you just might need to do a little more manual configuring. KB8NO has already explained how to do that. If you have waited more than say fifteen or twenty minutes and still  didn't get any satellite lock, it could be time to start reading from the  second paragraph of KB8NO's excellent post.
Although I didn't need to go through any of those steps with the USB GPS I have, I can understand the basics of what KB8NO is telling us. If you need more help I can try to explain it more in layman's terms for you need me to. Just tell me what parts you're having trouble with and I'll try to help where necessary rather than re-writing a more verbose interpretation of the entire post.

Has this been helpful so far?

---

### Post by newuser10 on 2011-12-29
Hi, I want to use the FoxtrotGPS for plotting "friends locations" as well. The "friends" on my case are 3 points in my vicinity. I tried using the "friends" option in foxtrot but it asks me to Register and then gives an error when I try to do so. Kindly help me in this regard. How can I plot 3 other locations' on my map (along with my own) and send my location to those three nodes as well so that they may plot my location on their maps in a similar manner. Any sort of help is acknowledged.

*I have attached a screenshot of the error it's giving me*

---

### Post by Herman on 2012-01-01
Hello newuser10,
The friend finder service in Foxtrot GPS doesn't work for me either, I think it's something that Foxtrot GPS developers are working on. 
It's in the list called 'RoadMap', here, [http://www.foxtrotgps.org/roadmap.html](http://www.foxtrotgps.org/roadmap.html)
Maybe some day after an update it will start working, but for the time being all we can do is wish and wait, unless we know how to write our own code.

---

