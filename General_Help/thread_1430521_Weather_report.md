---
title: "Weather report"
date: 2010-03-15
forum: General Help
---

### Post by Neosano on 2010-03-15
I need a command-line weather report tool.
Can't find any suitable.
There's one called "weather" but it's only for US, unfair!
KDE widgets work fine, but I need a command-line one.

---

### Post by sTpny on 2010-04-16
I'll second that! I want a command line tool for generating a spoken weather report to play after my morning alarm. I'm going to have to go look at source-forge. Maybe they'll have something more useful.

---

### Post by gmargo on 2010-04-16
Who said the **weather(1)** command (from the **weather-util** package) was US only?

Worldwide list of [METAR]("http://en.wikipedia.org/wiki/METAR") stations: [http://www.rap.ucar.edu/weather/surface/stations.txt](http://www.rap.ucar.edu/weather/surface/stations.txt)

Here are the current conditions in Iceland (no mention of volcanos though):
```

$ weather -i BIRK
Current conditions at Iceland (BIRK) 64-08N 021-54W 61M (BIRK)
Last updated Apr 16, 2010 - 09:00 PM EDT / 2010.04.17 0100 UTC
   Wind: from the NNE (020 degrees) at 25 MPH (22 KT)
   Sky conditions: mostly clear
   Temperature: 28 F (-2 C)
   Relative Humidity: 63%

```

---

### Post by solovievnn on 2012-12-21
> **gmargo said:**
> Who said the **weather(1)** command (from the **weather-util** package) was US only?


Wow. Thanks a lot! I was looking for weather-util alternative covering my home city when found your answer.

---

### Post by howefield on 2012-12-21
Old thread closed.

---

