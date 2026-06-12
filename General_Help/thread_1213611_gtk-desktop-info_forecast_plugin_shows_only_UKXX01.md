---
title: "gtk-desktop-info forecast plugin shows only UKXX0103 weather"
date: 2009-07-15
forum: General Help
---

### Post by dumblebee100 on 2009-07-15
[SIZE="4"][B]This bug is solved in recent version of gtk-desktop-info v 0.24
just edit the settings from ~/.config/gtk-desktop-info 
and not from the default location /usr/share/gtk-desktop-info 
because user config over rides the default config[/B][/SIZE]

recently Im trying gtk-desktop-info ....I successfully managed to change all the xml and css to my criteria for deluge plugin .....
when I tried forecast plugin ..I get only UKXX0103 weather ..

I have changed to my location to INXX0057 in plugin_forecast.config file which is located in /usr/share/gtk-desktop-info/config/

my config file looks like this 
```
# config settings for forecast plugin

# Template file determining the format for the top of the info.
HEADERTEMPLATE = 

# The template file to generate output. A displayable item in the file is in the form [--datatype=HT --startday=1].
# The following are possible options within each item:
# --location=CODE : The location code for weather data.
# --datatype=TYPE : The data type options are: DW (Day of Week), WF (Weather Font output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), VI (Visibility), WD (Wind Direction), WA (Wind Angle - in degrees), WS (Wind Speed), WG (Wind Gusts), BF (Bearing Font), BS (Bearing font with Speed), CN (City Name), CO (Country), OB (Observatory), SR (SunRise), SS (SunSet), DL (DayLight), MP (Moon Phase), MF (Moon Font), BR (Barometer Reading), BD (Barometer Description), UI (UV Index), UT (UV Text), DP (Dew Point), LU (Last Update at weather.com), LF (Last Fetch from weather.com)
# --startday=NUMBER : Define the starting day number, if omitted current conditions are output
# --endday=NUMBER : Define the ending day number, if omitted only starting day data is output
# --night : switch output to night data, if omitted day output will be output
# --shortweekday : Shorten the day of week data type to 3 characters
# --imperial : request imperial units, if omitted output is in metric
# --beaufort : request beaufort scale for wind speeds, if omitted output is either metric/imperial
# --hideunits :  Hide units such as mph or C, degree symbols (°) are still shown
# --hidedegreesymbol : Hide the degree symbol used with temperature output, this is only valid if used in conjunction with --hideunits
# --spaces=NUMBER : Define the number of spaces between ranged output
# --minuteshide=NUMBER : Works only with LU and LF. If present, hides the date part of the LU or LF timestamp if the day of the timestamp is today. The time part is also hidden, if the timestamp is older than minutes specified in this argument. If set to 0, the time part is always shown. If set to -1, the value EXPIRY_MINUTES from the config file is used
TEMPLATE = 

# The location code for weather data.
# Use the following url to determine your location code by city name:
# http://xoap.weather.com/search/search?where=Norwich
LOCATION = INXX0057

# How long before the cache is deemed out-of-date, so next refresh it will be updated from the weather.com website
EXPIRY_MINUTES = 30

# The format of time output
TIMEFORMAT = %H:%M

# The format of date output
DATEFORMAT = %Y-%m-%d

# with no setting the default locale of the system is used, if supported.
# If no translation is available then the plugin defaults to english
LOCALE = 

# Your registered partner id
XOAP_PARTNER_ID =  hidden for the forum

# Your registered licence key
XOAP_LICENCE_KEY = hidden for the forum

# maximum days forecast range, only change this if you have an extended license
MAXIMUM_DAYS_FORECAST = 4

# If set to true new weather data will retrieved each time the plugin runs
REFETCH = false

# The folder where forecast data cache files are stored. Best to leave the default setting
CACHE_FOLDERPATH = /tmp/

# Define the number of seconds before a connection timeout can occur. 
# Not applicable at command line when using templates
CONNECTION_TIMEOUT = 10

```

well this config file is not working for me so I tried changing the file plugin_forecast.py located at /usr/share/gtk-desktop-info/plugin_forecast.py

```
class ForecastConfig:
    HEADERTEMPLATE = None
    TEMPLATE = None
    LOCATION = ""
    EXPIRY_MINUTES = 1
    TIMEFORMAT = "%H:%M"
    DATEFORMAT = "%Y-%m-%d"
    LOCALE = None # with no setting the default locale of the system is used
    XOAP_PARTNER_ID = "" # need config with correct partner id
    XOAP_LICENCE_KEY = "" # need config with correct licence key
    MAXIMUM_DAYS_FORECAST = 4 # only change if you are used an extended license
    IMAGESIZE = 48
    REFETCH = False
    CACHE_FOLDERPATH = "/tmp/"
    CONNECTION_TIMEOUT = 10

```

in that code I entered the values of my location code, partnerId and license key ....but still if I execute the plugin then I get only UKXX0103 location weather ....

well my command is like this  and I get output like this 
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=18 --width=286 --height=870 --x=683 --y=0 --plugin=forecast --template=/usr/share/gtk-desktop-info/templates/forecast.template 




url:http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=10&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b&unit=m




Window moved to 683,1

```

why it searches for UKXX0103 even if I mention my location code even in config and python script both ...can you please correct where Im wrong ..

I even deleted the content of gtk-desktop-info forecast in /tmp folder and tried many times but everytime it downloads only UKXX0103 cache file

I posted a screenshot which gives you some idea what problem Im facing ...
the conkyweather ( **bottom left** ) is correct to my location ....but the (**top middle**) is the gtk-desktop-info ones ..it shows only UK weather and not my location weather 
and another problem is ...in the URL in screenshot ...it appears to be not taking my partner ID and license key but instead its using UKXX0103 by default everytime ...even though I added all the details in files plugin_forecast.config and plugin_forecast.py

---

### Post by dumblebee100 on 2009-07-16
32 views but still no reply from anyone ...

should I think no one has problems like me or else they couldnt solve my problem ....

Im expecting a answer from the ubuntu community

---

