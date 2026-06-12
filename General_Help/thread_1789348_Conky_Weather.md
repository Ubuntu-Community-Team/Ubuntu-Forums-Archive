---
title: "Conky Weather?"
date: 2011-06-23
forum: General Help
---

### Post by faint545 on 2011-06-23
This isn't a question of how do you get weather updates posted to your desktop using Conky but rather, why is it that everywhere I search, people seem to use the external program conkyForecast to get weather updates? I'm new to Conky and I've looked through the table of variables allowed ([http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)) and in it there is a variable for weather and weather forecast (${weather} and ${weather_forecast}). 

Now I haven't been able to figure out how to use it but why don't I see people using these variables instead?

---

### Post by dragonfriend0013 on 2011-12-21
I am also wondering the same thing.  If conky was changed to include this infomation, why can't i find any examples of anyone using them?  I am going to try tonight to get it working.

---

### Post by Sector11 on 2012-01-21
> **faint545 said:**
> This isn't a question of how do you get weather updates posted to your desktop using Conky but rather, why is it that everywhere I search, people seem to use the external program conkyForecast to get weather updates? I'm new to Conky and I've looked through the table of variables allowed ([http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)) and in it there is a variable for weather and weather forecast (${weather} and ${weather_forecast}). 

Now I haven't been able to figure out how to use it but why don't I see people using these variables instead?

${weather_forecast} is DEAD - they want US $20 a month now ... NOAA only gives todays info so it's a very minimum weather output:

Here's what works for Buenos Aires all other formatting codes removed for simplicity:
```
Buenos Aires
     Temp: ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE temperature}°
Barometer: ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE pressure}
 Humidity: ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE humidity} %
     Wind: ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE wind_dir_DEG} °
           ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE wind_dir}
         @ ${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ SABE wind_speed} k/h

```

You need to find the airport code near you, best place I've found is here: [Airport Code Database Search]("http://www.airlinecodes.co.uk/aptcodesearch.asp")

And as an historical fack: conkyForecast is now dead as well, it used weather·com ($20 now) but there is a ConkyForecastWU (WeatherUnderground) packaged with it for the moment - in alpha.  ConkyForecast was created "long before" the ${weather} and ${weather_forecast} became a variable in conky.

Check Teo's scripts in my sig as well.

---

