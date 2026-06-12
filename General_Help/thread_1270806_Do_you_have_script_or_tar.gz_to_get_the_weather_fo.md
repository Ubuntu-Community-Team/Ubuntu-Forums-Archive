---
title: "Do you have script or tar.gz to get the weather for the console (no X)?"
date: 2009-09-20
forum: General Help
---

### Post by frenchn00b on 2009-09-20
Wanna send the temperature to my console 
 
Greetigns

---

### Post by infurnus on 2009-09-20
#$apt-get install weather-util
#$weather -id=KICT

find your ID here [http://weather.noaa.gov/](http://weather.noaa.gov/)

---

### Post by kevdog on 2009-09-20
I didn't optimize the script but something like this:

$ curl -s "http://weather.chicagotribune.com/US/IL/Chicago/KORD.html?main=1" | grep Midway -A4 | tail -1 | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed 's/^[ \t]*//;s/[ \t]*$//' | cut -c 1-2

I guess the secret is finding a website or some website source which you can then basically do a filter on to extract the temperature.

The output of the script is the following:

$ curl -s "http://weather.chicagotribune.com/US/IL/Chicago/KORD.html?main=1" | grep Midway -A4 | tail -1 | sed -e :a -e 's/<[^>]*//g;/</N;//ba' | sed 's/^[ \t]*//;s/[ \t]*$//' | cut -c 1-2
60

---

