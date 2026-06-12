---
title: "Trying to get weather working..conky"
date: 2010-06-20
forum: General Help
---

### Post by localguy on 2010-06-20
Hello.

i'm having a problem trying to get weather installed/working for conky..

in my .conkyrc file i have this code of line
```
 ${color white}${execi 1800 /home/rjr/weather/weather.sh 92392}
```i have the 2 files weather.sh and weather.xslt in its own folder named weather

and in weather.sh file i have this line of code..
```
 # where this script and the XSLT lives
RUNDIR=/home/rjr/weather/ 
```i gave permission to weather.sh file, on my desktop running conky in the weather section it says **Invalid Partner Code.** 

I tried even putting USCA1197 in the .conkyrc file instead of my zip code and still same problem.

Do i have to give **weather** folder permission as well? Thanks hope someone can give a hand?


Just not my day had to make a new conky ](*,)

---

### Post by mobilediesel on 2010-06-21
> **localguy said:**
> Hello.

i'm having a problem trying to get weather installed/working for conky..

in my .conkyrc file i have this code of line
```
 ${color white}${execi 1800 /home/rjr/weather/weather.sh 92392}
```i have the 2 files weather.sh and weather.xslt in its own folder named weather

and in weather.sh file i have this line of code..
```
 # where this script and the XSLT lives
RUNDIR=/home/rjr/weather/ 
```i gave permission to weather.sh file, on my desktop running conky in the weather section it says **Invalid Partner Code.** 

I tried even putting USCA1197 in the .conkyrc file instead of my zip code and still same problem.

Do i have to give **weather** folder permission as well? Thanks hope someone can give a hand?


Just not my day had to make a new conky ](*,)

If your script is using weather.com you have to go to [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)
to get a partner code to use their api.

You can also use [conkyforecast]("http://ubuntuforums.org/showthread.php?t=869328") which also requires signing up for the partner code.

---

### Post by localguy on 2010-06-21
> **mobilediesel said:**
> If your script is using weather.com you have to go to [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)
to get a partner code to use their api.

You can also use [conkyforecast]("http://ubuntuforums.org/showthread.php?t=869328") which also requires signing up for the partner code.
  yes i did signup got the lic# key and partner ID added in terminal what do i do now?

---

### Post by mobilediesel on 2010-06-21
> **localguy said:**
> yes i did signup got the lic# key and partner ID added in terminal what do i do now?

Post the script you're using and I'll see where to put the license key and partner id.

---

### Post by localguy on 2010-06-21
> **mobilediesel said:**
> Post the script you're using and I'll see where to put the license key and partner id.


thie one from terminal or the weather.sh script or theweather.xslt? cause in teminal i have this

ofcouse with my ID and key already inserted 
i have this in .conkyrc at bottom
```
${color white}${execi 1800 /home/rjr/weather/weather.sh 92392}

``````
 # config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID =MY PARTNER ID IS IN
XOAP_LICENCE_KEY = MY LICENCE KEY IS IN
MAXIMUM_DAYS_FORECAST = 4
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&li$
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&l$








^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

---

### Post by mobilediesel on 2010-06-22
> **localguy said:**
> thie one from terminal or the weather.sh script or theweather.xslt? cause in teminal i have this

ofcouse with my ID and key already inserted 
i have this in .conkyrc at bottom
```
${color white}${execi 1800 /home/rjr/weather/weather.sh 92392}

``````
 # config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID =MY PARTNER ID IS IN
XOAP_LICENCE_KEY = MY LICENCE KEY IS IN
MAXIMUM_DAYS_FORECAST = 4
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&li$
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&l$








^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

Let's see the weather.sh and see what it's doing.

---

### Post by localguy on 2010-06-22
> **mobilediesel said:**
> Let's see the weather.sh and see what it's doing.


```
 #!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=92392

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=/home/rjr/weather/ 

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS&dayf=2"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt 

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"
```i still didnt kniw what to do after i added my ID and KEY CODE in here? so i just closed the terminal

```
 # config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID =MY PARTNER ID IS IN
XOAP_LICENCE_KEY = MY LICENCE KEY IS IN
MAXIMUM_DAYS_FORECAST = 4
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&li$
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&l$








^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
```

---

