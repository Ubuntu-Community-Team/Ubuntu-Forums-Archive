---
title: "compiz problems"
date: 2010-10-17
forum: General Help
---

### Post by flyingsliverfin on 2010-10-17
im trying to install compiz (ive tried synaptic, apt-get and software center). However, whenever i then go to system -> preference -> appearance ->effects and select anything other than none, it seems to turn of metacity and give me this "Your window manager does not support the show desktop button, or you are not running a window manager." then i click the "no i don't want to keep these settings" and it goes back. The windows have borders with the buttons again.
also after installing ccsm i start it from system -> preferences and nothing happens. it just loads a while then stops.

how can i get it to work?
thx

---

### Post by flyingsliverfin on 2010-10-17
oh and i just looked at dmesg heres what it says for ccsm

```
ccsm[2819]: segfault at 0 ip 002b8073 sp bfc91b1c error 4 in libc-2.10.1.so[245000+13e000]
```

---

### Post by sikander3786 on 2010-10-17
Which version of Ubuntu? Is it an upgrade from a previous version or a fresh install?

---

### Post by flyingsliverfin on 2010-10-17
oh sorry im running 9.10. im pretty sure i upgraded it a long time ago. I had compiz running last week then it had some problems and i removed it. want to try it again but having these problems

---

### Post by sikander3786 on 2010-10-18
Which graphics card are you using? Did you install the proprietary drivers?

---

### Post by blueabysm on 2010-10-18
are you sure that you installed compiz correctly?
it seems like a window decoration problem
try```
compiz --replace
```

good luck

---

### Post by VinDSL on 2010-10-18
> **flyingsliverfin said:**
> im trying to install compiz[...]

how can i get it to work?I've had to (re)install Compiz several times, on various machines.

The only success I've had is:
[LIST=1]
[*]Purge everything having to do with Compiz
[*]Reboot
[*]Install Compiz
[*]Install compiz-fusion-plugins-extra
[*]Reboot
[/LIST]

This works for me 100% of the time.

Compiz is very picky.  When it breaks, it's almost impossible to piece it back together (in my experience).  You're better off just starting from scratch...

I'll attach a screenie showing the 'Compiz files' on my current install.

If my Compiz was broken, I would purge all the files with green boxes to the left, and reinstall them.

---

### Post by flyingsliverfin on 2010-10-24
sorry for not replying i'd just forgotten about compiz for a while but now i want my cube back again :)

im pretty sure i have an nvidia quadro fx 540, and yes i do have a driver installed. uhhh im just using the recommended driver that it shows me (185) how do i know if its proprietary or not? btw this driver used to work so i dont think thats the problem

i ran the compiz --replace and that killed metacity(i think). i used ps -ef to kill the compiz but metacity is still missing... then i ran metacity from the terminal and window borders came back. however, i didnt want to have the terminal running the whole time, i ctrl+c 'd it, now there's no more desktops besides #1, it wont let me type in the terminal. going to restart now

---

### Post by flyingsliverfin on 2010-10-24
ok after a restart metacity's working again and so are the other desktops and window borders etc.

ill try ur purge after i finish my hw and have some more time

---

### Post by VinDSL on 2010-10-24
> **flyingsliverfin said:**
> im pretty sure i have an nvidia quadro fx 540, and yes i do have a driver installed. uhhh im just using the recommended driver that it shows me (185) how do i know if its proprietary or not?'185' is a proprietary driver.

I'm running 260.19.12 on an ancient nVidia GeForce 7600 GT, but your card might require '185'.

> **flyingsliverfin said:**
> ill try ur purge after i finish my hw and have some more timePurging and doing a fresh Compiz install always works for me.

Just took a screenie...


[INDENT][IMG]http://vindsl.com/images/works-4-me%28550x440%29.png[/IMG][/INDENT]

Good luck!  ;)

---

### Post by Dans564 on 2010-10-24
> **VinDSL said:**
> '185' is a proprietary driver.

I'm running 260.19.12 on an ancient nVidia GeForce 7600 GT, but your card might require '185'.

Purging and doing a fresh Compiz install always works for me.

Just took a screenie...


[INDENT][IMG]http://vindsl.com/images/works-4-me%28550x440%29.png[/IMG][/INDENT]

Good luck!  ;)

VinDSL,
would u by any chance like to post your conky config.  its super cool looking. :)

---

### Post by VinDSL on 2010-10-24
> **Dans564 said:**
> VinDSL,
would u by any chance like to post your conky config.  its super cool looking. :)
My pleasure......


([COLOR="Navy"]Desktop[/COLOR] - Click image for full-size view)
[INDENT][INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-oct-2010(550x413).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-oct-2010.png")[/INDENT][/INDENT]


([COLOR="Navy"]Working[/COLOR] - Click image for full-size view)
[INDENT][INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-28-oct-2010(550x413).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-28-oct-2010.png")[/INDENT][/INDENT]


```

 ##\\\\\\\\\\\\\|/////////////##
##  [COLOR="#FF9900"]~ [COLOR="#CC3333"]VinDSL[/COLOR] ~[/COLOR]  |  [COLOR="DarkGreen"]Screen Res[/COLOR]  ##
##  [[COLOR="Blue"]On The Web[/COLOR]]("http://www.google.com/search?q=vindsl")  | [COLOR="Purple"]1280x1024x24[/COLOR] ##
 ##/////////////|\\\\\\\\\\\\\##


####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont LiberationSans:size=9
xftalpha 0.1
text_buffer_size 2048

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_transparent yes

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_console no
out_to_ncurses no

####
## Text alignment.
#
alignment top_right

####
## Minimum size of text area.
#
minimum_size 235 0

####
## Specify width and height for bars.
#
default_bar_size 0 4

####
## Gap between text and screen borders.
#
gap_x 18
gap_y 28

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system buffers from used memory?
#
no_buffers no

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors.
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black

TEXT

##################
##     LOGO     ##
##################
${voffset -42}${color2}${font OpenLogos:size=103}v${voffset -66}${goto 178}${font UbuntuTitleBold:size=20}${color4}10.10
##################
##    SYSTEM    ##
##################
${voffset 10}${font Arial:bold:size=10}${color4}SYSTEM ${color8} ${hr 2}
${voffset 4}${color2}${font OpenLogos:size=10}u${voffset -4}${font}${color6} ${sysname} ${kernel} ${alignr} ${machine}
${voffset 2}${color2}${font StyleBats:size=10}A${voffset -1}${font}${color6} Intel P4 Extreme Edition ${alignr}${freq_g cpu0} GHz
${voffset 2}${color2}${font StyleBats:size=10}q${voffset -1}${font}${color6} Uptime ${alignr}${uptime}
${voffset 2}${color2}${font StyleBats:size=10}o${voffset -1}${font}${color6} File System ${alignr}${fs_type}
##################
##  PROCESSORS  ##
##################
${voffset 5}${font Arial:bold:size=10}${color4}PROCESSORS ${color8}${hr 2}
${voffset 2}${color2}${font StyleBats:size=10}k${voffset -2}${font}${color6} CPU1  ${cpu cpu1}%${color7}${alignc 35}${cpubar cpu1}
${voffset 2}${color2}${font StyleBats:size=10}k${voffset -2}${font}${color6} CPU2  ${cpu cpu2}%${color7}${alignc 35}${cpubar cpu2}
##################
##    MEMORY    ##
##################
${voffset 3}${font Arial:bold:size=10}${color4}MEMORY ${color8}${hr 2}
${voffset 2}${color2}${font StyleBats:size=10}l${voffset -2}${font}${color6} RAM ${goto 95}${mem}/ ${memmax}${alignr}${memperc}%
${color7}${membar}
##################
##     HDD      ##
##################
${voffset 3}${font Arial:bold:size=10}${color4}HDD ${color8}${hr 2}
${voffset 2}${color2}${font StyleBats:size=10}x${voffset -2}${font}${color6} ROOT ${goto 95}${fs_used /} / ${fs_size /}${alignr}${fs_free_perc /}%
${color7}${fs_bar /}
${voffset 2}${color2}${font StyleBats:size=10}x${voffset -2}${font}${color6} HOME ${goto 95}${fs_used /home}/ ${fs_size /home}${alignr}${fs_free_perc /home}%
${color7}${fs_bar /home}
${voffset 2}${color2}${font StyleBats:size=10}4${voffset -2}${font}${color6} SWAP ${goto 95}${swap} / ${swapmax}${alignr}${swapperc}%
${color7}${swapbar}
##################
# TOP PROCESSES ##
##################
${voffset 3}${font Arial:bold:size=10}${color4}TOP PROCESSES ${color8}${hr 2}
${voffset 2}${color1}${font StyleBats:size=10}h${voffset -3}${font}${color6} ${top_mem name 1}${goto 115}${top_mem mem_res 1}${alignr}${top mem 1}%
${voffset 2}${color1}${font StyleBats:size=10}h${voffset -3}${font}${color6} ${top_mem name 2}${goto 115}${top_mem mem_res 2}${alignr}${top mem 2}%
${voffset 2}${color1}${font StyleBats:size=10}h${voffset -3}${font}${color6} ${top_mem name 3}${goto 115}${top_mem mem_res 3}${alignr}${top mem 3}%
${voffset 2}${color1}${font StyleBats:size=10}h${voffset -3}${font}${color6} ${top_mem name 4}${goto 115}${top_mem mem_res 4}${alignr}${top mem 4}%
${voffset 2}${color1}${font StyleBats:size=10}h${voffset -3}${font}${color6} ${top_mem name 5}${goto 115}${top_mem mem_res 5}${alignr}${top mem 5}%
##################
##   NETWORK    ##
##################
${voffset 5}${font Arial:bold:size=10}${color4}NETWORK ${color8}${hr 2}
${voffset 2}${color2}${font PizzaDude Bullets:size=10}a${font}${color6} IPs on eth0${alignr}${addr eth0} / ${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${color2}${font PizzaDude Bullets:size=10}T${font}${color6} Down${alignr}${downspeed eth0}
${color2}${font PizzaDude Bullets:size=10}N${font}${color6} Up${alignr}${upspeed eth0}
${voffset 4}${color2}${font PizzaDude Bullets:size=10}T${font}${color6} Downloaded${alignr}${totaldown eth0}
${color2}${font PizzaDude Bullets:size=10}N${font}${color6} Uploaded${alignr}${totalup eth0}
##################
##   WEATHER    ##
##################
${voffset 5}${font Arial:bold:size=10}${color4}WEATHER ${color8}${hr 2}
${goto 65}${color1}${font Weather:size=40}y${voffset -8}${font RadioSpace:size=32}${color3} ${execpi 600 conkyForecast --imperial --location=USAZ0082}
${voffset -20}${font Arial:size=20}${color4}${alignc}${execi 600 conkyForecast --location=USAZ0082 --datatype=CT}
${goto 70}${font ConkyWeather:style=Bold:size=40}${color2}${execi 600 conkyForecast --location=USAZ0082 --datatype=WF}${goto 140}${font ConkyWindNESW:style=Bold:size=40}${color2}${execi 600 conkyForecast --location=USAZ0082 --datatype=BS}
${voffset -28}${goto 60}${font}${color2}Feels like ${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=LT --centeredwidth=4 -iu}${goto 150}${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=WS}
${voffset 7}${goto 53}${font}${color2}${execi 600 conkyForecast --location=USAZ0082 --datatype=DW --startday=1 --shortweekday}${goto 119}${execi 600 conkyForecast --location=USAZ0082 --datatype=DW --startday=2 --shortweekday}${goto 182}${execi 600 conkyForecast --location=USAZ0082 --datatype=DW --startday=3 --shortweekday}
${goto 43}${font}${color2}${font ConkyWeather:size=32}${execi 600 conkyForecast --location=USAZ0082 --datatype=WF --startday=1 --endday=3 --spaces=2}
${voffset -30}${goto 41}${font}${color2}${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=HT --startday=1 --hideunits --centeredwidth=4 -iu}/${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=LT --startday=1 --hideunits --centeredwidth=4 -iu}${goto 107}${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=HT --startday=2 --hideunits --centeredwidth=4 -iu}/${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=LT --startday=2 --hideunits --centeredwidth=4 -iu}${goto 172}${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=HT --startday=3 --hideunits --centeredwidth=4 -iu}/${execi 600 conkyForecast --location=USAZ0082 --imperial --datatype=LT --startday=3 --hideunits --centeredwidth=4 -iu}
##################
##     TIME     ##
##################
${voffset 2}${font Arial:bold:size=10}${color4}TIME ${color8}${hr 2}
${voffset -5}${font RadioSpace:size=32}${color3}${alignc}${time %l:%M%p}
${voffset -30}${font LiberationSans:size=10}${color4}${alignc}${time %A},${offset 5}${time %d %b %Y}
${voffset 2}${font Liberation Mono:size=9.5}${color3}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                    /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc -2} /' | sed /" $DJS "/s/" $DJS "/" "'${color4}'"$DJS"'${color3}'" "/}
${font LiberationSans:size=8.5}${color4}${alignc} Rise ${execi 3600 conkyForecast --location=USAZ0082 --datatype=SR --startday=1} | Set ${execi 3600 conkyForecast --location=USAZ0082 --datatype=SS --startday=1}

```


[INDENT][COLOR="Navy"]Desktop Fonts:[/COLOR]
[LIST][*]Application font: Liberation Sans (11)
[*]Document font: Liberation Sans (10)
[*]Desktop font: Liberation Sans (10)
[*]Window title font: Liberation Sans (11)
[*]Fixed width font: Liberation Mono (10)
[*]Rendering: Subpixel smoothing (LCDs)[/LIST]
[COLOR="Navy"]Desktop Theme:[/COLOR]
[LIST][*]Base Theme: Ambiance
[*]Controls: New Wave
[*]Colors: (Default)
[*]Window Border: New Wave
[*]Icons: Human (Skinned with Breathe Icon Set)
[*]Pointer: DMZ (White)
[*]Current Background: Fantasy Dragon Wallpaper (author unknown)[/LIST]
[COLOR="Navy"]Desktop Apps:[/COLOR]
[LIST][*]Conky
[*]ConkyForecast
[*]Compiz-Fusion
[/LIST]
[COLOR="Navy"]Conky / ConkyForecast Fonts:[/COLOR]
[LIST][*]Arial
[*]ConkyWeather
[*]ConkyWindNESW
[*]LiberationSans
[*]OpenLogos
[*]PizzaDude
[*]RadioSpace
[*]StyleBats
[*]UbuntuTitleBold
[*]Weather (by Jonathan Macagba)
[/LIST]
[COLOR="Navy"]Firefox Theme/Persona:[/COLOR]
[LIST][*]Zilla Spec (by Nerdski)
[/LIST][/INDENT]

---

### Post by flyingsliverfin on 2010-10-24
i got it working again with the purge idea :) thanks a lot now i have my old configs back again.

---

### Post by VinDSL on 2010-10-24
> **flyingsliverfin said:**
> i got it working again with the purge idea :) thanks a lot now i have my old configs back again.Sweet!  :D

---

### Post by gwu777 on 2010-10-25
Hi there,

Sorry to be a troublemaker, however the purge idea didn't work for me! I have purged and removed every compiz package I could, reinstalled it and I have the same problem:

When I restart, I need to do a compiz --replace to get compize working and the windows manager.

Now of course I could add that command into my starting apps, but I REALLY would like to understand why this behavior happen.

It used to work a little while ago. I have an ATI HD3200 card without the prioritary drivers (although it still doesn't work with them!)

I have been in confeditor and made sure that compix was my default windows manager which it is.

Please I need ideas...

---

### Post by flyingsliverfin on 2010-10-25
i thought compiz could be used only for the effects and not to replace metacity too. or does that mean if i have the cube that i have compiz as the window manager too?

did u do the complete remove from synaptic?

oh and any1 know the command for seeing all the related files to a specific package? im pretty sure it was something with dpkg

---

### Post by gwu777 on 2010-10-26
> **flyingsliverfin said:**
> 
did u do the complete remove from synaptic?


I have removed compiz via apt-get --purge

The fact is that compiz work fine it just doesn't start properly.

Here is another question, why I put my effects to none, I lose anykind of windows manager. Shouldn't something take over when compiz is disabled?

---

### Post by VinDSL on 2010-10-26
> **gwu777 said:**
> Here is another question, why I put my effects to none, I lose anykind of windows manager. Shouldn't something take over when compiz is disabled?Metacity is the windows manager.  Make sure it's installed/enabled.

Also, when you're running Compiz, make sure Metacity Compositing is disabled.

Put another way, you should have Compiz and Metacity enabled, with Metacity Compositing disabled.

I can't speak for everyone, but that's the way I do it...  ;)

---

### Post by flyingsliverfin on 2010-10-26
how do i check if ive got metacity (or compositing) and/or compiz enabled?

---

### Post by VinDSL on 2010-10-27
> **flyingsliverfin said:**
> how do i check if ive got metacity (or compositing) and/or compiz enabled?You cannot beat Ubuntu Tweak for slothfulness!  ;)


(Click image for full-size view)
[INDENT][[IMG]http://vindsl.com/images/ubu-tweak-26-oct-2010(550x440).png[/IMG]]("http://vindsl.com/images/ubu-tweak-26-oct-2010.png")
[/INDENT]

Ubuntu developers greatly prefer using Compiz for the windows manager over GNOME's Mutter windows manager. 

That's fine and dandy, but...

When Compiz breaks, you need Metacity for the fall-back!

---

### Post by gwu777 on 2010-10-28
> **VinDSL said:**
> You cannot beat Ubuntu Tweak for slothfulness!  ;)


I have just discovered this program myself and it is VERy usefull indeed.

After several test, I am not convinced this problem is linked to compiz. I do have a problem in my settings, but it seems that no windows manager is loaded at start automatically, whether it be compiz, metacity or gnome-wm. I shall start a new threat for my problem. Good luck to all with you compiz issu!

---

### Post by flyingsliverfin on 2010-10-29
is there a command line equivalent of ubuntu tweak? im trying to get used to using it more beyond the basics

---

### Post by VinDSL on 2010-10-30
> **flyingsliverfin said:**
> is there a command line equivalent of ubuntu tweak? im trying to get used to using it more beyond the basicsTo disable/enable Metacity compositing?

The command line switch to disable Metacity compositing is...

```
gconftool --set -t boolean /apps/metacity/general/compositing_manager [COLOR="Red"]false[/COLOR]
```

To enable Metacity compositing...

```
gconftool --set -t boolean /apps/metacity/general/compositing_manager [COLOR="Red"]true[/COLOR]
```

---

### Post by flyingsliverfin on 2010-10-30
will anything bad happen if i try it or should i do it in a virtual ubuntu so nothing gets too messed up?

---

### Post by VinDSL on 2010-10-31
> **flyingsliverfin said:**
> will anything bad happen if i try it or should i do it in a virtual ubuntu so nothing gets too messed up?You won't mess anything up, if you type the command switch correctly.  :D

If this worries you, just use gconf-editor (Gnome Configuration Editor) and check/uncheck the box.

```
gconf-editor /apps/metacity/general/compositing_manager
```

I strongly suggest NOT running Compiz and Metacity Compositing, at the same time.  Doing this usually borks Compiz.

Put another way, run Compiz, or run Metacity Compositing, but don't run them at the same time.  ;)

---

