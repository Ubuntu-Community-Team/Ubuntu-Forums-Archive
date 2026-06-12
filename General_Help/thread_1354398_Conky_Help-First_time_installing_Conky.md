---
title: "Conky Help-First time installing Conky"
date: 2009-12-13
forum: General Help
---

### Post by Rifester on 2009-12-13
I found this Conky set up:

 [http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

I really like the way it looks and was able to iron out a few problems with it.  But I cannot figure out why it won't display the weather temperature.  I have a screen shot showing the weather file, and it shows the accurate weather info.   It also is not showing the HDD temperature.   Any ideas?    

Thanks for helping me learn!

---

### Post by Johnny B on 2009-12-13
first try running:
> sudo chmod u+s /usr/sbin/hddtemp
if that doesnt work, please post your conkyrc file

---

### Post by Rifester on 2009-12-13
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py username pasword 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

---

### Post by Johnny B on 2009-12-13
i read that tutorial and i think perhaps you need to setup hddtemp:
[http://ubuntuforums.org/showthread.php?t=282353](http://ubuntuforums.org/showthread.php?t=282353)

---

### Post by Rifester on 2009-12-13
Thanks for the info.   I followed the tutorial and it now shows the C for celsius by HDD and  temperature.    Any idea why the weather temperature and barometer are not showing up?   It is picking up that it is CLOUDY from the weather file and displaying it on the desktop but no temperature...

---

### Post by Johnny B on 2009-12-13
could you run:
> ~/scripts/pogodynka.sh
and tell me what it says?
it appears to download the weather, just not display it.
also im having a hard time reading it, my polish is a bit rusty

---

### Post by Rifester on 2009-12-13
F / Barometer: F

---

### Post by Johnny B on 2009-12-13
you need to edit that file and change/add these two things:

```

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/Desktop

# Kod miasta
kod=USID0025

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
	#echo "Serwis niedostêpny"
  #else
	# pobieranie informacji
 	w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' [COLOR="Red"]| sed '/^$/d'[/COLOR] > $plik

	# ustalenie warto¶ci zmiennych
	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $1}'`
	tempo=`head [COLOR="Red"]-n4[/COLOR] $plik | tail -n1`
	cisn=`head -n8 $plik | tail -n1`
	wiatr=`head -n16 $plik | tail -n1`
	wilg=`head -n10 $plik | tail -n1`
	wsch=`head -n18 $plik | tail -n1`
	zach=`head -n20 $plik | tail -n1`
	if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
	  then
		stanpl=$stan
	  else
		stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
	fi
	
```

---

### Post by Rifester on 2009-12-13
That fixed it!   Thank you so much!   I have been pulling my hair out.   I added CONKY to my startup menu but it won't boot at startup, I have to start it in terminal.   Is there anyway to make it run automatically?   

Thankful,
Mark

---

### Post by Johnny B on 2009-12-13
sure, you can't start conky directly from the startup menu, but you can add a script that will start conky.
not sure why, but you need to wait a few seconds after login before starting conky, thats what that sleep command is for: 

```
#!/bin/bash
sleep 6
conky -c ~/.conkyrc &
```

save this wherever and add it to the startup menu

---

