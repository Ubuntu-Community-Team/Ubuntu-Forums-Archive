---
title: "Conky Weather. Not showing humidity etc"
date: 2009-11-14
forum: General Help
---

### Post by tarchy on 2009-11-14
Okay well my weather script is showing the wind...humidity and everything as 22 degrees celsius lol. 


Weather script in .conkyrc 

```
    ${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=ASXX0230 –datatype=WF}
    ${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=ASXX0230 –datatype=HT}
    $font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=WS}
    ${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=HM}
    ${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=PC}

    ${color DimGray}Sunrise: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SR}${alignr}
    Sunset: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SS}$color
```



And my conkyForecast.config

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID = xxxxx (dont worry these are filled in)
XOAP_LICENCE_KEY = xxxxx
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/ASXX0230?cc=*&dayf=10&li$
BASE_XOAP_URL = http://xml.weather.com/weather/local/ASXX0230?cc=*&dayf=10&link$



```


What am I doing wrong :S?

---

### Post by tarchy on 2009-11-15
. > In professional wrestling, a bump occurs whenever a wrestler hits the mat or the arena floor after receiving a move from his/her opponent. It can also refer to hitting the floor as a result of a missed aerial move. ...

---

### Post by mobilediesel on 2009-11-15
> **tarchy said:**
> Okay well my weather script is showing the wind...humidity and everything as 22 degrees celsius lol. 


Weather script in .conkyrc 

```
    ${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=ASXX0230 –datatype=WF}
    ${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=ASXX0230 –datatype=HT}
    $font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=WS}
    ${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=HM}
    ${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast –location=ASXX0230 –datatype=PC}

    ${color DimGray}Sunrise: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SR}${alignr}
    Sunset: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SS}$color
```



And my conkyForecast.config

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID = xxxxx (dont worry these are filled in)
XOAP_LICENCE_KEY = xxxxx
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/ASXX0230?cc=*&dayf=10&li$
BASE_XOAP_URL = http://xml.weather.com/weather/local/ASXX0230?cc=*&dayf=10&link$



```


What am I doing wrong :S?

It's a problem with copying and pasting the code you're using. Some forum/blog software changes double minus signs to dashes.
```
–location=ASXX0230 –datatype=WF
–location=ASXX0230 –datatype=HT
–location=ASXX0230 –datatype=WS
–location=ASXX0230 –datatype=HM
–location=ASXX0230 –datatype=PC
–location=BEXX0008 –datatype=SR
–location=BEXX0008 –datatype=SS
```
should be
```
--location=ASXX0230 --datatype=WF
--location=ASXX0230 --datatype=HT
--location=ASXX0230 --datatype=WS
--location=ASXX0230 --datatype=HM
--location=ASXX0230 --datatype=PC
--location=BEXX0008 --datatype=SR
--location=BEXX0008 --datatype=SS
```
Note that those are two minus signs, not full dashes. Just replace all the dashes with double minus signs and it should be good to go!

---

### Post by tarchy on 2009-11-15
> **mobilediesel said:**
> It's a problem with copying and pasting the code you're using. Some forum/blog software changes double minus signs to dashes.
```
–location=ASXX0230 –datatype=WF
–location=ASXX0230 –datatype=HT
–location=ASXX0230 –datatype=WS
–location=ASXX0230 –datatype=HM
–location=ASXX0230 –datatype=PC
–location=BEXX0008 –datatype=SR
–location=BEXX0008 –datatype=SS
```
should be
```
--location=ASXX0230 --datatype=WF
--location=ASXX0230 --datatype=HT
--location=ASXX0230 --datatype=WS
--location=ASXX0230 --datatype=HM
--location=ASXX0230 --datatype=PC
--location=BEXX0008 --datatype=SR
--location=BEXX0008 --datatype=SS
```
Note that those are two minus signs, not full dashes. Just replace all the dashes with double minus signs and it should be good to go!

Thanks bro you're a bloody legend.

---

