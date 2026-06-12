---
title: "how to modify conkyrc script to connect via proxy server ?"
date: 2011-02-11
forum: General Help
---

### Post by rvchari on 2011-02-11
hi,
i tried to search for possible tweak in getting conkyForecast connect via proxy server. it connects and functions well when directly connected to internet (from home) but in office, i have to connect via proxy...
any idea how i go about tweaking the script to connect via proxy?

---

### Post by Habitual on 2011-02-11
It shouldn't matter to conky.
Everything at the office is using the proxy, yes?

---

### Post by rvchari on 2011-02-11
yes. office lan is thru dhcp. internet has to be connected via proxy server. office runs windows, i m running ubuntu !

b4 i connect to the internet in office, i change my direct connetion to proxy in network proxy, apply it systemwide.

synaptic needs to be configured by editing its preferences and ofcourse links2 (which i use rarely) browser and skype connects cool empathy connects yahoo id but not skype when on proxy server.

so i thought there must b something in conkyrc that i have to add ? i think i cant just add HOST, PROXY SERVER, USER, PASS ?

---

### Post by aeiah on 2011-02-11
its not conky, its conkyforcast . it seems odd that it doesnt listen to system-wide proxy settings. in the source code, namely conkyForcast.py theres:

```

class ForecastConfig:
    CACHE_FOLDERPATH = "/tmp/"
    CONNECTION_TIMEOUT = 5
    EXPIRY_MINUTES = 30
    TIME_FORMAT = "%H:%M"
    DATE_FORMAT = "%Y-%m-%d"
    LOCALE = "" # with no setting the default locale of the system is used
    XOAP_PARTNER_ID = "" # need config with correct partner id
    XOAP_LICENCE_KEY = "" # need config with correct licence key
    DEFAULT_LOCATION = "UKXX0103"
    MAXIMUM_DAYS_FORECAST = 4
    AUTO_NIGHT = False
    BASE_XOAP_URL = "http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m"
    PROXY_HOST = None
    PROXY_PORT = 8080
    PROXY_USERNAME = None
    PROXY_PASSWORD = None

```

you should be able to just fill things in there. remember to use quotes. the coder prefers double quotes but it shouldn't matter. so do:
```

    PROXY_HOST = "name.of.host"
    PROXY_PORT = 8080
    PROXY_USERNAME = "your_username"
    PROXY_PASSWORD = "your_password"

```

however this might not work. it doesnt seem like there's a place to specify the type of proxy within the framework the developer has used. perhaps its worth sending a message to the developer. he has a thread for conkyforcast [url=http://ubuntuforums.org/showthread.php?t=869328]here[/here]

---

### Post by rvchari on 2011-02-11
> **aeiah said:**
> its not conky, its conkyforcast . it seems odd that it doesnt listen to system-wide proxy settings. in the source code, namely conkyForcast.py theres:

```

class ForecastConfig:
    CACHE_FOLDERPATH = "/tmp/"
    CONNECTION_TIMEOUT = 5
    EXPIRY_MINUTES = 30
    TIME_FORMAT = "%H:%M"
    DATE_FORMAT = "%Y-%m-%d"
    LOCALE = "" # with no setting the default locale of the system is used
    XOAP_PARTNER_ID = "" # need config with correct partner id
    XOAP_LICENCE_KEY = "" # need config with correct licence key
    DEFAULT_LOCATION = "UKXX0103"
    MAXIMUM_DAYS_FORECAST = 4
    AUTO_NIGHT = False
    BASE_XOAP_URL = "http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m"
    PROXY_HOST = None
    PROXY_PORT = 8080
    PROXY_USERNAME = None
    PROXY_PASSWORD = None

```

you should be able to just fill things in there.** remember to use quotes. the coder prefers double quotes but it shouldn't matter. **so do:
```

    PROXY_HOST = "name.of.host"
    PROXY_PORT = 8080
    PROXY_USERNAME = "your_username"
    PROXY_PASSWORD = "your_password"

```

however this might not work. it doesnt seem like there's a place to specify the type of proxy within the framework the developer has used. perhaps its worth sending a message to the developer. he has a thread for conkyforcast [url=http://ubuntuforums.org/showthread.php?t=869328]here[/here]

i think you may be right, i had forgotten to give quotes when fiddling that file. i ll do it tomorrow when in office and check out !!!
small oversight !!! but then it happens.... hope i find the solution tomorrow !

---

### Post by rvchari on 2011-02-12
its not connecting !!! :confused:

---

