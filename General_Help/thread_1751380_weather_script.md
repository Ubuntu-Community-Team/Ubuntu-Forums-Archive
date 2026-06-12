---
title: "weather script"
date: 2011-05-06
forum: General Help
---

### Post by rusty_jones on 2011-05-06
```
   WEATHER ${hr 2}
    
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USPA0311 --datatype=WF}${font}
${voffset -70}${font Weather:size=40}${font}  ${voffset -18}${font Arial Black:size=26}${execi 600 conkyForecast --location=USPA0311 --datatype=HT}${font}

${alignc 63}${execpi 600 conkyForecast --location=USPA0311 --datatype=DW --startday=1 --shortweekday} ${alignc 28}${execpi 600 conkyForecast --location=USPA0311 --datatype=DW --startday=2 --shortweekday} ${alignc -9}${execpi 600 conkyForecast --location=USPA0311 --datatype=DW --startday=3 --shortweekday} ${alignc -44}${execpi 600 conkyForecast --location=USPA0311 --datatype=DW --startday=4 --shortweekday}${alignc -94}${execpi 600 conkyForecast --location=USPA0311 --datatype=DW --startday=5 --shortweekday}
${alignc 95}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USPA0311 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${font DejaVu Sans:size=7}${alignc 38}${execpi 600 conkyForecast --location=USPA0311 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USPA0311 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc 12}${execpi 600 conkyForecast --location=USPA0311 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USPA0311 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -17}${execpi 600 conkyForecast --location=USPA0311 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USPA0311 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignc -46}${execpi 600 conkyForecast --location=USPA0311 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USPA0311 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 4}Location:${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=CN}
Last Updated: ${alignr} ${execi 600 conkyForecast --location=USPA0311 --hideunits --datatype=LU -m 0 }
Feels Like:${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=LT}
Dew Point: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=DP}
Current Condition:${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=CC}
Chance of Precip: ${alignr}${execi 600 conkyForecast  --location=USPA0311 --startday=0 --datatype=PC}
Humidity: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=HM}
Wind: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=WS --imperial} - ${execi 600 conkyForecast --location=USPA0311 --datatype=WD}
Pressure: ${alignr}${execi 600 conkyForecast --location=USPA0311 --hideunits --datatype=BR}
Visibility: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=VI --imperial}
Sunrise: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=SR}
Sunset: ${alignr}${execi 600 conkyForecast --location=USPA0311 --datatype=SS}
Moon Phase:${alignr 8}${execi 600 conkyForecast --location=USPA0311 --datatype=MP} ${font MoonPhases:size=8}${execi 600 conkyForecast --location=USPA0311 --datatype=MF}${font}
${hr 2}
```


How can I add a fifth day into this screen?

rusty

[ATTACH]191360[/ATTACH]

---

