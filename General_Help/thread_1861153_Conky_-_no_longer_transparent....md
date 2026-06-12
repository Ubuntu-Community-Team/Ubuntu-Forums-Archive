---
title: "Conky - no longer transparent..."
date: 2011-10-15
forum: General Help
---

### Post by Kevbert on 2011-10-15
I've recently moved over to Xubuntu 11.10 (from Ubuntu). My old conky script was fine in Ubuntu but is no longer transparent in Xubuntu. I'm also using DesktopNova to change background wallpaper. 
Do I need any new programs for this to work ?

My script:
```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
cpu_avg_samples 2
uppercase no
text_buffer_size 1024
override_utf8_locale yes

TEXT
${color orange}SYSTEM ${color white}${hr 1}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime

CPU: ${alignr}${freq} MHz
Temp ${goto 42}Core 0: ${alignr}${exec sensors | grep "Core 0" | awk '{print $3}'}
     ${goto 42}Core 1: ${alignr}${exec sensors | grep "Core 1" | awk '{print $3}'}

Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${goto 65}${cpu cpu1}%${goto 117}CPU2 ${goto 180}${cpu cpu2}%
${color orange}${cpugraph cpu1 20,107 FFFF00 FF0000}$alignr${cpugraph cpu2 20,107 FFFF00 FF0000}

${color}Ram ${alignr}$mem / $memmax ($memperc%)
${color orange}${membar 4}
${color}Swap ${alignr}$swap / $swapmax ($swapperc%)
${color orange}${swapbar 4}

${color}Highest CPU ${goto 140}CPU%${alignr}MEM%
${color red}${top name 1}${goto 140}${top cpu 1}${alignr}${top mem 1} 
${color orange}${top name 2}${goto 140}${top cpu 2}${alignr}${top mem 2} 
${color orange}${top name 3}${goto 140}${top cpu 3}${alignr}${top mem 3} 

${color}Highest MEM ${goto 140}CPU% ${alignr}MEM%
${color red}${top_mem name 1}${goto 140}${top_mem cpu 1}${alignr}${top_mem mem 1} 
${color orange}${top_mem name 2}${goto 140}${top_mem cpu 2}${alignr}${top_mem mem 2} 
${color orange}${top_mem name 3}${goto 140}${top_mem cpu 3}${alignr}${top_mem mem 3} 

${color orange}FILESYSTEM ${color white}${hr 1}

Root:${goto 65}${fs_free_perc /}%${goto 117}Home:${goto 180}${fs_free_perc /home}%
${color orange}${fs_bar 4,108 /}${alignr}${fs_bar 4,108 /home}
${color}Used: ${fs_used /}${goto 150}${fs_used /home}

${color orange}NETWORK ${color white}${hr 1}

${color}Eth0 Down ${downspeed eth0}/s ${alignr}Up ${upspeed eth0}/s
${color orange}${downspeedgraph eth0 20,107 FFFF00 FF0000}$alignr${upspeedgraph eth0 20,107 FFFF00 FF0000}
${color}Totals: Wlan0 ${totaldown wlan0} ${alignr}${totalup wlan0}
${color}Totals: Eth0  ${totaldown eth0} ${alignr}${totalup eth0}

Ports in use${goto 80}Privileged 1-1024  ${alignr}${tcp_portmon 1 1024 count} 
${goto 80}Other 1025 - 65535 ${alignr}${tcp_portmon 1025 65535 count} 

${color orange}WEATHER ${color white}${hr 1}

${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=CC}${goto 120}Hailsham,E.Sussex
${goto 120}Wind:${alignr}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=WS -i} ${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=WD}
${voffset -10}${goto 20}${font Weather:size=45}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=WF}
${alignc -5}${voffset -45}${font size=15}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=HT}
$font${voffset -65}${goto 120}Gusts:${alignr}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=WG -i} 
${goto 120}Humidity:${alignr}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=HM}
${goto 120}Rain:${alignr}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=PC}
${goto 120}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=BR}${alignr}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=BD}

Sunrise: ${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=SR}${alignr}Sunset: ${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=SS}
${voffset 12}Moon Phase: ${voffset -3}${goto 110}${font moon phases:size=15}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --datatype=MF}$font$color

${color orange}Four Day Forecast...
${color}${font weather:size=30}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX1537 --startday=1 --endday=4 --datatype=WF --spaces=8}$font$color
${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=1 --datatype=DW --shortweekday}${goto 66}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=2 --datatype=DW --shortweekday}${goto 130}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=3 --datatype=DW --shortweekday}${alignr}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=4 --datatype=DW --shortweekday}  
${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=1 --datatype=HT}${goto 66}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=2 --datatype=HT}${goto 130}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=3 --datatype=HT}${alignr}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=4 --datatype=HT}  
${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=1 --datatype=LT}${goto 66}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=2 --datatype=LT}${goto 130}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=3 --datatype=LT}${alignr}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=4 --datatype=LT}  
${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=1 --datatype=PC}${goto 66}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=2 --datatype=PC}${goto 130}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=3 --datatype=PC}${alignr}${execi 3600 python /home/kevin/.scripts/conkyForecast.py --location=UKXX1537 --startday=4 --datatype=PC}  
${hr 1}

```

---

### Post by TeoBigusGeekus on 2011-10-15
Screenshot?

---

### Post by Kevbert on 2011-10-15
Screenshot here...

---

### Post by TeoBigusGeekus on 2011-10-15
No problem here.
Have you tried delaying the conky command at startup using sleep?

---

### Post by Kevbert on 2011-10-15
Thanks for the quick reply.
Yes, I use a bash script to delay startup as I'm also accessing the web for weather data.

---

### Post by TeoBigusGeekus on 2011-10-15
Try increasing the number of seconds in the sleep command.

---

### Post by Toz on 2011-10-15
In your. conkyrc file, add:
```

own_window_argb_visual yes
own_window_argb_value 0

```

---

### Post by Kevbert on 2011-10-16
TeoBigusGeekus - the change in timing made no difference.
Toz - thanks. Adding the extra lines solved the problem. It seems strange that I need these lines in Xubuntu, but not in Ubuntu.:):):)

---

### Post by tomski on 2011-10-16
thanks for the help :)

---

### Post by TeoBigusGeekus on 2011-10-16
Never heard of these variables/settings, but I'm glad they worked for you.

---

### Post by iamnotthemessiah on 2011-10-16
i had this problem too in xubuntu and added those two lines..

result now is that my panel dies and i have to reboot. this is with compiz running
the config now looks like
```
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 0
```

any help? how should all these settings look?

---

### Post by Quackers on 2011-10-16
> **Kevbert said:**
> TeoBigusGeekus - the change in timing made no difference.
Toz - thanks. Adding the extra lines solved the problem. It seems strange that I need these lines in Xubuntu, but not in Ubuntu.:):):)

Doesn't xubuntu use xfce? I think xfce desktop is drawn differently and requires the argb line(s) to achieve transparency.

---

### Post by Quackers on 2011-10-16
> **iamnotthemessiah said:**
> i had this problem too in xubuntu and added those two lines..

result now is that my panel dies and i have to reboot. this is with compiz running
the config now looks like
```
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 0
```

any help? how should all these settings look?
Have you tried setting ```
own_window_type override
``` 
to
```
own_window_type normal
```
or
```
own_window_type desktop
```
What happens if you do?

---

### Post by Kevbert on 2011-10-16
> **Quackers said:**
> Doesn't xubuntu use xfce? I think xfce desktop is drawn differently and requires the argb line(s) to achieve transparency.

Thanks for the clarification ;)

---

### Post by Kevbert on 2011-10-16
> **iamnotthemessiah said:**
> i had this problem too in xubuntu and added those two lines..

result now is that my panel dies and i have to reboot. this is with compiz running
the config now looks like
```
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 0
```

any help? how should all these settings look?

You may need to use
```
own_window_type normal
``` instead of override.
Please post your full script as it may be something else causing the problem.

---

### Post by slumbergod on 2011-10-16
changing from override to normal fixed it for my xubuntu installation

---

### Post by Toz on 2011-10-16
Here is a reference link that notes these new settings and a brief blurb warning about complications using own_window_type override.

[http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

---

### Post by iamnotthemessiah on 2011-10-17
changing from override to normal almost fixed it for me as well, it works now, however when conky starts the desktop flickers and windows are moved around a little bit, as if compiz --replace was executed

heres the full thing

```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 2
cpu_avg_samples 2

imlib_cache_size 0
double_buffer yes
#no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont DejaVu Sans:size=8:weight=bold
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar
own_window_argb_visual yes
own_window_argb_value 0

alignment br
gap_x 4
gap_y 28
minimum_size 142 66
maximum_width 142


default_bar_size 68 8

#########################
# - Graphics settings - #
#########################
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
border_inner_margin 0
border_outer_margin 0
default_color DFDBD2
default_shade_color 1d1d1d
color0 ffffff
color1 ffffff
color2 ffffff


TEXT
Total UP:${alignr}${totalup ppp0}
${voffset 4}${font PizzaDude Bullets:size=20}N${font} ${upspeed ppp0} ${voffset -13}${alignr}${upspeedgraph ppp0 22,60 400}
Total DOWN:${alignr}${totaldown ppp0}
${voffset 4}${font PizzaDude Bullets:size=20}U${font} ${downspeed ppp0} ${voffset -13}${alignr}${downspeedgraph ppp0 22,60 600}
```

---

### Post by Kevbert on 2011-10-17
Seems to work here... You may need to increase the number of averages and change the update interval.

---

### Post by hilltop_yodeler on 2011-10-17
> **Quackers said:**
> Have you tried setting ```
own_window_type override
``` 
to
```
own_window_type normal
```


Quackers, this method worked great for me, thank you!

---

### Post by iamnotthemessiah on 2011-10-18
yeah that worked for me too however now ive got a new problem, my bars and graphs arent the colour ive specified
for example
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 2
cpu_avg_samples 2

imlib_cache_size 0
double_buffer yes
#no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont DejaVu Sans:size=8:weight=bold
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar
own_window_argb_visual yes
own_window_argb_value 0

alignment br
gap_x 4
gap_y 28
minimum_size 142 66
maximum_width 142


default_bar_size 68 8

#########################
# - Graphics settings - #
#########################
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
border_inner_margin 0
border_outer_margin 0
default_color DFDBD2
default_shade_color DFDBD2
color0 DFDBD2
color1 DFDBD2
color2 DFDBD2


#lua_load ~/.conky/conkybg.lua
#lua_draw_hook_pre conky_draw_bg
TEXT
Total UP:${alignr}${totalup ppp0}
${voffset 4}${font PizzaDude Bullets:size=20}N${font} ${upspeed ppp0} ${voffset -13}${alignr}${upspeedgraph ppp0 22,60 400}
Total DOWN:${alignr}${totaldown ppp0}
${voffset 4}${font PizzaDude Bullets:size=20}U${font} ${downspeed ppp0} ${voffset -13}${alignr}${downspeedgraph ppp0 22,60 600}
```

here the graphs should be DFDBD2 but they are FFFFFF
ive also tried adding ${color DFDBD2} pretty much everywhere in the code but no change...they were the right colour in 11.04 xubuntu

---

### Post by Kevbert on 2011-10-19
Interesting.
default_color dfdb00 works (a shade of yellow)
but dfdbbd2 shows white.  May be a bug...

---

### Post by Sector11 on 2012-01-21
> **Kevbert said:**
> Interesting.
default_color dfdb00 works (a shade of yellow)
but dfdbbd2 shows white.  May be a bug...

Probably because you have 7 characters.  Hex code uses 6, drop the "2"  :D

Colour picker in gedit is a great tool!

Conky will recognize the Hex Code, more choices, or these HTML Names:
```

Hex		Decimal		142 colours
code		code			HTML name

	Red colors
CD5C5C 	205  92  92	IndianRed
F08080 	240 128 128	LightCoral
FA8072 	250 128 114	Salmon
E9967A 	233 150 122	DarkSalmon
FFA07A 	255 160 122	LightSalmon
DC143C 	220  20  60	Crimson
FF0000 	255   0   0	Red
B22222 	178  34  34	FireBrick
8B0000 	139   0   0	DarkRed

	Pink colors
FFC0CB 	255 192 203	Pink
FFB6C1 	255 182 193	LightPink
FF69B4 	255 105 180	HotPink
FF1493 	255  20 147	DeepPink
C71585 	199  21 133	MediumVioletRed
DB7093 	219 112 147	PaleVioletRed

	Orange colors
FFA07A 	255 160 122	LightSalmon
FF7F50 	255 127  80	Coral
FF6347 	255  99  71	Tomato
FF4500 	255  69   0	OrangeRed
FF8C00 	255 140   0	DarkOrange
FFA500 	255 165   0	Orange

	Yellow colors
FFD700 	255 215   0	Gold
FFFF00 	255 255   0	Yellow
FFFFE0 	255 255 224	LightYellow
FFFACD 	255 250 205	LemonChiffon
FAFAD2 	250 250 210	LightGoldenrodYellow
FFEFD5 	255 239 213	PapayaWhip
FFE4B5 	255 228 181	Moccasin
FFDAB9 	255 218 185	PeachPuff
EEE8AA 	238 232 170	PaleGoldenrod
F0E68C 	240 230 140	Khaki
BDB76B 	189 183 107	DarkKhaki

	Purple colors
E6E6FA 	230 230 250	Lavender
D8BFD8 	216 191 216	Thistle
DDA0DD 	221 160 221	Plum
EE82EE 	238 130 238	Violet
DA70D6 	218 112 214	Orchid
FF00FF 	255   0 255	Fuchsia
FF00FF 	255   0 255	Magenta
BA55D3 	186  85 211	MediumOrchid
9370DB 	147 112 219	MediumPurple
8A2BE2 	138  43 226	BlueViolet
9400D3 	148   0 211	DarkViolet
9932CC 	153  50 204	DarkOrchid
8B008B 	139   0 139	DarkMagenta
800080 	128   0 128	Purple
4B0082 	 75   0 130	Indigo
6A5ACD 	106  90 205	SlateBlue
483D8B 	 72  61 139	DarkSlateBlue
7B68EE 	123 104 238	MediumSlateBlue

	Green colors
ADFF2F 	173 255  47	GreenYellow
7FFF00 	127 255   0	Chartreuse
7CFC00 	124 252   0	LawnGreen
00FF00 	  0 255   0	Lime
32CD32 	 50 205  50	LimeGreen
98FB98 	152 251 152	PaleGreen
90EE90 	144 238 144	LightGreen
00FA9A 	  0 250 154	MediumSpringGreen
00FF7F 	  0 255 127	SpringGreen
3CB371     60 179 113	MediumSeaGreen
2E8B57 	 46 139  87	SeaGreen
228B22 	 34 139  34	ForestGreen
008000 	  0 128   0	Green
006400 	  0 100   0	DarkGreen
9ACD32 	154 205  50	YellowGreen
6B8E23 	107 142  35	OliveDrab
808000 	128 128   0	Olive
556B2F 	 85 107  47	DarkOliveGreen
66CDAA 	102 205 170	MediumAquamarine
8FBC8F 	143 188 143	DarkSeaGreen
20B2AA 	 32 178 170	LightSeaGreen
008B8B 	  0 139 139	DarkCyan
008080 	  0 128 128	Teal

	Blue/Cyan colors
00FFFF 	  0 255 255	Aqua
00FFFF 	  0 255 255	Cyan
E0FFFF 	224 255 255	LightCyan
AFEEEE 	175 238 238	PaleTurquoise
7FFFD4 	127 255 212	Aquamarine
40E0D0 	 64 224 208	Turquoise
48D1CC 	 72 209 204	MediumTurquoise
00CED1 	  0 206 209	DarkTurquoise
5F9EA0 	 95 158 160	CadetBlue
4682B4 	 70 130 180	SteelBlue
B0C4DE 	176 196 222	LightSteelBlue
B0E0E6 	176 224 230	PowderBlue
ADD8E6 	173 216 230	LightBlue
87CEEB 	135 206 235	SkyBlue
87CEFA 	135 206 250	LightSkyBlue
00BFFF 	  0 191 255	DeepSkyBlue
1E90FF 	 30 144 255	DodgerBlue
6495ED 	100 149 237	CornflowerBlue
7B68EE 	123 104 238	MediumSlateBlue
4169E1 	 65 105 225	RoyalBlue
0000FF 	  0   0 255	Blue
0000CD 	  0   0 205	MediumBlue
00008B 	  0   0 139	DarkBlue
000080 	  0   0 128	Navy
191970 	 25  25 112	MidnightBlue

	Brown colors
FFF8DC 	255 248 220	Cornsilk
FFEBCD 	255 235 205	BlanchedAlmond
FFE4C4 	255 228 196	Bisque
FFDEAD 	255 222 173	NavajoWhite
F5DEB3 	245 222 179	Wheat
DEB887 	222 184 135	BurlyWood
D2B48C 	210 180 140	Tan
BC8F8F 	188 143 143	RosyBrown
F4A460 	244 164  96	SandyBrown
DAA520 	218 165  32	Goldenrod
B8860B 	184 134  11	DarkGoldenrod
CD853F 	205 133  63	Peru
D2691E 	210 105  30	Chocolate
8B4513 	139  69  19	SaddleBrown
A0522D 	160  82  45	Sienna
A52A2A 	165  42  42	Brown
800000 	128   0   0	Maroon

	White colors
FFFFFF 	255 255 255	White
FFFAFA 	255 250 250	Snow
F0FFF0 	240 255 240	Honeydew
F5FFFA 	245 255 250	MintCream
F0FFFF 	240 255 255	Azure
F0F8FF 	240 248 255	AliceBlue
F8F8FF 	248 248 255	GhostWhite
F5F5F5 	245 245 245	WhiteSmoke
FFF5EE 	255 245 238	Seashell
F5F5DC 	245 245 220	Beige
FDF5E6 	253 245 230	OldLace
FFFAF0 	255 250 240	FloralWhite
FFFFF0 	255 255 240	Ivory
FAEBD7 	250 235 215	AntiqueWhite
FAF0E6 	250 240 230	Linen
FFF0F5 	255 240 245	LavenderBlush
FFE4E1 	255 228 225	MistyRose

	Gray colors
DCDCDC 	220 220 220	Gainsboro
D3D3D3 	211 211 211	LightGrey
C0C0C0 	192 192 192	Silver
A9A9A9 	169 169 169	DarkGray
808080 	128 128 128	Gray
696969 	105 105 105	DimGray
778899 	119 136 153	LightSlateGray
708090 	112 128 144	SlateGray
2F4F4F 	 47  79  79	DarkSlateGray
000000 	  0   0   0	Black

```

---

### Post by princemackenzie on 2012-07-02
Just wanted to stop by and thank everyone in this thread for sorting some of Conky issues with xubuntu!

---

