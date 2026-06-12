---
title: "Conky Miscellaneous Python Scripts"
date: 2010-12-16
forum: General Help
---

### Post by kaivalagi on 2010-12-16
[SIZE="1"][COLOR="Green"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*
```
Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

This is a collection is very simple scripts to do various conky orientated things.

The scripts present are:
[LIST]
[*]conkyText - provides formatted output from a delimited text file
[*]conkyLatLong - provides latitude/longtitude co-ordinates based on your IP address
[*]conkyDateDiff - provides a difference in time between now/a date to another date
[*]conkyDaysDiff - provides a difference in days between now/a date to another date
[*]conkySlideshow - provides a locally stored image on each call based on an input file of image URLs
[/LIST]

There is a README with the install, I suggest you give it atleast a quick once over! It can be found in the installation folder, normally following the path of /usr/share/conkymisc/

**_[SIZE=3][COLOR=Blue]Basic Install[/COLOR][/SIZE]_**

**[COLOR=Blue]Method 1: Using apt[/COLOR]**

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
[INDENT]* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site[/INDENT]

2) Now that is done simply run the following to update your repo cache and install the scripts: 

```
sudo apt-get update && sudo apt-get install conkymisc

```

**[COLOR=Blue]Method 2: Using deb file[/COLOR]**

Run the .deb file available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR=Blue]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the tar.gz file to an appropriate folder, and edit the various /usr/bin calling scripts (e.g. conkyText) to point to the correct location where th epython scripts have been placed (e.g conkyText.py). The tar.gz file is available at the Conky Companions PPA site here: [https://launchpad.net/~conky-companions/+archive/ppa/+packages](https://launchpad.net/~conky-companions/+archive/ppa/+packages)

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

For each command you can get the current help options at any time by running (change the command as necessary):
```

conkyText -h

```
or
```

conkyText --help

```

**[COLOR="Blue"]conkyText Help (conkyText --help)[/COLOR]**
```
Usage: conkyText [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output
  -f FILE, --textfile=FILE
                        location of the text file to output.
  -d FILE, --delimiter=FILE
                        default:[;]Specify the delimiter to use when splitting
                        out a line of text into formatted segments
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

**[COLOR="blue"]conkySlideshow Help (conkySlideshow --help)[/COLOR]**
```

Usage: conkySlideshow.py [options]

Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output, the placeholders are [imagename], [imageurl],
                        [imagepath], [imagewidth], [imageheight]
  -l FILE, --imagelist=FILE
                        location of the text file providing the image list
                        data, strict format required of NAME;URL on each line.
  -i FILE, --index=FILE
                        [default: /tmp/conkySlideshow.idx] Location of the
                        temp index file used to store the last image index
                        used
  -o FILE, --output=FILE
                        [default: /tmp/conkySlideshow.jpg] Location of the
                        file used for output
  -x NUMBER, --maxwidth=NUMBER
                        [default: 0] Output images maximum width, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set
  -y NUMBER, --maxheight=NUMBER
                        [default: 0] Output images maximum height, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set
  -r, --random          Request a random image from the list rather than the
                        next in the series
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10]
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

**[COLOR="blue"]conkyLatLong Help (conkyLatLong --help)[/COLOR]**
```
Usage: conkyLatLong [options]
Options:
  -h, --help            show this help message and exit
  -l, --longitudeonly   Force the script output Longitude only
  -L, --latitudeonly    Force the script output Latitude only
  -i, --imperial        Force the script to output in Degrees / Minutes and
                        Seconds. If not set the script outputs in the standard
                        metric decimal fashion
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10]
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

**[COLOR="blue"]conkyDateDiff Help (conkyDateDiff --help)[/COLOR]**
```
Usage: conkyDateDiff <startdate> [<enddate>]
  If no end date given it is assumed to be today.

  examples:

    $ conkyDateDiff 20080105 20091225
    1 year, 11 months, 20 days

```

**[COLOR="blue"]conkyDaysDiff Help (conkyDaysDiff --help)[/COLOR]**
```
Usage: conkyDaysDiff <startdate> [<enddate>]
  If no end date given it is assumed to be today.

  examples:

    $ conkyDaysDiff 20080105 20091225
    720

```


**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [URL="https://code.launchpad.net/%7Econky-companions/+junk/conkymisc"]https://code.launchpad.net/~conky-companions/+junk/conkymisc
[/URL] All packages available from me can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/%7Econky-companions/+archive/ppa")

---

### Post by Sector11 on 2011-02-09
Well I'll be a monkey's uncle - no, scratch that ...

Well I'll be.  I'll have to subscribe to this thread, I use all fours of them  :)

---

### Post by 42dorian on 2011-02-09
Hey kaivalagi!  Yet another bunch of great scripts for conky!

Question though.  Would it be possible to code switches to limit the data output?  Right now I'm using Grep/Awk to grab Latitude separate from Longitude.  Could another release of the conkyLatLong script include a switch to do that for me/the user?

And, also, a switch to go to a decimal format rather than minutes/seconds would be nice too.  I only ask because there's a place in my Conky for the data, but it's narrower than the space it takes for the way the script currently displays the output.  I used this to grab only one output at a time.

```

Lat: ${execi 30 conkyLatLong | grep 'N' | awk '{print $1}'}
Long:${execi 30 conkyLatLong | grep 'W' | awk '{print $3}'}

```

I was kinda hoping some future release might have this an alternative:

```

conkyLatLong -Lat
conkyLatLong -Long
conkyLatLong -u (For switching units.)

```

Just to simplify the code in the Conky.  Just an idea!

---

### Post by kaivalagi on 2011-02-09
I can't sleep so I'm taking a look now...I'm building in an options parser like used with the bigger scripts to give the abilities needed. It shouldn't take long as it's pretty much a cut and paste exercise from other scripts.

edit: Okay, find attached v1.01 of the Lat Long script, here are the options:

```

Usage: conkyLatLong [options]
Options:
  -h, --help            show this help message and exit
  -l, --longitudeonly   Force the script output Longitude only
  -L, --latitudeonly    Force the script output Latitude only
  -i, --imperial        Force the script to output in Degrees / Minutes and
                        Seconds. If not set the script outputs in the standard
                        metric decimal fashion
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10]
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

An example of commands and their output:
```

**]$** conkyLatLong
52.6280 / 1.3030
**]$** conkyLatLong -i   **[COLOR="Green"]<-- as before[/COLOR]**
52°37"40.8'N / 1°18"10.8'E
**]$** conkyLatLong -l
1.3030
**]$** conkyLatLong -L
52.6280
**]$** conkyLatLong -l -i
1°18"10.8'E
**]$** conkyLatLong -L -i
52°37"40.8'N

```

Get back to me once you've had a play with it to let me know iof all is well for a release or not

Cheers

---

### Post by 42dorian on 2011-02-09
I'm just going to shortcut it all... It works perfectly without a flaw I can find.  Do you need proof or is that good enough for you?

...And WOW that was fast!  Thank You!  My code thanks you too!

---

### Post by kaivalagi on 2011-02-10
It works for me too so it's going into a new conkyMisc package soon

---

### Post by kaivalagi on 2011-02-10
**[COLOR=Purple][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Updated conkyLatLong to have arguments for long only, lat only and imperial / metric output as well as the standard logging and verbose functions
[*]Amended usr/bin scripts to bring in line with other scripts
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.02_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.02_source.changes)

The apt packages should be available soon

---

### Post by GrouchyGaijin on 2011-02-17
I have the latitude and longitude script installed and it was working until this morning.  I noticed nothing was being displayed in my conky so I tried the command from the terminal and received this:

```
$ conkyLatLong
ERROR: writeOutput error:HTTP Error 500: Internal Server Error
```

Any ideas on what is going wrong or how to fix it?  I haven't changed anything.
I'm guessing that this is an error with the website used to fetch the coordinates.  I'm not sure though and the first thought my newbie mind had was that*** Internal*** Server Error meant something wrong on my end.

---

### Post by Sector11 on 2011-02-17
> **GrouchyGaijin said:**
> I have the latitude and longitude script installed and it was working until this morning.  I noticed nothing was being displayed in my conky so I tried the command from the terminal and received this:

```
$ conkyLatLong
ERROR: writeOutput error:HTTP Error 500: Internal Server Error
```

Any ideas on what is going wrong or how to fix it?  I haven't changed anything.
I'm guessing that this is an error with the website used to fetch the coordinates.  I'm not sure though and the first thought my newbie mind had was that*** Internal*** Server Error meant something wrong on my end.

Interesting, I have the same problem:

```
  08:34 ~
         $ conky -c ~/Conky/LatLong
Conky: forked to background, pid is 7796

  08:34 ~
         $ 
Conky: desktop window (1ad) is root window
Conky: window type - override
Conky: drawing to created window (0x2e00001)
Conky: drawing to double buffer
ERROR: writeOutput error:HTTP Error 500: Internal Server Error
conky -c ~/Conky/LatLong
Conky: forked to background, pid is 8117
```

So I reverted to my older version of conkyLatLong
```
conky -c ~/Conky/LatLong
Conky: forked to background, pid is 8117

  08:36 ~
         $ 
Conky: desktop window (1ad) is root window
Conky: window type - override
Conky: drawing to created window (0x3000001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/sector11/Conky/scripts/conkyLatLong.py", line 37, in <module>
    usock = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 397, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 435, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 518, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 500: Internal Server Error
         $
```

I installed a "localhost" yesterday I wonder if that could be the problem:

```
http://localhost/
```
> It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.

---

### Post by GrouchyGaijin on 2011-02-17
> **Sector11 said:**
> 
         $[/CODE]

I installed a "localhost" yesterday I wonder if that could be the problem:

```
http://localhost/
```

Do you mean that your conky latitude and longitude now works?
I really don't understand the last part of your reply.

When I type ```
http://localhost/
``` I also get

"It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet."

---

### Post by kaivalagi on 2011-02-17
Looks like the service used to get the co-ords based on IP is down, this is the URL used by the script:

```
http://gd.geobytes.com/gd?after=-1&variables=GeobytesLatitude,GeobytesLongitude
```

Cheers

---

### Post by Sector11 on 2011-02-17
> **GrouchyGaijin said:**
> Do you mean that your conky latitude and longitude now works?
I really don't understand the last part of your reply.

When I type ```
http://localhost/
``` I also get

"It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet."

No what I mean is that before I did this:

sudo apt-get install apache2 mysql-server php5 php5-mysql 

It worked!

I figured since I installed that and it stopped working the "localhost" is interfering, hence the:
> Internal Server Error

But I see K has the answer  :D
K stands for Kudos for kaivalagi

---

### Post by Sector11 on 2011-02-17
> **kaivalagi said:**
> Looks like the service used to get the co-ords based on IP is down, this is the URL used by the script:

```
http://gd.geobytes.com/gd?after=-1&variables=GeobytesLatitude,GeobytesLongitude
```

Cheers

It's even worse:

```
http://gd.geobytes.com/
```
has gone down!

> Server Application Error
The server has reached the maximum recovery limit for the application during the processing of your request. Please contact the server administrator for assistance.

And that message almost sounds like:
```
Keyboard Error!
Hit [F1] to continue.
```

What part of Keyboard Error doesn't that other OS understand?

Yes, I know - "someone" can phone or yell: "Hey Bob, we gotta a problem...."
:D

---

### Post by kaivalagi on 2011-02-17
Fingers crossed it's only a short term problem, if not we'll need to find an alternative service to provide location data...

---

### Post by Sector11 on 2011-02-17
> **kaivalagi said:**
> Fingers crossed it's only a short term problem, if not we'll need to find an alternative service to provide location data...

+1 on that!

EDIT:  But couldn't help it, I went looking!

[http://www.satsig.net/maps/lat-long-finder.htm](http://www.satsig.net/maps/lat-long-finder.htm)

Typed in my city - Buenos Aires, Argentina
Latitude = -34.6084, Longitude = -58.3732
Lat    = 34 degrees,   36.5 minutes   South
Long = 58 degrees,   22.4 minutes   West
{I'm outside that map area so don't think you found me}
But I could give you the exact co-ordinates of three other Linux users from here, one is a #!'er too.  :)

If you want to point a satellite TV dish at Satellite= 13 East orbit longitude
Beam elevation= 6.8, Azimuth= 85.8 (magnetic compass), Polarisation= 53.9

Zoomed in with the map until I got my street corner, zoomed in more, adjusting the point, then switched to satellite and put the point over my apartment.

It comes down to four decimal places: Latitude = -34.xxxx, Longitude = -58.xxxx with the pointer over my living room.  Calculating the minutes down to seconds:
```
Latitude = -34.xxxx = 34° xx' xx.6"
Longitude = -58.xxxx = 58° xx' xx.4"
```
That's pretty darn close!

---

### Post by kaivalagi on 2011-02-19
**[COLOR=Orange][SIZE=4]UPDATE[/SIZE][/COLOR]**

Looks like no fix was needed for the latlong stuff, the service is back up and working, find some new stuff to play with too :)

Updates as follows:
[LIST]
[*]Added conkySlideshow to the package
[/LIST]

Here's the help output for it:
```
Usage: conkySlideshow [options]
Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output, the placeholders are [imagename], [imageurl]
                        and [imagepath]
  -l FILE, --imagelist=FILE
                        location of the text file providing the image list
                        data, strict format required of NAME;URL on each line.
  -i FILE, --index=FILE
                        [default: /tmp/conkySlideshow.idx] Location of the
                        temp index file used to store the last image index
                        used
  -o FILE, --output=FILE
                        [default: /tmp/conkySlideshow.jpg] Location of the
                        file used for output
  -r, --random          Request a random image from the list rather than the
                        next in the series
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10]
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

I've added example files to the example folder which should get you started...look at the imagelist and template files, the two options for these are all that are needed to get working well.

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.03_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.03_source.changes)

The apt packages should be available soon

edit: small error on the file paths in the example conkyrc file for the conkySlideshow script...please make sure "SLideshow" is updated to be "Slideshow" before trying the example ;)

---

### Post by 42dorian on 2011-02-19
...I'm afraid to try it... I see this letting me be able to animate things in Conky... would that be too much for this script K?

This is not a feature request, this is me wondering if the script has limitations of this type.

---

### Post by kaivalagi on 2011-02-19
> **42dorian said:**
> ...I'm afraid to try it... I see this letting me be able to animate things in Conky... would that be too much for this script K?

This is not a feature request, this is me wondering if the script has limitations of this type.

Animations...No, I doubt it or conky is really up for the challenge :)

Wouldn't hurt to try it for a laugh though...reduce the update interval to 0.2 and get a massive 5 frames a second :D

---

### Post by 42dorian on 2011-02-19
Thank You, Good Sir.  You stopped me from trying to create any sort of animated Conky.  You're a Godsend.

I can see it used for other things, but, I'm glad it's not good for animations.  Cheers, K!

---

### Post by kaivalagi on 2011-02-20
I've added a maxwidth and maxheight option to the conkySlideshow script so that images are resized prior to being used if that is required. Here's the affected help entries:

```
  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output, the placeholders are [imagename], [imageurl],
                        [imagepath], [imagewidth], [imageheight]
...
  -x NUMBER, --maxwidth=NUMBER
                        [default: 0] Output images maximum width, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set
  -y NUMBER, --maxheight=NUMBER
                        [default: 0] Output images maximum height, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set

```

With this comes additional template placeholders for [imagewidth] and [imageheight] so the dimensions calculated for maintaining aspect can then be used in the $image variable

The example conkyrc when published will have this:
```
${execpi 10 conkySlideshow --imagelist=/usr/share/conkymisc/example/conkySlideshow.imagelist --template=/usr/share/conkymisc/example/conkySlideshow.template --maxwidth=300}
```

And the example template when published will have this:
```
${color1}${font Liberation Sans:size=11:style=Bold}[imagename]${color2}${font Liberation Sans:size=8}([imageurl])
${image [imagepath] -n -p 0,0 -s [COLOR="Red"][imagewidth[/COLOR]]x[COLOR="red"][imageheight][/COLOR]}
```

I'll not update the package yet as there will no doubt be some more features added soon enough too...but do find the modified conkySlideshow script attached

---

### Post by kaivalagi on 2011-02-25
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:
[LIST]
[*]Added maxwidth and maxheight to conkySlideshow, these force resizing of an image to fit the dimensions (width option overrides height). There are also [imagewidth] and [imageheight] placeholders available for the template too so resized dimensions can be used for output too.
[/LIST]

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.04_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.04_source.changes)

Here's the full help for conkySlideshow now it's changed (added/altered arguments in green):
```
Options:
  -h, --help            show this help message and exit
[COLOR="Green"][B]  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output, the placeholders are [imagename], [imageurl],
                        [imagepath], [imagewidth], [imageheight][/B][/COLOR]
  -l FILE, --imagelist=FILE
                        location of the text file providing the image list
                        data, strict format required of NAME;URL on each line.
  -i FILE, --index=FILE
                        [default: /tmp/conkySlideshow.idx] Location of the
                        temp index file used to store the last image index
                        used
  -o FILE, --output=FILE
                        [default: /tmp/conkySlideshow.jpg] Location of the
                        file used for output
[COLOR="Green"][B]  -x NUMBER, --maxwidth=NUMBER
                        [default: 0] Output images maximum width, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set
  -y NUMBER, --maxheight=NUMBER
                        [default: 0] Output images maximum height, if zero has
                        no effect, maxwidth overrides maxheight if both are
                        set
[/B][/COLOR]  -r, --random          Request a random image from the list rather than the
                        next in the series
  -c NUMBER, --connectiontimeout=NUMBER
                        [default: 10]
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

The apt packages should be available soon, waiting for the first build to start at time of posting

---

### Post by GrouchyGaijin on 2011-02-25
Hi Guys,

I'm using the latitude longitude script and get the output 59.3330 18.0500.

I checked to see where exactly that is and it looks like that puts me in Stockholm.  I'm actually a couple of hours north of Stockholm by express train.

I then typed my IP address (85.89.80.236) into Google's IP Geolocator and it came to with in a few blocks of my house.

Do you know why there is such a difference?

(This is **_not_** a complaint.  I could not write the code for this if my life depended on it.  I'm just curious.)

---

### Post by kaivalagi on 2011-02-25
Fair question, no idea why it's **_so_** off, my location is off by about a mile which isn't great but I can live with it

The site link used is here: [http://gd.geobytes.com/gd?after=-1&variables=GeobytesLatitude,GeobytesLongitude]("http://gd.geobytes.com/gd?after=-1&variables=GeobytesLatitude,GeobytesLongitude")

If you can provide another easy programmatic means of getting accurate oc-ords based on IP address do let me know...if it's more accurate I'll implement it

Cheers

edit: only good down to city level I think, just looking at geoip and here: [http://www.geobytes.com/IpLocator.htm]("http://www.geobytes.com/IpLocator.htm")

---

### Post by Sector11 on 2011-02-25
> **GrouchyGaijin said:**
> Hi Guys,

I'm using the latitude longitude script and get the output 59.3330 18.0500.

I checked to see where exactly that is and it looks like that puts me in Stockholm.  I'm actually a couple of hours north of Stockholm by express train.

I then typed my IP address (85.89.80.236) into Google's IP Geolocator and it came to with in a few blocks of my house.

Do you know why there is such a difference?

(This is **_not_** a complaint.  I could not write the code for this if my life depended on it.  I'm just curious.)

Hi Grouchy

I think it depends in where you go, mine in three sites show:

```
Lat            Long
-34.608418     -58.373161 
-34.6130       -58.4700
-34.5875       -58.6725
```

None of those are close to my house and they are different by quite a lot.  Now I'm sure my ISP isn't moving around.  :D

I use this to find my house:
[http://www.satsig.net/maps/lat-long-finder.htm](http://www.satsig.net/maps/lat-long-finder.htm)
I can zoom right onto my roof!

First use the map to zoom to the street corner - then switch to "satellite" view and keep that "little dot" where you want it.  :)

---

### Post by kaivalagi on 2011-02-25
> **Sector11 said:**
> I use this to find my house:
[http://www.satsig.net/maps/lat-long-finder.htm](http://www.satsig.net/maps/lat-long-finder.htm)
I can zoom right onto my roof!

You can use google maps too, just install the tools from the labs (see attached screeny)

---

### Post by GrouchyGaijin on 2011-02-25
When I hit that link I get
```
var sGeobytesLocationCode="SESTSTOC";var sGeobytesIsLocationMatch=false;var sGeobytesLatitude="59.3330";var sGeobytesLongitude="18.0500";
``` But my town is:

Falun, Sweden
Region: Dalarnas Lan
Country: Sweden
Latitude: 60.6
Longitude: 15.6333333

I see that Google's Geolocator uses maxmind.com which costs money :-(

---

### Post by Sector11 on 2011-02-25
> **kaivalagi said:**
> You can use google maps too, just install the tools from the labs (see attached screeny)

Hmmmmmmmmm ... google grrrrrr ... *install the tools from the labs*?

That lab?

---

### Post by kaivalagi on 2011-02-25
> **Sector11 said:**
> That lab?

The labs link is the little green test vial and red "New" at the top right of the maps page (just log in with your google account to retain the settings)

---

### Post by 42dorian on 2011-02-25
In all cases I'm finding that the only difference between the results I get from the script and therefore the site being used BY the script, and my actual map location is the number of decimals of latitude and longitude that the site is willing to go to for the location.

Literally, that's all I'm finding.  If latitude or longitude on the website were three or four more decimals more accurate, they'd get the same results that Google and satsig.net get for my location.  It appears the problem is that truncating the last few decimals is also rounding them up or down enough to throw the location off.

Or, that's what I'm seeing.

---

### Post by Sector11 on 2011-02-25
> **kaivalagi said:**
> The labs link is the little green test vial and red "New" at the top right of the maps page (just log in with your google account to retain the settings)

Google account?  Me?

Don't have one  :D

---

### Post by GrouchyGaijin on 2011-02-25
Thanks for the help guys.
Maybe its just so cold up here their website won't list this far north :D

---

### Post by Sector11 on 2011-02-27
> **GrouchyGaijin said:**
> Thanks for the help guys.
Maybe its just so cold up here their website won't list this far north :D

Oh I don't know, I have the info for a place where calling Santa is a local call: [Alert, Nunavut, Canada]("http://en.wikipedia.org/wiki/Alert,_Nunavut") this is [a good one too]("http://weather.gladstonefamily.net/site/CYLT") and it's further north than your are.  :D

Of wait, that's not using LatLong.py - bummer!

Oh well, good try. :popcorn:

---

### Post by GrouchyGaijin on 2011-02-27
LOL We here in Sweden pride ourselves on living at the edge of civilization.:)

---

### Post by Sector11 on 2011-02-27
> **GrouchyGaijin said:**
> LOL We here in Sweden pride ourselves on living at the edge of civilization.:)

And we Canuck's call ourselves "The Frozen Chosen" with good reason.

Although I must admit that others can make that claim as well, Greenland, Iceland, Norway, Sweden, Finland & Siberia for example.  We coined the phrase first.  It's ours!  :D

However as of today we will recognize our Swedish Cousins in Ice, hereby refered to as SCI, as "De Frysta Valda" (if my translation program is right).  :lol:

---

### Post by GrouchyGaijin on 2011-02-27
> **Sector11 said:**
> 
However as of today we will recognize our Swedish Cousins in Ice, hereby refered to as SCI, as "De Frysta Valda" (if my translation program is right).  :lol:

It works for me, but I'm not from here.  I'm an immigrant from the US.  We moved here when my wife was offered a good job at a university here.  We've been here about 18 months and I'm _*starting*_ to get a handle on the language.  It's been an adventure.

---

### Post by Sector11 on 2011-02-27
> **GrouchyGaijin said:**
> It works for me, but I'm not from here.  I'm an immigrant from the US.  We moved here when my wife was offered a good job at a university here.  We've been here about 18 months and I'm _*starting*_ to get a handle on the language.  It's been an adventure.

Ahhhhhhhh you tricked me!  When you said:
> **GrouchyGaijin said:**
> LOL We here in Sweden pride ourselves on living at the edge of civilization.:)

I though you were a Swede.  Now I suppose you'll tell me you come from the southern states where the only ice you see come in drinks. :mrgreen:

**NOTE:**  These "flashing" smilies are going to give me a seizure!

---

### Post by GrouchyGaijin on 2011-02-27
Naw Dude Chicago - I consider myself a Swede in spirit.  I've gone outside at -30. (I didn't want to, but I did)

---

### Post by Sector11 on 2011-02-27
> **GrouchyGaijin said:**
> Naw Dude Chicago - I consider myself a Swede in spirit.  I've gone outside at -30. (I didn't want to, but I did)

Chicago and still alive!  Now that's tough!
You qualify!  :D

---

### Post by kaivalagi on 2011-03-15
**[COLOR=Orange][SIZE=4]UPDATE[/SIZE][/COLOR]**

**New script added**

Updates as follows:
[LIST]
[*]Added conkyDatetimeDiff script to the package, it handles all previous conkyDaysDiff and conkyDateDiff operations as well as time based ones....It relies on standard date time formatting options ([http://docs.python.org/library/datetime.html#strftime-and-strptime-behavior]("http://docs.python.org/library/datetime.html#strftime-and-strptime-behavior")) rather than a strict format so should prove useful when comparing a range of inputs.
[/LIST]

Here's the help output for it:
```
Usage: conkyDatetimeDiff [options]
Options:
  -h, --help            show this help message and exit
  -s DATETIME, --startdatetime=DATETIME
                        [Mandatory] Start datetime to use for difference
                        output
  -e DATETIME, --enddatetime=DATETIME
                        End datetime to use for difference output, if omitted
                        then the current datetime is used.
  -i FORMAT, --inputformat=FORMAT
                        default:[%Y%m%d]Specify the format of the input date
                        time fields. See python docs for formatting options:
                        http://docs.python.org/library/datetime.html#strftime-
                        and-strptime-behavior
  -o OPTION, --outputformat=OPTION
                        default:[DIFF]Specify the format of the output date
                        time difference values, options are either DIFF,
                        YEARS, MONTHS, WEEKS, DAYS, HOURS, MINUTES, SECONDS
  -S, --shortoutput     Specify if short output is required resulting in ':'
                        separated string values where complex or a number
                        where not rather than plain english
  -n, --displaynegatives
                        Specify if a negative value should be output, normally
                        only the positive time difference is displayed
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

```

I've added example files to the example folder which should get you started...

Package changes can be seen here:  [https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.05_source.changes](https://launchpad.net/~conky-companions/+archive/ppa/+files/conkymisc_1.05_source.changes)

The apt packages should be available soon

**Example function calls**

Just a start datetime so defaults to DIFF and populates the end date from now (baby due date :)):
```
]$ conkyDatetimeDiff -s 20110324
8 days 23 hrs 59 mins 59 secs

```

Same as above but with --shortoutput option
```
]$ conkyDatetimeDiff -s 20110324 -S
00:00:08:23:59:59
```

days difference from new year of 2000 to now:
```
]$ conkyDatetimeDiff -s 20100101 -o DAYS
438 days
```

same but with end date and in seconds:
```
]$ conkyDatetimeDiff -s 20100101 -e 20110401 -o SECS
39312000 secs
```

How about a different datetime format giving date and time (spaces so quotes needed!):
```
]$ conkyDatetimeDiff -s "12/02/2009 18:25:12" -i "%d/%m/%Y %H:%M:%S"
2 yrs 1 mth  2 days 21 hrs 28 mins 32 secs
```

How about the short form of it:
```
]$ conkyDatetimeDiff -s "12/02/2009 18:25:12" -i "%d/%m/%Y %H:%M:%S" -S
02:01:02:21:30:47
```

Just a time, the date element is auto filled rather than left to the default of the start of time (1900 in this case), -n option gives the same:
```
]$ conkyDatetimeDiff -s 18:25:12 -i %H:%M:%S
2 hrs 38 mins 14 secs
```

and again with -n option (startdatetime ahead of now):
```
]$ conkyDatetimeDiff -s 18:25:12 -i %H:%M:%S -n
-2 hrs 38 mins 14 secs
```

and again but short output:
```
]$ conkyDatetimeDiff -s 18:25:12 -i %H:%M:%S -n -S
-00:00:00:02:38:14
```

and between two times (-n option output unchanged as starttime before endtime):
```
]$ conkyDatetimeDiff -s 18:25:12 -e 21:05:14 -i %H:%M:%S
2 hrs 40 mins 2 secs
```

Just for kicks added a month number on the front to show the diversity of input allowed:
```
]$ conkyDatetimeDiff -s 02-18:25:12 -i %m-%H:%M:%S
27 days 21 hrs 22 mins 43 sec
```

edit: missed the example file off the package, find it attached
edit2: fixed an issue running with python 2.6 so there's a newer version (1.06) of the package coming shortly too...it will have the example file included too

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by lofijerm on 2011-10-17
Quick question.

Can someone explain the second part of this operation in detail please? (Newb language.)

> Extract all the contents of the tar.gz file to an appropriate folder, and edit the various /usr/bin calling scripts (e.g. conkyText) to point to the correct location where th epython scripts have been placed (e.g conkyText.py). 
:confused:

---

### Post by Sector11 on 2011-10-17
> **lofijerm said:**
> Quick question.

Can someone explain the second part of this operation in detail please? (Newb language.)

> Extract all the contents of the tar.gz file to an appropriate folder, and edit the various /usr/bin calling scripts (e.g. conkyText) to point to the correct location where the python scripts have been placed (e.g conkyText.py).

:confused:

**[COLOR="DarkRed"]EDIT:[/COLOR]**: looks like you are using a non-Debian based OS.

Extract conkyMisc to /usr/share/conkymisc/ if your system has a /usr/share/ in your path and
test it with:
```
conky -c /usr/share/conkymisc/example/conkyText.conkyrc &
```
if you see this:
[[IMG]http://thumbnails47.imagebam.com/15443/6eaa49154429583.jpg[/IMG]](http://www.imagebam.com/image/6eaa49154429583)
... it is working and what follows should work as well.

```
/usr/share/conkymisc/conkyDateDiff.py
/usr/share/conkymisc/conkyDateDiff.pyc
/usr/share/conkymisc/conkyDatetimeDiff.py
/usr/share/conkymisc/conkyDatetimeDiff.pyc
/usr/share/conkymisc/conkyDaysDiff.py
/usr/share/conkymisc/conkyDaysDiff.pyc
/usr/share/conkymisc/conkyLatLong.py
/usr/share/conkymisc/conkyLatLong.pyc
/usr/share/conkymisc/conkySlideshow.py
/usr/share/conkymisc/conkySlideshow.pyc
/usr/share/conkymisc/conkyText.py
/usr/share/conkymisc/conkyText.pyc

/usr/share/conkymisc/example
/usr/share/conkymisc/example/conkyDatetimeDiff.conkyrc
/usr/share/conkymisc/example/conkySlideshow.conkyrc
/usr/share/conkymisc/example/conkySlideshow.imagelist
/usr/share/conkymisc/example/conkySlideshow.template
/usr/share/conkymisc/example/conkyText.conkyrc
/usr/share/conkymisc/example/conkyText.template
/usr/share/conkymisc/example/conkyText.txt
```

An example (conkyText) that uses 12 text files, for birthdays, anniversaries, etc., simply called jan.txt, feb.txt etc, etc.
```
${voffset 15}${if_match "${time %b}"=="Jan"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/jan.txt}${else}\
${if_match "${time %b}"=="Feb"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/feb.txt}${else}\
${if_match "${time %b}"=="Mar"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/mar.txt}${else}\
${if_match "${time %b}"=="Apr"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/apr.txt}${else}\
${if_match "${time %b}"=="May"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/may.txt}${else}\
${if_match "${time %b}"=="Jun"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/jun.txt}${else}\
${if_match "${time %b}"=="Jul"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/jul.txt}${else}\
${if_match "${time %b}"=="Aug"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/aug.txt}${else}\
${if_match "${time %b}"=="Sep"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/sep.txt}${else}\
${if_match "${time %b}"=="Oct"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/oct.txt}${else}\
${if_match "${time %b}"=="Nov"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/nov.txt}${else}\
${if_match "${time %b}"=="Dec"}${execp conkyText --template=/home/sector11/Conky/DAYS/appts.template --textfile=/home/sector11/Conky/DAYS/dec.txt}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}${endif}
```

**conkyText --help**
```
  09:39:37 ~
         $ conkyText --help
Usage: conkyText.py [options]

Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        location of the template file to define the layout of
                        output
  -f FILE, --textfile=FILE
                        location of the text file to output.
  -d FILE, --delimiter=FILE
                        default:[;]Specify the delimiter to use when splitting
                        out a line of text into formatted segments
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.

  09:39:47 ~
         $ 
```

Any problems just ask.

---

### Post by ohnonot on 2011-12-05
thanks to kaivalagi for sharing these scripts!

i have a question about slideshow - are there any examples/configs around that use it?
i have a bit of a problem setting it up: 
- making the template find the right place to put the slide: i have it above my conky and would like it to close the gaps if the pic is smaller.
-  making it respect a maxheight as well as maxwidth.

...but most of all i'd need a shell script to create a decent file list from the pics on my hd. maybe even self-updating once a week or so, that would be wicked!
:guitar:

---

