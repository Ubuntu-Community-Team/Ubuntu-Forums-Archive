---
title: "Can't get conky to start"
date: 2012-05-29
forum: General Help
---

### Post by sky5564 on 2012-05-29
so i have installed conky and the first time i ran it it worked fine but after i rebooted my pc it no longer works, When i run conky from terminal i get this - 

```
skilo@laptop1:~$ conky
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-BtwHED/pkcs11: No such file or directory
Conky: /home/skilo/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer
/home/skilo/scripts/pogodynka.sh: 50: /home/skilo/scripts/pogodynka.sh: w3m: not found
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Traceback (most recent call last):
  File "/home/skilo/scripts/gmail_parser.py", line 15, in <module>
    import feedparser         # For parsing the feed
ImportError: No module named feedparser
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

```

It says it cant find something in pogodynka.sh?

pogodynka.sh

```
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Pogodynka 0.2.2.1													#
#															#
# azhag (azhag@bsd.miki.eu.org)												#
#															# 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i	#
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message.					#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Wymagane aplikacje:													#
# w3m - tekstowa przegl±darka www											#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															# 
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod".							#
#															#
# Aby ustaliæ kod swojego miasta wejd¿ na stronê http://weather.yahoo.com/ i wyszukaj tam swoje miasto. Kodem jest 	#
# koñcówka linka z pogod± naszego miasta.										#	
#															#
# Przyk³adowe kody:													#
# Warszawa - PLXX0028													#
# Kraków - PLXX0012													#
# Gdañsk - PLXX0005													#
# Szczecin - PLXX0025													#
#															#
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji		#
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych.			#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/scripts

# Kod miasta
#kod=url

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
	#echo "Serwis niedostêpny"
  #else
	# pobieranie informacji
 	w3m -dump "$kod" | grep -A26 "Current" | sed 's/DEG/°/g' > $plik

	# ustalenie warto¶ci zmiennych
	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $2}'`
	#tempo=`head -n6 $plik | tail -n1`
	tempo=`tail -n1 $plik | awk '{print $4}'`
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
	
	# formatowanie informacji wyj¶ciowej
	# dostêpne zmienne:
	# $stan		opis stanu po angielsku
	# $stanpl	opis stanu po polsku
	# $temp		temperatura powietrza
	# $tempo	temperatura odczuwalna
	# $cisn		ci¶nienie atmosferyczne
	# $wiatr	kierunek, si³a wiatru
	# $wilg		wilgotno¶æ powietrza
	# $wsch		godzina wschodu s³oñca
	# $zach		godzina zachodu s³oñca
	
	#echo $stan
	#echo $stanpl
	echo $temp F  /  $tempo F
	#echo Cisnienie $cisn hPa
	#echo $wiatr
	#echo Wilgotno¶æ: $wilg
	#echo Wschód S³oñca: $wsch
	#echo Zachód S³oñca: $zach
	#echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# Šnieg
# Snow / Wind
# Šnieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# Šnieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# Šnieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# Šnieg z deszczem/Wiatr
# Rain / Snow / Wind
# Šnieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
# 
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
# 
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
# 
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
# 
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
# 
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d


```

And finally my conky file

```
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
color1 4D6844



TEXT
 ${color D3DADF}${font OpenLogos:size=45} u t
${font weather:size=82}${color C9CFD4}${execi 600 ~/scripts/conditions.sh}${color 265276}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${color 4EA9F3}${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${color}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color 014A7F}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py yourgmailusername yourgmailpassword 3}

   ${color 014A7F}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${color 014A7F}${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}


```

Can anyone help?

---

### Post by ajgreeny on 2012-05-29
In your conky config file replace the path of the script shown ```
${execi 1200 ~/scripts/pogodynka.sh}
``` with the full path ```
/home/*user*/scripts/pogodynka.sh
``` or even ```
$USER/scripts/pogpdynka.sh
```
Perhaps conky does not understand the ~ shortcut for home.

---

### Post by sky5564 on 2012-05-29
> **ajgreeny said:**
> In your conky config file replace the path of the script shown ```
${execi 1200 ~/scripts/pogodynka.sh}
``` with the full path ```
/home/*user*/scripts/pogodynka.sh
``` or even ```
$USER/scripts/pogpdynka.sh
```
Perhaps conky does not understand the ~ shortcut for home.

No luck, I still get the same error

```
skilo@laptop1:~$ conky
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-4RTZvl/pkcs11: No such file or directory
Conky: /home/skilo/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (140012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Traceback (most recent call last):
  File "/home/skilo/scripts/gmail_parser.py", line 15, in <module>
    import feedparser         # For parsing the feed
ImportError: No module named feedparser
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

```

---

### Post by sky5564 on 2012-05-29
I tried another conky configuration from here - [http://www.techdrivein.com/2011/02/6-awesome-conky-configs-that-just-works.html]("http://www.techdrivein.com/2011/02/6-awesome-conky-configs-that-just-works.html")

I didnt get as many errors with it but conky still failed to start.

```
skilo@laptop1:~$ conky -c ~/.conky/conkyrc_grey
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-4RTZvl/pkcs11: No such file or directory
Conky: forked to background, pid is 2750
skilo@laptop1:~$ 
Conky: desktop window (140012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2a00001)
Conky: drawing to double buffer

```

---

### Post by ajgreeny on 2012-05-29
What do you get if you run conky with no configuration file specified?

---

### Post by sky5564 on 2012-05-29
> **ajgreeny said:**
> What do you get if you run conky with no configuration file specified?

This.

```
skilo@laptop1:~$ conky
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-nwmrKh/pkcs11: No such file or directory
Conky: /home/skilo/.conkyrc: 14: no such configuration: 'border_margin'
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Segmentation fault (core dumped)

```

---

### Post by ajgreeny on 2012-05-29
Sorry but this is all beyond me now.  I don't think I've ever seen conky not start if it has no configuration file.

PS:  I assume you do not have a **/home/user/.conkyrc** file that you are overlooking, and which is the configuration that conky is still using.

---

### Post by sky5564 on 2012-05-29
> **ajgreeny said:**
> Sorry but this is all beyond me now.  I don't think I've ever seen conky not start if it has no configuration file.

PS:  I assume you do not have a **/home/user/.conkyrc** file that you are overlooking, and which is the configuration that conky is still using.

I moved the .conkyrc file to another folder then tried it again and now it works, Only it is not using my theme i want, I just get the standard black theme.

What am i doing wrong?

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> No luck, I still get the same error

```
...
Traceback (most recent call last):
  File "/home/skilo/scripts/gmail_parser.py", line 15, in <module>
    import feedparser         # For parsing the feed
ImportError: No module named feedparser
...

```
This is because you don't have the feedparser python module installed or it is installed for the wrong version of python.

try running conky with
```

conky -DD -c path/to/.conkyrc

```It may give more detailed error messages that indicate which conky variables are causing the other errors.

Try commenting out the line
   ```
${color 014A7F}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}
```it looks like it might be causing these error messages.
```

Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

```[Also try asking in the big conky thread]("http://ubuntuforums.org/showthread.php?t=281865&page=1993") there are a lot of people there who will help you.

---

### Post by sky5564 on 2012-05-29
> **arclance said:**
> This is because you don't have the feedparser python module installed or it is installed for the wrong version of python.

try running conky with
```

conky -DD -c path/to/.conkyrc

```It may give more detailed error messages that indicate which conky variables are causing the other errors.

Try commenting out the line
   ```
${color 014A7F}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}
```it looks like it might be causing these error messages.
```

Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

```[Also try asking in the big conky thread]("http://ubuntuforums.org/showthread.php?t=281865&page=1993") there are a lot of people there who will help you.

I installed the pythonfeed parser module and ran the command with -DD

Now i get this

```
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${updates}' to '11'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${time %H}' to '18'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${time %M}' to '38'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${time %S}' to '56'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/core.c:354]: Adding $cpu for CPU 0
DEBUG(1) [../../src/conky.c:2416]: evaluated '${cpu cpu0}' to '24'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/core.c:354]: Adding $cpu for CPU 1
DEBUG(1) [../../src/conky.c:2416]: evaluated '${cpu cpu1}' to '26'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${memperc }' to '15'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
DEBUG(1) [../../src/conky.c:2416]: evaluated '${fs_used_perc /}' to '4'
DEBUG(1) [../../src/core.c:1218]: no templates to replace
```

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> I installed the pythonfeed parser module and ran the command with -DD

Now i get this

I don't see anything wrong with that.
I looks like you might not have posted all the terminal output though.
Did you post everything?
If you wait longer are there new (no repeating) lines in the terminal or do the lines repeat?

Try running it again without the -DD to see if there are still any error messages.

It looks like the errors related to reading battery data are gone.
Did you comment out the battery line?

---

### Post by sky5564 on 2012-05-29
> **arclance said:**
> I don't see anything wrong with that.
I looks like you might not have posted all the terminal output though.
Did you post everything?
If you wait longer are there new (no repeating) lines in the terminal or do the lines repeat?

Try running it again without the -DD to see if there are still any error messages.

It looks like the errors related to reading battery data are gone.
Did you comment out the battery line?

It never ends man, The command output just never stops it keeps going and going and i cant even do a ctrl+c to stop it, I have to open the task manager and kill it from there.

It says basically the same stuff but never starts

Here it is being run without -DD

```
skilo@laptop1:~$ conky -c /home/skilo/.conky/conkyrc_grey
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-foobKz/pkcs11: No such file or directory
Conky: forked to background, pid is 2658
skilo@laptop1:~$ 
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
```

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> It never ends man, The command output just never stops it keeps going and going and i cant even do a ctrl+c to stop it, I have to open the task manager and kill it from there.

It says basically the same stuff but never starts

Here it is being run without -DD

```
skilo@laptop1:~$ conky -c /home/skilo/.conky/conkyrc_grey
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-foobKz/pkcs11: No such file or directory
Conky: forked to background, pid is 2658
skilo@laptop1:~$ 
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
```
Yes -DD is endless because the debug output is printed for every update, you might have to press ctrl+c a few times to stop conky when using -DD.
After seeing your output without -DD I don't think anything important was missing before.

conky is producing normal terminal messages at startup now (ignore the gnome-keyring line I haven't heard of it causing anyone problems before).

Does you conky display correctly now without the battery line?
If not what window manager are you using (openbox, compiz, ect.)?

---

### Post by sky5564 on 2012-05-29
Never mind this post look below. |
                                 |
                                 |
                                 |
                                 |
                                 |
                                 |
                                 |
                                 V

---

### Post by sky5564 on 2012-05-29
Ok to make this less confusing, I'm starting over from scratch and going the the instructions on this page - [http://www.unixmen.com/configure-conky-lua-in-ubuntu-11-10-12-04-fedora-debian-and-linuxmint-howto-conky/]("http://www.unixmen.com/configure-conky-lua-in-ubuntu-11-10-12-04-fedora-debian-and-linuxmint-howto-conky/")

My NEW .conkyrc file looks like this now - 

```
# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.conky/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ LQBK temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed eth0}
${color FFFFFF}${goto 125}${upspeed eth0}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

```

After i have followed all the instruction from that page i run the command as follows and i get this - 

```
skilo@laptop1:~$ conky -c /home/skilo/.conkyrc
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-foobKz/pkcs11: No such file or directory
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
^CConky: received SIGINT or SIGTERM to terminate. bye!
skilo@laptop1:~$ 

```

Conky does not start.

I can however get conky to start without specifying a config file and just running the command "conky" from the terminal wich then successfully starts conky but it does not load a theme it just uses a default ugly black theme.

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> Ok to make this less confusing, I'm starting over from scratch and going the the instructions on this page - [http://www.unixmen.com/configure-con...t-howto-conky/]("http://www.unixmen.com/configure-conky-lua-in-ubuntu-11-10-12-04-fedora-debian-and-linuxmint-howto-conky/")

My NEW .conkyrc file looks like this now - 
...

If it runs with no errors in the terminal but nothing is displayed it is probably a problem with your settings in this section of your .conkyrc.
```

own_window yes 
own_window_type override 
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```The correct settings depend on your window manager.

"own_window_type override" does not work with all window managers some require
"own_window_type desktop" or "own_window_type normal"

Some window managers like compiz require special scripts to start conky at the right time.

I need to know what your window manager is to help you further.

> **sky5564 said:**
> 
I can however get conky to start without specifying a config file and  just running the command "conky" from the terminal wich then  successfully starts conky but it does not load a theme it just uses a  default ugly black theme.

Since the .conkyrc that is used when you just run conky displays something could you post it so I can see what setting it is using?
It should be located at either ~/.conkyrc or /etc/conky/conky.conf

---

### Post by sky5564 on 2012-05-29
> **arclance said:**
> If it runs with no errors in the terminal but nothing is displayed it is probably a problem with your settings in this section of your .conkyrc.
```

own_window yes 
own_window_type override 
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```The correct settings depend on your window manager.

"own_window_type override" does not work with all window managers some require
"own_window_type desktop" or "own_window_type normal"

Some window managers like compiz require special scripts to start conky at the right time.

I need to know what your window manager is to help you further.



Since the .conkyrc that is used when you just run conky displays something could you post it so I can see what setting it is using?
It should be located at either ~/.conkyrc or /etc/conky/conky.conf

I'm running Lubuntu 12.04 So i guess the window manager is either openbox or LXDE or both?

I'm just running the standard Lubuntu setup i have not changed window managers.

> Since the .conkyrc that is used when you just run conky displays something could you post it so I can see what setting it is using?
It should be located at either ~/.conkyrc or /etc/conky/conky.conf

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

alignment top_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

```

****************UPDATE**************

After following the steps on that page even running "conky" no longer starts conky.

Running the command "conky" now gives this output but never starts.

```
skilo@laptop1:~$ conky
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-foobKz/pkcs11: No such file or directory
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer

```

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> I'm running Lubuntu 12.04 So i guess the window manager is either openbox or LXDE or both?

I'm just running the standard Lubuntu setup i have not changed window managers.

...

****************UPDATE**************

After following the steps on that page even running "conky" no longer starts conky.

Running the command "conky" now gives this output but never starts.

```
skilo@laptop1:~$ conky
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-foobKz/pkcs11: No such file or directory
Conky: desktop window (120012f) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer

```
If you are using the base Lubuntu your window manager should be openbox.

In your .conkyrc try changeing

```

own_window yes  
own_window_type override  
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```to 
```

own_window yes  
own_window_type desktop
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```and see what happens.
If that does not work try using
```

own_window yes  
own_window_type normal
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
```

---

### Post by sky5564 on 2012-05-29
> In your .conkyrc try changeing

Code:
own_window yes  
own_window_type override  
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
to 
Code:
own_window yes  
own_window_type desktop
own_window_transparent yes 
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


You beautiful man....

[IMG]http://s13.postimage.org/me0qdc2jr/desktop_1_003.png[/IMG]

---

### Post by arclance on 2012-05-29
> **sky5564 said:**
> You beautiful man....
[IMG]http://s13.postimage.org/me0qdc2jr/desktop_1_003.png[/IMG]
I thought that would fix it, you usually only need to use override with window managers like compiz.

---

### Post by sky5564 on 2012-05-29
Yep that did the trick, And i thank you very much for your help.

---

