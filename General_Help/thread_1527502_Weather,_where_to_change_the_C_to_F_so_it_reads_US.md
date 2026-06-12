---
title: "Weather, where to change the C to F so it reads USA temp,"
date: 2010-07-09
forum: General Help
---

### Post by localguy on 2010-07-09
Hello All,

I'm having little problem trying to change weather to USA it reads C  instead of F on conky forecast here is screenshot

Thanks for reading and the help

---

### Post by birkopf on 2010-07-09
> **localguy said:**
> Hello All,

I'm having little problem trying to change weather to USA it reads C  instead of F on conky forecast here is screenshot

Thanks for reading and the help


In you home folder you should have file called .conkyrc
(You need to press Ctrl + H to see all files)

You can change it there. If you will have a problem - send here content of this file.

---

### Post by localguy on 2010-07-09
> **birkopf said:**
> In you home folder you should have file called .conkyrc
(You need to press Ctrl + H to see all files)

You can change it there. If you will have a problem - send here content of this file.
here is the weather part in my .conkyrc

```
 ${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USCA1197 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USCA1197 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USCA1197 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USCA1197 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USCA1197 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USCA1197 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USCA1197 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USCA1197 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USCA1197 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USCA1197 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USCA1197 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USCA1197 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}
```

---

### Post by birkopf on 2010-07-09
> **localguy said:**
> here is the weather part in my .conkyrc
[...]


That file is massive! From what I see - you have repeated few times same code with different network interfaces (wlan0, eth0, eth1....)

You will be modifying one set that is assigned to your interface. Right click on Network icon in right top corner and select connection information. You will have in Interface - which one you use. 


Try to modify datatype=LT or datatype=HT or datatype=WF
I don't know what to as I didn't wrote this script. Search for configuration in place where you got it from. 
you have also there --hideunits option. Maybe this is hiding temperature ?

---

### Post by localguy on 2010-07-09
> **birkopf said:**
> That file is massive! From what I see - you have repeated few times same code with different network interfaces (wlan0, eth0, eth1....)

You will be modifying one set that is assigned to your interface. Right click on Network icon in right top corner and select connection information. You will have in Interface - which one you use. 


Try to modify datatype=LT or datatype=HT or datatype=WF
I don't know what to as I didn't wrote this script. Search for configuration in place where you got it from. 
you have also there --hideunits option. Maybe this is hiding temperature ?

im not sure trying couple other things, i didnt notice the connections i'll check em now

---

### Post by localguy on 2010-07-09
> **localguy said:**
> im not sure trying couple other things, i didnt notice the connections i'll check em now
ok fixed it finally lol just had to add ```
 --imperial} 
``` before datetype=HT now just need to do it all to my laptop lol

---

### Post by squidpotion on 2010-07-09
Out of curiosity, does the weather temp ever go above 99? Lately around here it's been 100+ and I haven't seen it go above 99. Is there any way to change it if it does?

---

### Post by localguy on 2010-07-10
> **squidpotion said:**
> Out of curiosity, does the weather temp ever go above 99? Lately around here it's been 100+ and I haven't seen it go above 99. Is there any way to change it if it does?
  i'll find out this weekend suppose to be 113 this weekend and 111 rest of the week YUCK lol

---

