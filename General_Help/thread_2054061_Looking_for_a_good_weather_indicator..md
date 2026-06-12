---
title: "Looking for a good weather indicator."
date: 2012-09-06
forum: General Help
---

### Post by Erik1984 on 2012-09-06
Ubuntu has no weather indicator by default since the switch to Unity. The only indicator I found in the repos is "indicator-weather".  This one only half works. Sometimes the temperature next to the icon is gone (maybe the Google Weather API is to blame for this as I had the same trouble with a KDE weather indicator) and not all weather situations have a monochrome icon. Are there any alternatives I could try?

---

### Post by Erik1984 on 2012-09-08
*bump*

---

### Post by dcstar on 2012-09-08
> **Euroman said:**
> Ubuntu has no weather indicator by default since the switch to Unity. The only indicator I found in the repos is "indicator-weather".  This one only half works. Sometimes the temperature next to the icon is gone (maybe the Google Weather API is to blame for this as I had the same trouble with a KDE weather indicator) and not all weather situations have a monochrome icon. Are there any alternatives I could try?

If you use Gnome 3 you get a Weather Indicator. That is one of the reasons I don't use Unity.

---

### Post by claracc on 2012-09-08
You can install and try my-weather-indicator adding the corresponding ppa: [http://www.techlw.com/2012/08/install-my-weather-indicator-05-in.html](http://www.techlw.com/2012/08/install-my-weather-indicator-05-in.html)

---

### Post by newb85 on 2012-09-08
The version of indicator-weather in the repositories is 11.11.28.  By adding the developers' ppa, you can upgrade it to the latest, which is 12.07.30.

```
$ sudo add-apt-repository ppa:weather-indicator-team/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

Yes, the problem is with Google's weather API.  I've had better luck selecting Yahoo's weather data service.

---

### Post by Frogs Hair on 2012-09-08
I have been using the one at the link and Google should be avoided as stated above. [http://www.iloveubuntu.net/my-weather-indicator-adds-new-weather-source-world-weather-online](http://www.iloveubuntu.net/my-weather-indicator-adds-new-weather-source-world-weather-online)

---

### Post by wheeze on 2012-09-08
> **euroman said:**
> looking for a good weather indicator.

All the indicators I've used report both good and bad weather. :D

---

### Post by newb85 on 2012-09-08
> **wheeze said:**
> All the indicators I've used report both good and bad weather. :D

:razz:

---

### Post by Erik1984 on 2012-09-08
> **wheeze said:**
> All the indicators I've used report both good and bad weather. :D

LOL 

But seriously, My Weather seems like a nice suggestion so thanks! I'll try it with the Yahoo weather API first.

---

### Post by claracc on 2012-09-09
> All the indicators I've used report both good and bad weather:lol:

Euroman, if you got fixed your problem, please, mark the thread as solved with "thread tools" in the upper right part of the page.

---

### Post by Erik1984 on 2012-09-09
> **claracc said:**
> Euroman, if you got fixed your problem, please, mark the thread as solved with "thread tools" in the upper right part of the page.

Ok. I haven't tried any of the suggestions yet (so my 'problem' isn't really fixed) but I guess those suggestions are the answer to my original question so I'll mark it as solved.

---

