---
title: "Conky - where do I begin? It looks fairly overwhelming"
date: 2010-10-19
forum: General Help
---

### Post by Cavsfan on 2010-10-19
I've seen a lot of Conky examples and I think I would like to set one up, but googling how to do conky doesn't seem to net much.

I would just like to have on the right side of my screen the info. from my CPU, video card, the weather and some other stuff.
I also have compiz, cairo dock and emerald wm all maxed out.
It is already installed and when I enter **conky -v** I get this:```
Conky 1.8.0 compiled Fri Apr 23 10:42:08 UTC 2010 for Linux 2.6.24-27-server (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```I have Maverick 64 bit.
Thanks in advance for any help! :)

---

### Post by wojox on 2010-10-19
Start out slow to get a feel for configuring it. This helped me [ubuntugeek]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html").

As far as the weather there is a thread around here to help you configure that. [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328&highlight=conky+weather") & [Conky Lua & Cairo Troubleshooting]("http://ubuntuforums.org/showthread.php?t=1280453&highlight=conky+weather")

---

### Post by Quackers on 2010-10-19
Here's my screenshot, .conkyrc and weather.template to give you some ideas.
.conkyrc
```
alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
xftfont terminus:size=11
gap_x 10
gap_y 50
maximum_width 320
minimum_size 300 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096

TEXT
${font Terminus:style=bold:size=11}SYSTEM $hr
${font}$sysname $kernel $alignr $machine
Host: $alignr $nodename
Temp: $alignr ${acpitemp}C
${color light blue}
${font Terminus:style=bold:size=11}PROCESSORS $hr
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color pink}
${font Terminus:style=bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
${color orange}
${font Terminus:style=bold:size=11}DISKS $hr
${font}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
${color red}
${font Terminus:style=bold:size=11}BATTERY $hr
${battery_percent BAT0}% ${battery_bar BAT0}
${color green}
${font Terminus:style=bold:size=11}TOP PROCESSES $hr
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
${color yellow}
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
${execpi 1800 conkyForecast --location=UKXX0092 --template=/home/mike64/weather.template}
$hr
${font Terminus:style=bold:size=11}${time %k:%M}${alignr}${time %a/%b/%d}
```

weather.template
```

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}TODAY $hr

${color1}${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT]
${image [--location=UKXX0092 --datatype=WI] -p 0,610 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS]${font}

[--location=UKXX0092 --datatype=HT]                               [--location=UKXX0092 --datatype=WS --imperial]  [--location=UKXX0092 --datatype=WD]

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}TOMORROW ${hr}

${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT --startday=1]
${image [--location=UKXX0092 --datatype=WI --startday=1] -p 0,775 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS --startday=1]${font}

[--location=UKXX0092 --datatype=HT --startday=1] / [--location=UKXX0092 --datatype=LT --startday=1]                       [--location=UKXX0092 --datatype=WS --imperial --startday=1]  [--location=UKXX0092 --datatype=WD --startday=1]

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}DAY AFTER $hr

${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT --startday=2]
${image [--location=UKXX0092 --datatype=WI --startday=2] -p 0,935 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS --startday=2]${font}

[--location=UKXX0092 --datatype=HT --startday=2] / [--location=UKXX0092 --datatype=LT --startday=2]                       [--location=UKXX0092 --datatype=WS --imperial --startday=2]  [--location=UKXX0092 --datatype=WD --startday=2]
```

---

### Post by Cavsfan on 2010-10-20
Thank you so much!!! This is great! I will begin the learning process. And thanks **Quackers** for providing that as that looks to be exactly 
what I would want. Everytime I have ever looked at Conky before it just looked so unimaginably "large" if you know what I mean. But, 
knowledge is power and makes things appear "smaller" in the end.
Thanks again! :)

---

### Post by Cavsfan on 2010-10-20
Well I can't seem to get Network Quality to display. It always shows "0%" with this line:
[B]${font Terminus:style=bold:size=11}NETWORK QUALITY: [eth0] $alignr ${wireless_link_qual eth0}%
[/B]
I don't have a wireless, but cannot find anything else mentioned except ${wireless_link_qual
eth0 is what ifconfig and the network icon on the top panel show I have.

And the weather won't display although I changed the location to match mine in weather.template which I linked .cronkyrc to.

**sh: conkyForecast: not found** is what terminal keeps displaying from time to time.

When I set it up in Startup applications and rebooted it kept coming up with a black screen 
and I couldn't login, except to recovery. I was getting sort of freaked out. But, after 
about 3 boots, it finally came up normally. Whew!

I could not get that 1st temp. to show up no matter what, so I found where I could stick the core 
temps in there and did that. How would I get those to display in F instead of Celsius?

I tried to use that weather link **wojox**, but it wanted my website and I don't have one.
I didn't know what to do.

Thanks for both of your help! 

Here is what I have so far:

[IMG]http://ubuntuforums.org/picture.php?albumid=2066&pictureid=6881[/IMG]

---

### Post by Quackers on 2010-10-20
I don't have ethernet connected normally so I can't be sure, but have you tried ending the line with
${ethernet_link_qual eth0}%

If you're using the xoap site for weather you have to open an account and get a partner ID and a licence key  then put those in the .conkyforecast.config file (which is in your Home folder - but hidden).

As far as the website address is concerned I may have made one up :-)

---

### Post by Cavsfan on 2010-10-21
Well, I got the weather part added and I did make up a website. I even was able to figure out how to get the weather in Fahrenheit as I 
am from the US and we don't grasp Celsius too well. I figured out how to add the GPU temp, but I could not figure out how to get that 
or the CPU temps in Fahrenheit. I tried what you suggested with the ${ethernet_link_qual eth0}% But you can see what it displays. (${ethernet).

This is by no means easy! The whole thing is very complicated, but if I could figure out how to get the temps for CPU and GPU  
to display in Fahrenheit as well as the network quality to display I would be happy. :)

Also I added a startup item and when I booted up the conky was "on top" of anything displayed. I had to kill it and start it back up with terminal.
And I would like not to have to leave a terminal open to display the conky if possible. I tried adding a script to sleep 30 && conky, but that did 
not work when I rebooted.

So, far I've learned some things; the main one being this stuff is very complicated!

Also, is there any way to make the weather smaller? It currently takes up a lot of room.

Thanks in advance!

[IMG]http://ubuntuforums.org/picture.php?albumid=2066&pictureid=6882[/IMG]

---

### Post by Quackers on 2010-10-21
It's not easy. It's difficult at times.
I've googled around for the ethernet quality variable but have had no luck. Presumably this is because ethernet quality is always likely to be 100% whereas wireless can vary widely.
Are you running 64 bit? I had a problem where open folders slid under conky. See post #7 here for details.

[http://ubuntuforums.org/showthread.php?t=1558978](http://ubuntuforums.org/showthread.php?t=1558978)

With regard to the weather being smaller, do you mean smaller displayed items (reduce font size) or too spread out in lines (don't leave as many empty lines in .conkyrc).
I don't know about converting C to F in temps. Is google no help there?

---

### Post by Cavsfan on 2010-10-21
> **Quackers said:**
> It's not easy. It's difficult at times.
I've googled around for the ethernet quality variable but have had no luck. Presumably this is because ethernet quality is always likely to be 100% whereas wireless can vary widely.
Are you running 64 bit? I had a problem where open folders slid under conky. See post #7 here for details.

[http://ubuntuforums.org/showthread.php?t=1558978](http://ubuntuforums.org/showthread.php?t=1558978)

With regard to the weather being smaller, do you mean smaller displayed items (reduce font size) or too spread out in lines (don't leave as many empty lines in .conkyrc).
I don't know about converting C to F in temps. Is google no help there?

I've made a lot of progress, but man is this difficult!!! I gave up on the ethernet quality as you are probably right mine would probably say 100% 
all of the time. I got the startup to work with the parameter of pause 8 seconds and it works well. It doesn't stay on top of anything this way.

The only issue I have is converting the Cs to Fs! And so far nothing! Apparently there are not a lot of Americans that use conky or else 
they are satisfied with Celsius!  And one more thing I want to change the date and time at the bottom from Military time.

So, with 2 full days of jacking with this stuff, I just have to convert the C to F and the date at the bottom I think. You see how spread out the weather is at the bottom and i would like to add humidity and possibly some other info.
Oh, and one more thing, how do I keep my windows drive mounted? It will unmount after a period of time and I have to click on it and then it shows in conky.
Here is what it looks like:

[[IMG]http://ompldr.org/tNXcwZQ[/IMG]]("http://ompldr.org/vNXcwZQ")

Thanks immensely for your help!!! I have been on this all day and am ready for a break! :)

---

### Post by Quackers on 2010-10-21
The weather images just need lowering until they look right. That's the bit at
${image [--location=UKXX0092 --datatype=WI] -p 0,610 -s 90x90 -n}
change the -p 0,610 to something like -p 0,650 and see how it looks. (Do the same for all of them). 
the (90x90) part is the size of the weather image, which can be any size you want.
Also did you get your account details and licence key sorted out and installed?
I don't know whether CPU temps can be displayed in degrees F - but it seems likely. Maybe google some more?

---

### Post by mobilediesel on 2010-10-21
You could try the [Mega-Conky-Thread]("http://ubuntuforums.org/showthread.php?t=281865"). Or you could try [Conky PitStop]("http://conky-pitstop.wikidot.com/") which is also linked in my sig. Conky PitStop would probably be easier to go through for information since it's a wiki format rather than an insanely-long forum thread. The thread will be good for asking questions that you can't answer yourself from the wiki site.

---

### Post by Cavsfan on 2010-10-22
> **Quackers said:**
> The weather images just need lowering until they look right. That's the bit at
${image [--location=UKXX0092 --datatype=WI] -p 0,610 -s 90x90 -n}
change the -p 0,610 to something like -p 0,650 and see how it looks. (Do the same for all of them). 
the (90x90) part is the size of the weather image, which can be any size you want.
Also did you get your account details and licence key sorted out and installed?
I don't know whether CPU temps can be displayed in degrees F - but it seems likely. Maybe google some more?

Thanks! I'll play with the size of the weather as you mention. Yes, I did get my account all setup for the weather. 
This stuff is not for the meek! :-k My system boots up in about 8-10 seconds, but I discovered that a delay below 
15 seconds can cause the conky to stay on top of any windows.

---

### Post by Cavsfan on 2010-10-22
> **mobilediesel said:**
> You could try the [Mega-Conky-Thread]("http://ubuntuforums.org/showthread.php?t=281865"). Or you could try [Conky PitStop]("http://conky-pitstop.wikidot.com/") which is also linked in my sig. Conky PitStop would probably be easier to go through for information since it's a wiki format rather than an insanely-long forum thread. The thread will be good for asking questions that you can't answer yourself from the wiki site.

Thanks! I'll look into this. This stuff is killing me! Definitely not for novices. :) I appreciate the help!

---

### Post by Cavsfan on 2010-10-22
To change the CPU temps to fahrenheit, you just have to add this above the TEXT line: **temperature_unit fahrenheit**
Then I noticed the GPU temp was still in Celsius. and after some more googling I found this:
I have an nVidia card and **nvidia-settings -query GPUCoreTemp** gives you the temp. in Celsius. 
And apparently there is no fahrenheit output from that command. It has to be computed, but I found this which worked perfectly!
```
${color}GPU Temperature: $color${execi 10 nvidia-settings -q GPUCoreTemp | awk '{if (NR==2) {print ($4*9)/5+32}}'} °F
```

My brain is fried now! I am somewhat intimidated by the weather settings and I think it looks pretty darn good right now!
Maybe sometime when I feel like I am up for some abuse I will pursue the weather, but for now I am satisfied!
Thanks to the 3 of you for helping! :) I am grateful!

---

### Post by Cavsfan on 2010-10-22
Here is the final result:

[[IMG]http://ompldr.org/tNXc3aA[/IMG]]("http://ompldr.org/vNXc3aA")

---

### Post by Quackers on 2010-10-22
When you've had a rest you'll be back. Believe me the weather image alignment will drive you mad :-)
Nice work, hang in there.

---

### Post by Cavsfan on 2010-10-22
> **Quackers said:**
> When you've had a rest you'll be back. Believe me the weather image alignment will drive you mad :-)
Nice work, hang in there.

Thanks! It will definitely be a while! That took a lot out of me! But, you are most probably right and I would like to add humidity to the mix.
But, like I say, it will be a while! Thanks for your help and hopefully this will provide some others a way to get their stuff to show in F instead of C!

Getting the weather to display F was as simple as adding **--imperial** as a parameter. And the CPU was simple once I found it.
The nVidia GPU temp, not so easy and there are many different cards out there, but this will hopefully help nVidia card owners! :)

---

### Post by Quackers on 2010-10-22
Yes, some very useful tips for our cousins over the pond :-)
Sadly humidity I know nothing about.
FYI if you are editing weather.template then save the file, if you also open .conkyrc in gedit and just save that file (not making any changes) conky will restart with its amended weather details. (Just so you don't need to killall every time - but maybe you found that out already! :-) )

---

### Post by Cavsfan on 2010-10-22
Yes, I found out that saving the .conkyrc file would immediately restart conky with the changes,  I really liked that. Through one of the links you all 
provided on this thread I seen all of the possible weather parameters. Humidity is HM I think. But, I will give my brain a good amount of time to 
calm down before I even think of changing it any more! It is perfectly fine as it is! Thanks again! :)

---

### Post by Quackers on 2010-10-22
If you're happy, I'm happy! :-)

---

### Post by Cavsfan on 2010-10-26
Well there were 2 updates - conkyweather and conkyrythmbox and when I installed them, my weather went away. :confused:  I removed conkyweather
and still no weather. Then I reinstalled conky-all and still no weather. I don't know why this would have broken my weather on my conky.
It was looking pretty good before the update broke it.

---

### Post by Quackers on 2010-10-26
From Kaivalagi in the Weather Thread

Re: Conky Weather Forecast Python Script
UPDATE

Updates as follows:

    * Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)


Package changes can be seen here: [http://launchpadlibrarian.net/58195347/conkyforecast_2.13_source.changes](http://launchpadlibrarian.net/58195347/conkyforecast_2.13_source.changes)

The apt packages should be available soon

Cheers

Note For 10.10 Users
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:


```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

---

### Post by Cavsfan on 2010-10-26
> **Quackers said:**
> From Kaivalagi in the Weather Thread

Re: Conky Weather Forecast Python Script
UPDATE

Updates as follows:

    * Updated the /usr/bin/ script to use the python2 sym link instead of python as Python 3 is either here (Arch) or coming (Ubuntu)


Package changes can be seen here: [https://launchpad.net/~conkyhardcore...source.changes]("https://launchpad.net/%7Econkyhardcore...source.changes")

The apt packages should be available soon

Cheers

Note For 10.10 Users
I do beleive that Ubuntu 10.10 has a bug not having the python2 symbolic link, all other distro's I've used including previous versions of Ubuntu do have a python2 sym link...chances are it's been forgotten about in the hurry to rollout 10.10....

To fix things so the script can work as it is supposed to post the latest update just add a symbolic link in for python2 like this:


```
sudo ln -s /usr/bin/python2.6 /usr/bin/python2
```

Thanks!!! :)  My weather is back to working!!! I never would have figured this out without your help!
BTW, I unresolved this thread as conky is never resolved.  
Thanks for your help! It is much appreciated! :)

---

### Post by Quackers on 2010-10-26
You're welcome.
I only found it by chance. My Conky weather was still working and I just checked on the main thread when somebody posted and saw that. I ran it, then did the updates, so I never lost the display.  I would have been scratching my head if I hadn't seen that though :-)

---

### Post by Cavsfan on 2010-10-26
> **Quackers said:**
> You're welcome.
I only found it by chance. My Conky weather was still working and I just checked on the main thread when somebody posted and saw that. I ran it, then did the updates, so I never lost the display.  I would have been scratching my head if I hadn't seen that though :-)

I was scratching my head wondering why the weather went away! This stuff is too complicated for me!
But, I am glad you found that solution! :)

BTW that link doesn't go anywhere.

---

### Post by Quackers on 2010-10-26
Oh right, I'll tell him. (I hadn't tried that :-) )

---

### Post by Quackers on 2010-10-26
Apparently the original link works, but because I have copied it, the system truncates it, so we have been trying to connect to half a link. The original link is in post #2256 here

[http://ubuntuforums.org/showthread.php?t=869328&page=226](http://ubuntuforums.org/showthread.php?t=869328&page=226)

---

