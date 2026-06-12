---
title: "No weather data in conkyforecast help plz"
date: 2010-05-20
forum: General Help
---

### Post by HiryuPD on 2010-05-20
Hi all, I am not much of a scripter, but I have been toying with conky and been happy with my results so far, except forecast! I cannot seem to get data to show up in the forecast window. I have my city ID and I also went to weather.com and signed up and got my 2 keys and put them in conkyforecast.config.  So here is what I have (the template is someone else s mind you but I have my city data enetered. I'm sure I am overlooking something but what I don't know :p

conkyforecast:
> 
alignment bottom_left
background yes
border_width 0
cpu_avg_samples 2
default_color white
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
double_buffer yes
use_xft yes
xftfont Arial:size=10
gap_x 10
gap_y 220
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type normal
own_window_transparent yes
own_window_argb_visual 
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale yes
show_graph_range yes


TEXT
${font Sans:bold:size=10}${color2}${color blue}WEATHER
${color1}${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=30}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WF}
${voffset -52}${font Weather:size=40}y ${offset -15}${font Sans:size=20}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –imperial}
${font}${alignr}${offset 0}${voffset -15}${execpi 1800 conkyForecast –location=USWI0411 –datatype=CT}
Temperature:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –imperial} (Feels Like ${execpi 1800 conkyForecast –location=USWI0411 –datatype=LT –imperial})
Humidity:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HM}
Dew Point:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=DP –imperial}
Visibility:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=VI –imperial}
Wind:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WD –imperial} (${execpi 1800 conkyForecast –location=USWI0411 –datatype=WS –imperial})
UV-Index:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=UI} (${execpi 1800 conkyForecast –location=USWI0411 –datatype=UT})
Barometer:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=BR –imperial} (${execpi 1800 conkyForecast –location=USWI0411 –datatype=BD})
Daylight:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=SR}-${execpi 1800 conkyForecast –location=USWI0411 –datatype=SS}
Moon Phase:${alignr}${execpi 1800 conkyForecast –location=USWI0411 –datatype=MP}
${font Sans:bold:size=10}${color2}EXTENDED FORECAST${hr 2}${font}
${color1}${voffset 0}${execpi 1800 conkyForecast –location=USWI0411 –datatype=DW –startday=1 –shortweekday}${goto 70}${execpi 1800 conkyForecast –location=USWI0411 –datatype=DW –startday=2 –shortweekday}${goto 140}${execpi 1800 conkyForecast –location=USWI0411 –datatype=DW –startday=3 –shortweekday}${goto 210}${execpi 1800 conkyForecast –location=USWI0411 –datatype=DW –startday=4 –shortweekday}
${voffset 0}${font ConkyWeather:size=20}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WF –startday=1}${goto 70}${font ConkyWeather:size=20}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WF –startday=2}${goto 140}${font ConkyWeather:size=20}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WF –startday=1}${goto 210}${font ConkyWeather:size=20}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WF –startday=4}${font}
${voffset 0}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –startday=1 –imperial –hideunits}/${execpi 1800 conkyForecast –location=USWI0411 –datatype=LT –startday=1 –imperial –hideunits}${goto 70}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –startday=2 –imperial –hideunits}/${execpi 1800 conkyForecast –location=USWI0411 –datatype=LT –startday=2 –imperial –hideunits}${goto 140}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –startday=3 –imperial –hideunits}/${execpi 1800 conkyForecast –location=USWI0411 –datatype=LT –startday=3 –imperial –hideunits}${goto 210}${execpi 1800 conkyForecast –location=USWI0411 –datatype=HT –startday=4 –imperial –hideunits}/${execpi 1800 conkyForecast –location=USWI0411 –datatype=LT –startday=4 –imperial –hideunits}
${voffset 0}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WD –startday=1 –imperial}${goto 70}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WD –startday=2 –imperial}${goto 140}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WD –startday=3 –imperial}${goto 210}${execpi 1800 conkyForecast –location=USWI0411 –datatype=WD –startday=4 –imperial}


---

### Post by bra|10n on 2010-05-20
Delete everything after TEXT and copy / paste the following...
Edit accordingly

${execpi 1800 conkyForecast --location=[COLOR=Red]UKXX0103[/COLOR]  --template=/usr/share/conkyforecast/example/conkyForecast.template} - [COLOR=Red]edit to your location[/COLOR]

---

### Post by HiryuPD on 2010-05-20
> **bra|10n said:**
> Delete everything after TEXT and copy / paste the following...
Edit accordingly

${execpi 1800 conkyForecast --location=[COLOR=Red]UKXX0103[/COLOR]  --template=/usr/share/conkyforecast/example/conkyForecast.template} - [COLOR=Red]edit to your location[/COLOR]


Here is what I got after doing this, which is actually more than I had before...in a way lol

---

### Post by HiryuPD on 2010-05-20
I'm still not sure whats going on, I didn't change any of the general settings for x or y positioning, I have all my data entered.. still looks like the above screenshot. :(

---

### Post by bra|10n on 2010-05-20
Ok its a start.
You have  installed conkyForecast from the PPA and followed Kaivalagi's instructions on setting up?
Have you inserted your ID and location into the conkyForecast.config script?
You need to copy/paste conkyForecast.config into /home dir.

Is that screenshot only coming from the line I gave you earlier?

Post back here and I can help you further. 
Directions for setup though are on the first page of the thread also
cheers

---

### Post by HiryuPD on 2010-05-21
> **bra|10n said:**
> Ok its a start.
You have  installed conkyForecast from the PPA and followed Kaivalagi's instructions on setting up?
Have you inserted your ID and location into the conkyForecast.config script?
You need to copy/paste conkyForecast.config into /home dir.

Is that screenshot only coming from the line I gave you earlier?

Post back here and I can help you further. 
Directions for setup though are on the first page of the thread also
cheers

I went and re typed and reconfigured conkyforecast.config, it is in my /home dir and I copied and pasted the template from the usr/share/conkyforecast/examples  folder into my .conkyrc for weather and entered my location there. Does it have to do with the fact that its the 4th conky I have running? I wouldn't think so... I am also running a multiple_conky.sh at startup. Still looks like the above screencap too.

---

### Post by bra|10n on 2010-05-21
Check .xsession-errors in your home dir and see if that tells you anything

---

### Post by bra|10n on 2010-05-21
Lets start from the beginning ;)
Go to usr/share/conkyforecast.
Open[COLOR=Blue] conkyForecast.config[/COLOR] and ensure that you have entered your [COLOR=Red]Locale=[/COLOR], [COLOR=Red]XOAP_PARTNER_ID =[/COLOR], and [COLOR=Red]XOAP_LICENCE_KEY =[/COLOR]
Close the file and copy/paste [COLOR=Blue]conkyForecast.config[/COLOR] to ~/

Now, delete everything after TEXT in your conkyrc and copy / paste the following...
${execpi 1800 conkyForecast --location=USWI0411   --template=/usr/share/conkyforecast/example/conkyForecast.template}
This should be all that's in your conkyrc after TEXT now :)

One last thing. ..
If you have edited the [COLOR=Purple]conkyForecast.[/COLOR][COLOR=Purple]template[/COLOR] file during these attempts at getting this to work then you will need to restore it to its original version. (Note that I have not asked you to edit the template file in these instructions)

Let me know if it works!
cheers

---

### Post by HiryuPD on 2010-05-21
It appears I dont have that folder? of course hidden files are enabled visible :) hmmm

---

### Post by bra|10n on 2010-05-21
> **bra|10n said:**
> Ok its a start.
[SIZE=4][COLOR=Red]You have  installed conkyForecast from the PPA and followed Kaivalagi's instructions on setting up?[/COLOR][/SIZE]
Have you inserted your ID and location into the conkyForecast.config script?
You need to copy/paste conkyForecast.config into /home dir.

Is that screenshot only coming from the line I gave you earlier?

Post back here and I can help you further. 
Directions for setup though are on the first page of the thread also
cheers

... lol
If you indeed haven't, delete all you have (or move or rename it at least) and 
install the software ;)

---

### Post by bra|10n on 2010-05-21
Yeah I know,
it's here [http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyforecast](http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyforecast)

---

### Post by HiryuPD on 2010-05-21
Ok reinstalled and did everything again. Now I have this! lol

---

### Post by bra|10n on 2010-05-21
Congratulations! Sorry about the rain though ...
Change the size in conkyrc to something bigger, 
# Minimum size of text area
minimum_size 400 0
maximum_width 400

If you don't have this just copy and paste it in

---

### Post by HiryuPD on 2010-05-21
Well thanks again, I guess the tweaking can begin :P Sorry for being such a noob about this.

---

### Post by bra|10n on 2010-05-21
# alignment can be tl, tm, tr, bl, bm, br, ml, mr,
alignment tl           
background yes
border_width 0
cpu_avg_samples 1
default_color white
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
double_buffer yes
use_xft yes
xftfont Arial:size=10
# adjust gap_x for distance from edge of screen
gap_x 10
# adjust gap_y for distance from top or bottom of screen
gap_y 220
minimum_size 350
maximum_width 350 
net_avg_samples 1
no_buffers yes
out_to_console no
own_window yes
own_window_type override
own_window_transparent yes
own_window_argb_visual 
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no


TEXT


Above is your conkyrc updated a little.
Change yours to match.
To lose the shadow go to compiz / Windows Decorations and exclude conky,
something like type=!&conky

---

### Post by bra|10n on 2010-05-21
> **HiryuPD said:**
> Well thanks again, I guess the tweaking can begin :P Sorry for being such a noob about this.

You are very welcome!
We all start from somewhere, who knows you might be helping me before you know it!

Pls post a screenshot of the "whole" weather conky after you've resized your conkyrc

And pls mark your thread as Solved
Cheers HiryuPD

---

### Post by HiryuPD on 2010-05-21
I don't get what is going on here If I run the template file, it looks grand! But my own conkyrc for weather still is messed up. I'm sure missing something.. I reread the install guide AGAIN, and the readme... lol

---

### Post by bra|10n on 2010-05-21
I think I know what's going on here. 2 posts up I gave your conkyrc file updated but I think it is missing some key variables. Just go to the conkyrc in example folder and copy everything down to and including TEXT. Then replace everything in your conkyrc with that, keeping just what's below TEXT.
Let me know how it goes.

---

### Post by HiryuPD on 2010-05-21
That did the trick! All I need to know now is where do I change variable for Celsius to Fahrenheit. :)

---

### Post by bra|10n on 2010-05-21
Well the script should be showing Fahrenheit by default as the script's author is based in the UK.
Double check though... in the template file you should see --imperial in the lines relating to WS, CT, etc
I'm wondering now if your using the right 'template' file for your weather. Anyway you seem to have got the hang of it now...
I suggest you just delete all of those earlier copy/paste files you started with just to be sure...
The app is A1, works flawlessly and is well written

Enjoy!

---

