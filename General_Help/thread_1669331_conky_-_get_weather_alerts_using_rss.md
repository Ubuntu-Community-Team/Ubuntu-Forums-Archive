---
title: "conky - get weather alerts using rss?"
date: 2011-01-17
forum: General Help
---

### Post by beoram on 2011-01-17
Quick question about how to get weather alerts with conky.

I'm using the following bit of code:

${execpi 3600 ~/.conky/scripts/conky-rss.sh "http://www.weather.gov/alerts/wwarssget.php?zone=MDZ006"|sed '1,3d'|fold -sw 62}

This (correctly) display a message to the effect "There are no weather alerts for ...." when there are no weather alerts. However, when there is an alert, it simply displays a message like "Short-term forecast for ..." with no further information.

Any suggestions?

How are other people getting weather alert info in their conkys?

---

### Post by VastOne on 2011-01-17
> **beoram said:**
> Quick question about how to get weather alerts with conky.

I'm using the following bit of code:

${execpi 3600 ~/.conky/scripts/conky-rss.sh "http://www.weather.gov/alerts/wwarssget.php?zone=MDZ006"|sed '1,3d'|fold -sw 62}

This (correctly) display a message to the effect "There are no weather alerts for ...." when there are no weather alerts. However, when there is an alert, it simply displays a message like "Short-term forecast for ..." with no further information.

Any suggestions?

How are other people getting weather alert info in their conkys?

Is it possible that your fold statement is cutting off the full message?

Look for Conky Forecast here and K's scripts... In my sig line That is what most of use for forecasts in Conky

---

### Post by beoram on 2011-01-17
Thanks, VastOne.

I tried without the "fold", and it's no different.

I've looked round here (and elsewhere) at conky configs, but I haven't found anything for weather alerts specifically.

---

### Post by VastOne on 2011-01-17
> **beoram said:**
> Thanks, VastOne.

I tried without the "fold", and it's no different.

I've looked round here (and elsewhere) at conky configs, but I haven't found anything for weather alerts specifically.

The folks at Conky PitStop (also in my sig line) are gurus that can help you and they hang out a lot [_[COLOR="DarkRed"]at this mega thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865").  

I realize it is a mountain of messages but well worth checking there

Good Luck

---

### Post by VastOne on 2011-01-17
Found this by Mobilediesel, who is part of the Conky PitStop crew

[[COLOR="Blue"]_weather alerts by MobileDiesel_[/COLOR]]("http://sites.google.com/site/mobilediesel/Home/conky/modular/weather-alerts")

---

### Post by beoram on 2011-01-17
Many thanks, VastOne!

---

### Post by kmw288 on 2011-01-31
I wrote a small app to grab alert data from the RSS feed about a year back. I recently tried to use it again, and it seems to return "unknown location" no matter what I do. It looks like they may be working on a new beta version, and could be phasing the old system out at the moment? just a thought. (There are references to using "/alerts-beta/" in the link rather than "/alerts/".

---

### Post by NertSkull on 2011-07-18
So I'm now on the hunt to try and get this working.

That mobile diesel page is telling me its not there any more.

Does anyone else have weather alerts working for conky that could point me in the right direction?

---

### Post by Habitual on 2011-07-18
[http://ubuntuforums.org/showthread.php?t=1156383](http://ubuntuforums.org/showthread.php?t=1156383)

---

