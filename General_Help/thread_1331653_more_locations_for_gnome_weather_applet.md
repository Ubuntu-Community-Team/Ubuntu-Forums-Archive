---
title: "more locations for gnome weather applet?"
date: 2009-11-19
forum: General Help
---

### Post by katana1000 on 2009-11-19
The gnome weather applet has a small list and doesnt include my location. But its available on weather.com, and many other sources

how do I add my location to the list?

thanks

---

### Post by berman56 on 2009-11-19
That is a popular idea:

[http://brainstorm.ubuntu.com/idea/17670/](http://brainstorm.ubuntu.com/idea/17670/)

There are some solutions proposed in the discussion, check it out.

---

### Post by psychok7 on 2009-11-25
i still cant seem to get my city to work on the applet.. i enter the code like they suggest, but it doesn't change

---

### Post by psychok7 on 2009-11-25
found the solution: 

So this is how you can add your location/city to City list on Weather Report.

    * Get your desire location by using wikimapia.org
    * change the longitude and latitude by using GPS Converter or wikimapia can also convert your longitude and latitude just fine.
    * Open up terminal, and go to folder /usr/share/libgweather/
    * Edit the Location.xml with your Favourite text editor. Please be aware that gedit might not be suitable due to encoding problem. Some editor might hung or crash. My suggestion is to use VIM or nano.
    * Go to nearest location by using the 'find' option.
    * Then add new city by using this template:

    <city><name>Your City</name><coordinates>27.990000 101.890989</coordinates></city>

    * Please change the template with your city name and your city coordinates that you got from previous steps.

After finish editing the Location.xml, please select your city listed on Weather Report Preferences by right-clicking the applet icon on your tray. If no data shown on update, just play around with the coordinates. 

more details here: 
[http://blog.gunbladeiv.com/2009/06/add-new-city-to-weather-report-applet.html](http://blog.gunbladeiv.com/2009/06/add-new-city-to-weather-report-applet.html)

---

