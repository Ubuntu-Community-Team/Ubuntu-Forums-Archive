---
title: "Want to add a new location to the Gnome Weather Applet"
date: 2010-07-11
forum: General Help
---

### Post by randlieb on 2010-07-11
I have found a post ([http://ubuntuforums.org/showthread.php?t=1331653](http://ubuntuforums.org/showthread.php?t=1331653)) that tells me how to add a location to the Locations.xml file for the Gnome Weather Applet (NOT THE CLOCK/WEATHER APPLET). However when I try to open the file (the file is 916 kb) in bluefish it just hangs and never opens. I have tried doing something with both vim and nano but my expertise in using either of those is non-existent. If someone can help me understand how to open a file in vim or nano so I can edit this file (or ANY way to edit this file) I would be SOOOOO appreciative!!! THANKS!!

Am running Lucid.

---

### Post by gmargo on 2010-07-12
I figured out how to edit the Locations.xml file and to add an entry.  Just for you I added a Cottonwood, AZ entry.  Instead of cutting/pasting a lengthy procedure, I've attached a text file describing the methods I used.  See if it works for you.

So not everyone has to open the file, here is the key bit.  With the following sed command you can transform Locations.xml into a compatible but easily-edited format:
```

sed 's/\(<[a-z]\)/\n\1/g' < Locations.xml > Loc1.xml

```

---

### Post by randlieb on 2010-07-12
HOLY CRAP!!!!!!! THAT DID IT!!!!!! THANKS!!!

This should be a HOW TO somewhere here in the forums. I have seen a number of questions for this particular problem.

Thanks again!!!=D>

---

### Post by majoda on 2011-01-29
Hi,
Have done first step, made a copy of file in user/share....

following second step did not work making a file to work on in HOME.

My abilities are about copy and past! [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
what is correct code for second step, even if just put file to desktop.
found info for Biloela here
[http://www.bom.gov.au/products/IDQ60801/IDQ60801.94376.shtml](http://www.bom.gov.au/products/IDQ60801/IDQ60801.94376.shtml)
help appreciated
thanks

---

### Post by gmargo on 2011-01-30
Regarding gweather supporting Biloela and the nearby Thangool Airport (YTNG), it seems there is no METAR weather report for Thangool or any nearby airport.

This is the web interface for METAR reports: [http://weather.noaa.gov/weather/metar.shtml](http://weather.noaa.gov/weather/metar.shtml) so you can look up your nearby airport codes.

---

### Post by gmargo on 2011-01-30
> **majoda said:**
> 
following second step did not work making a file to work on in HOME.


Based on your email, I think you might have typed the directory name incorrectly.  Try using the  $HOME/Documents/ directory (note the capital-D).

Here's another quick tip.  Instead of the 'sed' command in those instructions, use the **xmllint(1)** command, which produces nicely indented XML.
```

$ xmllint --format Locations.xml > Loc1.xml

```

---

### Post by majoda on 2011-02-05
As can be seen by site I attached, weather reports e=are done every 30 minutes, not posted onto the internation web site that gmargo attached.
Must be some thing in programme to get from this site.
Ross

---

### Post by majoda on 2011-02-05
p { margin-bottom: 0.21cm; }  whether (weather/wether) I remove the <code>YTNG</code> and leave the line <zone>@ID039089</zone> which is the link to weather readings.
radar is the site of nearest at Gladstone.




 <city>
 <name>Biloela</name>
 <coordinates>-24.401000 150.511000</coordinates>
 &#8722;
 <location>
 <name>Thangool Airport</name>
 <code>YTNG</code>
 <zone>@ID039089</zone>
 <coordinates>-24.491535 150.573539</coordinates>
 <radar>@IDR232</radar>
 <coordinates>-23.869322 151.219876</coordinates>
 </location>
 </city>

---

