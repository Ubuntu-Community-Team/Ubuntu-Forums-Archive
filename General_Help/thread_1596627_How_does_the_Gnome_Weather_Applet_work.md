---
title: "How does the Gnome Weather Applet work?"
date: 2010-10-14
forum: General Help
---

### Post by m4lte on 2010-10-14
Hi there,
I'm wondering where the Gnome Weather Applet gets its weather data from.

In particular I would like to add my location to the weather applet. I found a technical solution in this thread [http://ubuntuforums.org/showthread.php?t=1529032](http://ubuntuforums.org/showthread.php?t=1529032), but I don't understand where the weather data comes from. In the file Locations.xml coordinates (e.g. 34.739188 -112.009879), codes (e.g. KSEZ) and zones (e.g. AZZ038) are specified. What do the codes and zones mean? How can I locate a weather station near me and find out it's codes? Where does the applet get its data from?
For the weather report in the Clock Applet I just entered the coordinates of my location and now I'm getting some weather data. Does that mean that the program automatically takes data from the nearest location in its database?

I hope someone can shed some light on this ;)
Thanks!

btw. my location is Nijmegen in the Netherlands.

---

### Post by happyhamster on 2010-10-14
Synaptic has this little bit of info about the weather-applet (part of the gnome-applets package):
> 
Weather report: downloads weather information from the U.S National Weather Service (NWS) servers, including the Interactive Weather Information Network (IWIN).


---

