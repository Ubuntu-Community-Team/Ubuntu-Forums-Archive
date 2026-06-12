---
title: "Conky weather problem"
date: 2009-07-08
forum: General Help
---

### Post by Hangwire on 2009-07-08
Hello everyone! I've been using the following script to get my weather display in conky, and as of yesterday i didnt have any problems. Today though, it has stopped working. Where the weather should be it displays 

> Missing 'XOAP link in Request

The script is as follows: 

```
#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /home/johan/.weather.sh SWXX0006}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=$1

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=/home/nick/Scripts/weather

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
```

In conkyrc, I call it out with: 
```

${execi 1800 /home/nick/Scripts/weather/weather.sh BUXX0003}
```

Any suggestions? Google hasn't been very helpful. =/

---

### Post by Hangwire on 2009-07-11
Shameless bump.

---

### Post by Bruce M. on 2009-07-12
> **Hangwire said:**
> Hello everyone! I've been using the following script to get my weather display in conky, and as of yesterday i didnt have any problems. Today though, it has stopped working. Where the weather should be it displays 

Any suggestions? Google hasn't been very helpful. =/

> # The orignal script and xslt can be downloaded from [http://pondol.com/weather.tar.gz](http://pondol.com/weather.tar.gz)

I tried downloading it, got a 404 error.

I know they made some "internal" changes recently. Maybe that is causing problems with this script.

Why not try [ConkyForecast]("http://ubuntuforums.org/showthread.php?t=869328") where you posted for help with a link here?

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-07-12
> **Hangwire said:**
> Shameless dump.

Which means?

---

### Post by Hangwire on 2009-07-22
> **Bruce M. said:**
> Which means?

shameless bump... probably made a typo, excuse me :D

---

